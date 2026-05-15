---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 19
github_pull_request_id: 3295651781
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/19
state: closed
draft: False
author: vinifen
created_at: 2026-02-17T19:10:01Z
updated_at: 2026-02-17T19:57:09Z
merged_at: 2026-02-17T19:18:46Z
closed_at: 2026-02-17T19:18:46Z
head_ref: @vinifen/infra/11/finish-s3-config
base_ref: develop
title: "🏗️ infra: finish s3 storage config"
---

# 🏗️ infra: finish s3 storage config

# 🏗️ Finish s3 storage config
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #11 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
This document includes information beyond this PR (e.g. troubleshooting and behaviour notes gathered during implementation and deployment).

## Goal

Enable **staging** and **production** (Coolify) to use **MinIO/S3** for image storage while keeping **local** on local disk. Images are served via the **application domain** (proxy), so MinIO and credentials are not exposed to the frontend.

---

## What was done

### 1. Filesystem configuration

- **`config/filesystems.php`**
  - Conditional `public` disk: when `FILESYSTEM_DISK=s3`, use S3 driver (MinIO) with `AWS_*`; otherwise keep local disk.
  - For S3, the `public` disk URL is `APP_URL.'/storage'` (not `AWS_URL`), so all image URLs point to the app domain.

### 2. Storage proxy in Laravel

- **`app/Http/Controllers/StorageProxyController.php`** (new)
  - Handles `GET /storage/{path}` (e.g. `/storage/items/11/xxx.png`).
  - Reads the file with `Storage::disk('public')` (local or S3) and streams the response.
  - Validates the path (empty, `..`) and returns 404 if invalid.
  - On `UnableToCheckExistence` or `UnableToReadFile` (e.g. MinIO unreachable), logs and returns 404 instead of 500.

- **`routes/web.php`**
  - Route added: `Route::get('/storage/{path}', StorageProxyController::class)->where('path', '.*')->name('storage.proxy');`

### 3. Nginx

- Removed the `location /storage/` block with `alias` from:
  - `docker/nginx/staging/default.conf`
  - `docker/nginx/production/default.conf`
  - `docker/nginx/local_prod-local/default.conf`
- Requests to `/storage/...` are now handled by Laravel (proxy).

### 4. Docker Compose

- **`docker-compose.staging.yml`** and **`docker-compose.production.yml`**
  - Comments on volumes clarifying they are only for **logs, sessions, and framework cache**; application data (images) lives in S3.

### 5. Environment documentation

- **`.env.example`**
  - Coolify **Production** and **Staging** sections with storage variables: `FILESYSTEM_DISK`, `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_DEFAULT_REGION`, `AWS_BUCKET`, `AWS_ENDPOINT`, `AWS_USE_PATH_STYLE_ENDPOINT`, `AWS_URL`.
  - Note for staging: when MinIO is internal-only, `AWS_ENDPOINT` should be the internal URL (e.g. `http://staging-minio-storage:9000`).

### 6. Code style

- **`app/Http/Controllers/StorageProxyController.php`**
  - PHPCS: added spaces around `|` in the `catch`: `UnableToCheckExistence | UnableToReadFile`.

---

## Problems encountered and how they were fixed

### 1. Images 404 on staging (Coolify)

- **Problem:** URLs like `/storage/items/...` returned 404.
- **Causes:** (a) The web container had no `public/storage` symlink (only a copy of `public/` at build time); (b) in some setups, `APP_URL` in Coolify pointed to the **app** service instead of the **web** service, so image URLs used a different host.
- **Solution:** First, a `location /storage/` alias was added in Nginx to serve from the volume; then the **Laravel proxy** was adopted and `APP_URL` in Coolify was set to the public (web) domain. With the proxy, Nginx no longer needs the alias; the app serves images.

### 2. MinIO unreachable (UnableToCheckFileExistence)

- **Problem:** When using S3, Laravel threw `UnableToCheckFileExistence` and returned 500.
- **Causes:** Wrong endpoint (e.g. public URL when MinIO is internal, or the reverse), or connectivity/credentials issues.
- **Solution:** Set `AWS_ENDPOINT` (and other `AWS_*`) correctly in Coolify; in some environments **HTTP** had to be used for the endpoint instead of HTTPS (MinIO certificate). The controller was updated to catch these exceptions and return 404 with a log entry instead of 500.

### 3. Access Denied when opening the bucket (direct MinIO URL)

- **Problem:** Opening the MinIO URL in the browser returned Access Denied (private bucket).
- **Solution:** With the **proxy**, images are requested from the app domain; the app uses credentials to talk to MinIO internally. The bucket can stay private; MinIO URL and credentials are not exposed to the frontend.

### 4. Seeder "Permission denied" (storage/logs and storage/app/public)

- **Problem:** When running the seed, errors creating directories under `storage/app/public/items/...` and writing to `storage/logs/laravel.log`.
- **Context:** In some flows (e.g. local with bind mount or after resetting containers), the "Fixing permissions" step in the `run` script uses `chown laravel:www-data`; the `laravel` user does not exist in the Alpine image, so the chown failed silently and permissions depended on the environment.
- **Solution:** In the environment where the error appeared, **resetting Docker** (recreating containers/volumes) fixed it. The `run` script was not permanently changed to `www-data:www-data` because in another context that broke the seeder; the current script behaviour was kept.

### 5. PHP CodeSniffer (PSR-12)

- **Problem:** `OperatorSpacing.NoSpaceBefore` / `NoSpaceAfter` on `catch (UnableToCheckExistence|UnableToReadFile)`.
- **Solution:** Add spaces around `|`: `catch (UnableToCheckExistence | UnableToReadFile $e)`.

---

## Final behaviour

| Environment | Storage (images) | Image URLs | Compose volume |
|-------------|------------------|------------|----------------|
| **Local** | Local disk | `APP_URL/storage/...` | N/A or bind mount |
| **Staging (Coolify)** | MinIO (S3) | `APP_URL/storage/...` (proxy) | Logs/sessions/cache only |
| **Production (Coolify)** | MinIO (S3) | `APP_URL/storage/...` (proxy) | Logs/sessions/cache only |

- The browser only sees `domain/storage/...`; MinIO and credentials stay on the backend.
- `php artisan storage:link` is no longer required; the proxy serves all public storage content.

---

## Files changed / added

- `config/filesystems.php` – conditional `public` disk and S3 URL
- `app/Http/Controllers/StorageProxyController.php` – **new**
- `routes/web.php` – proxy route
- `docker/nginx/staging/default.conf` – removed `location /storage/`
- `docker/nginx/production/default.conf` – removed `location /storage/`
- `docker/nginx/local_prod-local/default.conf` – removed `location /storage/`
- `docker-compose.staging.yml` – volume comments
- `docker-compose.production.yml` – volume comments
- `.env.example` – Coolify examples with storage variables (Production and Staging)

```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **INFRA**

### ⏳ Time spent:
- **4 HOURS** (approximate)

### 📝 Additional notes:
<!-- Any extra context, screenshots, or information for the reviewer -->
- N/A

## ✅ PR Checklist
- [x] No sensitive information (passwords, API keys, secrets) exposed
- [x] All tests run and pass successfully (unit, e2e, lint, etc.)
- [x] Code compiles and runs without errors
- [x] Tests and documentation updated or added if applicable
- [x] Removed unnecessary comments, debug statements and dev artifacts
- [x] Related issues, labels, and PR links established; PR title OK
