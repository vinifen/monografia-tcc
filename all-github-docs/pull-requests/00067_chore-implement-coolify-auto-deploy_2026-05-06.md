---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 67
github_pull_request_id: 3638378564
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/67
state: closed
draft: False
author: vinifen
created_at: 2026-05-06T17:38:17Z
updated_at: 2026-05-06T17:43:05Z
merged_at: 2026-05-06T17:43:05Z
closed_at: 2026-05-06T17:43:05Z
head_ref: @vinifen/chore/66/auto-deploy-coolify
base_ref: develop
title: "⚙️ chore: implement coolify auto-deploy"
---

# ⚙️ chore: implement coolify auto-deploy

# ⚙️Implement coolify auto-deploy
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #66 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
## Application config

- **`config/app.php`:** `asset_url` now falls back to `APP_URL` when `ASSET_URL` is not set, so asset URLs can track the app URL without a separate env var.

## GitHub poll → Coolify deploy

- **`scripts/coolify-auto-deploy.sh`:** Shell script for Coolify **Scheduled Tasks** inside the PHP app container. It runs `git ls-remote` on `COOLIFY_AUTO_DEPLOY_GITHUB_REPO_URL` / branch, compares the tip SHA to a file under `storage/coolify/`, and on change calls `COOLIFY_AUTO_DEPLOY_DEPLOY_URL` with `Authorization: Bearer` + `COOLIFY_AUTO_DEPLOY_TOKEN`. The SHA is written **after** a successful HTTP response. State files: `last_sha_github_repo_staging` and `last_sha_github_repo_production` (per `APP_ENV`).

- **`Dockerfile.staging` / `Dockerfile.production`:** Copy `scripts/` into the image, mark `coolify-auto-deploy.sh` executable in the vendor stage and again in the final `app` stage after filesystem permissions.

## Repository hygiene

- **`.gitignore`:** Ignore the two Coolify SHA state files under `storage/coolify/`.
- **`storage/coolify/.gitkeep`:** Keep the directory in version control.

## Environment templates

- **`docs/deploy-coolify/coolify-staging.env.example`** and **`coolify-production.env.example`:** Document optional `COOLIFY_AUTO_DEPLOY_*` variables.
- **`.env.example`:** Comments pointing at the Coolify templates and auto-deploy doc.

## Documentation layout (`docs/deploy-coolify/`)

- **`auto-deploy/doc.md`:** How to create the API token, set env vars, schedule the task (e.g. staging every 5 minutes, production every 10), and run `/var/www/scripts/coolify-auto-deploy.sh`.
- **`minio-s3/doc.md`:** Post-install: create the S3 bucket and upload objects; references compose port mappings.
- **`mysql/doc.md`:** Post-install: import a SQL dump into the Coolify MySQL service.
- **MinIO compose files** live under `minio-s3/` (staging/production stacks).

## Product / design docs

- **`docs/prd.md`:** Ops note + NFR for optional Coolify polling deploy; changelog entry.
- **`docs/sdd.md`:** Operations bullet for the script and state files; changelog entry.
- **`docs/storage/doc.md`:** Deploy examples pointer updated to `docs/deploy-coolify/`.

```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **CHORE**

### ⏳ Time spent:
- **2 HOURS** (approximate)

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
