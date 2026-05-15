---
repository: vinifen/e-museu-2.1.0-beta
github_pull_request_number: 2
github_pull_request_id: 2801001588
html_url: https://github.com/vinifen/e-museu-2.1.0-beta/pull/2
state: closed
draft: False
author: vinifen
created_at: 2025-09-04T22:23:21Z
updated_at: 2026-01-04T20:25:36Z
merged_at: 2026-01-04T20:24:54Z
closed_at: 2026-01-04T20:24:54Z
head_ref: @vinifen/infra/1/setup-docker
base_ref: develop
title: "🏗️ infra: initial project setup"
---

# 🏗️ infra: initial project setup

# 🏗️ Initial Project Setup
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #1 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- Created local (development) and production environment using docker.
- Configured the ``run`` file with commands to load environments, dynamically determined by the ``APP_ENV`` variable in the ``.env.example`` file.
- Removed forced redirect to https
- Migrated frontend to Vite, with SCSS.
- Updated PHP from 8.1 to 8.3.25
- Removed bootstrap-typeahead 
- Fixed javascript errors
- The name was changed from '🏗️ Setup Docker' to '🏗️ Initial Project Setup' to reflect the broader scope of the changes. As a result, the name of the initial issue and branch also differ.

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **INFRA**

### ⏳ Time spent:
- **more than 25 HOURS** (approximate)

### 📝 Additional notes:
<!-- Any extra context, screenshots, or information for the reviewer -->
- There are console errors related to the migration to Vite and recent technology updates, which will be addressed in a separate pull request. Since the goal of this PR is to set up the application setup, this is acceptable, and overall the application is running.

## ✅ PR Checklist
- [x] No sensitive information (passwords, API keys, secrets) exposed
- [x] All tests run and pass successfully (unit, e2e, lint, etc.) [no tests yet]
- [x] Code compiles and runs without errors [Compile and run but there are some console errors]
- [x] Tests and documentation updated or added if applicable
- [x] Removed unnecessary comments, debug statements and dev artifacts
- [x] Related issues, labels, and PR links established; PR title OK
