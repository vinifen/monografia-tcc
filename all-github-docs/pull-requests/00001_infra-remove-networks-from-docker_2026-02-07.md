---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 1
github_pull_request_id: 3258721519
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/1
state: closed
draft: False
author: vinifen
created_at: 2026-02-07T22:48:24Z
updated_at: 2026-02-07T22:53:49Z
merged_at: 2026-02-07T22:53:49Z
closed_at: 2026-02-07T22:53:49Z
head_ref: develop
base_ref: main
title: "🏗️ infra: remove networks from docker"
---

# 🏗️ infra: remove networks from docker

# 🏗️ Remove networks from docker
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: N/A
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- Networks were removed because they were no longer useful.

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **INFRA**

### ⏳ Time spent:
- **1 HOURS** (approximate)

### 📝 Additional notes:
<!-- Any extra context, screenshots, or information for the reviewer -->
- This was done because I was having a problem with Coolify where deployment worked and no errors appeared, but after a short time a gateway timeout appeared.

## ✅ PR Checklist
- [x] No sensitive information (passwords, API keys, secrets) exposed
- [x] All tests run and pass successfully (unit, e2e, lint, etc.)
- [x] Code compiles and runs without errors
- [x] Tests and documentation updated or added if applicable
- [x] Removed unnecessary comments, debug statements and dev artifacts
- [x] Related issues, labels, and PR links established; PR title OK
