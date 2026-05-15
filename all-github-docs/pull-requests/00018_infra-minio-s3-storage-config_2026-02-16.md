---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 18
github_pull_request_id: 3291956881
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/18
state: closed
draft: False
author: vinifen
created_at: 2026-02-16T23:47:25Z
updated_at: 2026-02-17T19:57:08Z
merged_at: 2026-02-16T23:51:59Z
closed_at: 2026-02-16T23:51:59Z
head_ref: @vinifen/infra/11/s3-storage
base_ref: develop
title: "🏗️ infra: minio s3 storage config"
---

# 🏗️ infra: minio s3 storage config

# 🏗️ Add MinIO/S3 storage for staging and production

### Related Issue: #11

## 🔄 Change Overview

### ✨ Summary of changes:
- Make `public` disk in `config/filesystems.php` conditional: when `FILESYSTEM_DISK=s3`, use S3/MinIO (AWS_* env vars); otherwise keep local storage so dev stays unchanged.
- Extend `.env.example` Coolify section with Production and Staging examples including storage vars (`FILESYSTEM_DISK`, `AWS_*`) for MinIO so deploy only needs env config in Coolify.
- Local remains on local disk; staging and production on Coolify use MinIO when the listed env vars are set.

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **Infra**

### ⏳ Time spent:
- **1 HOUR** (approximate)

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

