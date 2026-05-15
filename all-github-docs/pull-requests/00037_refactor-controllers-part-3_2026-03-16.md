---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 37
github_pull_request_id: 3405527277
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/37
state: closed
draft: False
author: vinifen
created_at: 2026-03-16T17:07:43Z
updated_at: 2026-03-16T17:15:03Z
merged_at: 2026-03-16T17:14:22Z
closed_at: 2026-03-16T17:14:22Z
head_ref: @vinifen/refactor/36/controllers-part-3
base_ref: develop
title: "♻️ refactor: controllers part 3"
---

# ♻️ refactor: controllers part 3

# Controllers Part 3
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #36 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
- **StoreItemContributionAction**
  - Action now returns a small domain result array (`status` + optional `item`) instead of `RedirectResponse`.
  - Collaborator resolution returns a status + optional `Collaborator`, with guards to ensure non-null collaborators.
  - Item creation transaction only updates `identification_code`, and image normalization is delegated to `ItemImagesService`.
  - Added logging when component items are not found and improved PHPDoc/type hints.

- **Controllers**
  - `ItemController::store()` and `ExtraController::store()` now interpret service/action status and handle all redirects and error flashes in the controller layer.
  - `AdminItemController::destroyImage()` now correctly calls `$lockService->requireUnlocked($item)`.
  - `HomeController::index()` now uses `ItemService::getRandomValidatedItemsForHome()` instead of querying `Item` directly.

- **Services**
  - `ExtraService::storeSingleExtra()` returns a status array instead of performing redirects.
  - `ItemService::getRandomValidatedItemsForHome()` added; count-by-category methods now use exact ID comparison where appropriate.
  - `ItemImagesService` now:
    - Uses `UploadedFile` checks for cover/gallery images.
    - Normalizes the item’s cover image inside `storeCoverImage()` / `storeGalleryImages()`.
    - Logs and throws on upload read failures and mismatched image ownership.

- **Tooling**
  - `run` script gained `all-fix`, which runs `phpcbf`, `pint`, `eslint-fix`, and `prettier` in sequence.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **REFACTOR**

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
