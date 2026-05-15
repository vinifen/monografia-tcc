---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 17
github_pull_request_id: 3291734050
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/17
state: closed
draft: False
author: vinifen
created_at: 2026-02-16T22:03:29Z
updated_at: 2026-02-16T22:08:01Z
merged_at: 2026-02-16T22:08:01Z
closed_at: 2026-02-16T22:08:01Z
head_ref: develop
base_ref: main
title: "🔧 fix: images storage link"
---

# 🔧 fix: images storage link

# 🔧 Images storage link
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #13
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
# PR: Fix static file serving for `/storage` in Docker (staging, production, prod-local)

## Problem

In staging (Coolify) and in production-like Docker setups, image URLs under `/storage/items/...` returned **404**. The app and web services run in separate containers and share a named volume at `/var/www/storage`. The web container only receives a **copy** of `public/` at build time (no `public/storage` symlink), so when Nginx handles a request for `/storage/items/5/xxx.png` it looks under `root /var/www/public` and does not find the file, then falls back to `index.php` and Laravel returns 404.

Additionally, if **APP_URL** in the deployment environment pointed to the app (PHP-FPM) service URL instead of the public/web URL, image `src` attributes used a different host than the one serving the site, so requests hit the wrong service and also failed.

## Solution

1. **Nginx: serve `/storage/` from the volume**  
   A dedicated `location /storage/` was added so Nginx serves files directly from `/var/www/storage/app/public/` (the mounted volume), without relying on a symlink under `public/`.

2. **APP_URL**  
   In Coolify (and any environment where app and web have different URLs), **APP_URL** must be set to the **public** URL (the one that hits the web/Nginx service), so generated storage URLs use the same host that actually serves `/storage/`.

## Changes

### Docker Compose (volume setup)

Staging, production, and prod-local all use a **shared named volume** mounted at `/var/www/storage` on **both** the app and web services. This is required so that:

- The app writes uploads to `storage_path('app/public')` → `/var/www/storage/app/public/`
- The web container sees the same path and Nginx can serve it via `location /storage/` with `alias /var/www/storage/app/public/`

Relevant files and volume names:

- **`docker-compose.staging.yml`** – volume `staging_e_museu_storage` on `app-staging` and `web-staging`
- **`docker-compose.production.yml`** – volume `production_e_museu_storage` on `app-production` and `web-production`
- **`docker-compose.prod-local.yml`** – volume `e_museu_storage` on `app` and `web`

No changes were made to these compose files in this PR; they already used this pattern. The Nginx change relies on it.

### Nginx configs

- **`docker/nginx/staging/default.conf`**  
  Added:
  ```nginx
  location /storage/ {
    alias /var/www/storage/app/public/;
  }
  ```

- **`docker/nginx/production/default.conf`**  
  Same `location /storage/` block as above.

- **`docker/nginx/local_prod-local/default.conf`**  
  Same `location /storage/` block so local prod-local mirrors staging/production behaviour and can be used to test this flow.

### Views (conditional image rendering)

Views render the item/component image **only when `image_url` is present**, so we avoid broken image placeholders when an item has no image or the URL is empty.

Affected views:

- `resources/views/home.blade.php` – carousel item image
- `resources/views/items/index.blade.php` – item card image
- `resources/views/items/show.blade.php` – item image, component image, timeline item image
- `resources/views/admin/items/show.blade.php` – item image
- `resources/views/admin/items/edit.blade.php` – previous image thumbnail
- `resources/views/admin/proprietaries/show.blade.php` – item image
- `resources/views/admin/item-tags/show.blade.php` – item image
- `resources/views/admin/extras/show.blade.php` – item image
- `resources/views/admin/components/show.blade.php` – item and component images

Pattern used: `@if ($item->image_url)` (or equivalent for the related model) wrapping the `<img>` tag.

## Behaviour after the fix

- Requests to `https://<public-host>/storage/items/...` are handled by Nginx and served from `/var/www/storage/app/public/` in the web container.
- The app container continues to write uploads to the same volume at `storage_path('app/public')` (i.e. `/var/www/storage/app/public`), so both app and web see the same files.
- Staging (Coolify), production, and local prod-local all use the same serving strategy for `/storage/`.

## Deployment note

After merging, **rebuild the web image** and redeploy staging/production so the new Nginx config is applied. Ensure **APP_URL** in the deployment environment points to the public/web URL.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **TYPE**

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
