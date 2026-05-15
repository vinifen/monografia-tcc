---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 47
github_pull_request_id: 3489448193
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/47
state: closed
draft: False
author: vinifen
created_at: 2026-04-04T20:27:29Z
updated_at: 2026-04-05T23:26:46Z
merged_at: 2026-04-04T20:32:44Z
closed_at: 2026-04-04T20:32:44Z
head_ref: @vinifen/fix-enhan/46/fixes-improves
base_ref: develop
title: "📈 enhancement: fix & enhancement"
---

# 📈 enhancement: fix & enhancement

# 📈  Fix & Enhancement
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #46 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview
### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
## Checklist (done in this branch)

| Goal | Notes |
|------|--------|
| Fix odd **scrolling** and **size proportions** (public + admin) | `resources/sass/custom.scss`: `overflow-x: clip` on `body.app-public-layout` / `body.admin-layout`, `min-width: 0` on flex children, explore strip uses flex + horizontal scroll inside the bar (not the whole page), admin toolbar row scrolls horizontally instead of blowing page width. |
| Add **favicon** (.ico) for E-Museu | `public/favicon.ico` replaced/added; layouts reference favicon as before. |
| **Selects**: do not show huge lists; **search** inside the control | `resources/js/shared/ui/enhanced-select.js` (debounced search, page size 50, scroll load). `resources/views/components/ui/inputs/select.blade.php` and admin select: `enhanced` default + i18n placeholders. Related SCSS for `.enhanced-select-*` (single caret, dropdown layout). |
| **Staging** image vs dev tooling | `Dockerfile.staging` documents **`composer install --no-dev`**: staging matches production (no Ignition/Debugbar/phpunit in vendor). Use a **local/debug** image when you need full dev dependencies. |
| **Organize** FormRequests around **translations** (admin create/update) | `AppliesAdminTranslationsPayload` + `AdminTranslationsPayloadContract`: one place for empty-string → null and cross-locale consistency; admin catalog/collaborator-related requests refactored to use it. `AdminItemTranslationsPayloadTest` locks behavior. |
| **Tests** no longer **wipe the local DB** | `phpunit.xml` sets `DB_DATABASE=emuseu_testing`. `docker/mysql/init/01-create-testing-database.sh` + compose mounts on **`docker-compose.local.yml`** and **`docker-compose.prod-local.yml`**. `./run test` runs **`ensure-mysql-testing-database`** before PHPUnit inside Docker so `emuseu_testing` exists and is granted. `README.md` documents the flow. |
| **Rate limiting** | `bootstrap/app.php`: named limiters; `routes/web.php`: throttles on public catalog, light JSON routes, admin, storage proxy, login. |
| **Imports** in grouped “domain” form (fewer lines) | Widespread `use Vendor\{A, B, C};` style (e.g. controllers, `StoreItemContributionAction`, `StorageProxyController`). |
| **Reset** control for **admin table search** and **catalog filters** | `resources/views/components/admin/search-form.blade.php`: reset link drops `search_column`, `search`, `page` while keeping other query params. `filter-menu.blade.php`: reset clears tag-panel filters + order, keeps `item_category` + text `search`. `lang/*/view.php`: `view.shared.buttons.reset`. |
| Fix **public catalog filtering** (items index) | `ItemController@index`: redirect bare URL to a **default query string** so filters behave consistently. Explore **desktop + mobile**: preserve `category[]`, `tag[]`, `order`, and **search value** when switching item category or submitting search; proper `type="submit"` on search buttons; unique mobile search id. Filter panel: accordions **open when filters active**; checkbox state aligned with request. |
| **localStorage** for contribution flow: save / clear on submit | `resources/js/shared/storage/local-storage.js`, `contribution-form-draft.js` (debounce + TTL + version), `item-create-storage.js` (wizard), `clear-item-create-form.js` (full clear + UI sync), image upload reset hook. |

---

## Technical index (by area)

### Routing and HTTP hardening

- Throttle middleware wired in `routes/web.php`; catalog JSON routes ordered **before** `items/{id}`.
- Convenience **redirects** for empty admin section roots (`catalog`, `taxonomy`, `identity`).
- `StorageProxyController`: on **local** disk, `realpath` check so resolved file stays under disk root.

### Public contribution (backend)

- `StoreItemContributionAction`: single **DB transaction**; on failure after item exists, **delete public storage folder** for that item id.
- Shared `CatalogImageRules`; stricter `ItemContributionValidator` and related requests.

### Admin validation helpers

- `CatalogRelationIdRules` (tag/component cannot reference same item as parent).
- `AdminCollaboratorRules` where collaborator rules are centralized.

### Frontend modules

- `enhanced-select.js`, `local-storage.js`, `contribution-form-draft.js`, `clear-item-create-form.js`, updates to `item-create-storage.js`, modals, `form-session-restore.js`, `catalog-item-image-upload-form.js`.
- `resources/js/app.js` / `admin.js` register scripts as needed.

### Tests and i18n

- New: `ItemContributionStoreDateTest`, `AdminItemTranslationsPayloadTest`.
- Adjusted: `OptionalContentLocaleJsonTest`, `TagFindOrCreateTest`, `TranslationResolutionTest`.
- Catalog/layout strings for filters, reset, select search, etc.
``` 

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **FIX & ENHANCE**

### ⏳ Time spent:
- **6 HOURS** (approximate)

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
