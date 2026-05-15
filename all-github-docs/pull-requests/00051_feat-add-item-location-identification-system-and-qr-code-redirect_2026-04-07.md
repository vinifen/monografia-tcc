---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 51
github_pull_request_id: 3498869405
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/51
state: closed
draft: False
author: vinifen
created_at: 2026-04-07T16:00:30Z
updated_at: 2026-04-13T01:19:09Z
merged_at: 2026-04-07T16:39:11Z
closed_at: 2026-04-07T16:39:11Z
head_ref: @vinifen/feat/50/item-localization-identification
base_ref: develop
title: "✨ feat: add item location/identification system and QR code redirect"
---

# ✨ feat: add item location/identification system and QR code redirect

# ✨ Add item location/identification system and QR code redirect
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #50 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
### Scope

This branch introduces item localization and identification improvements across the catalog domain, including:

- A new `locations` reference model linked to catalog items.
- Structured identification codes for items.
- Public redirect resolution by identification code.
- QR code generation and admin QR actions.
- Public and admin filtering/search updates for location-aware flows.
- Refactoring of contribution completion and received-mail responsibilities into dedicated services.
- UI, translation, migration, environment, and test updates to support the full feature set.

### Key Functional Changes

#### 1) Location support for catalog items

- Added `locations` table and linked `items.location_id` via migration.
- Added `App\Models\Location` with normalized uppercase codes and localized display labels.
- Added `LocationService` and `CatalogLocationDefaultResolver` to provide ordered location lists and default resolution (`UTFPR`, fallback to `INDEF`).
- Updated public catalog query builder and admin index/search configuration to support location-based filtering/search.
- Updated forms, filters, and views (public + admin) to expose and display location data.
- Added language entries for location labels in both English and Brazilian Portuguese.

#### 2) Item identification code system

- Added `App\Support\Catalog\ItemIdentificationCode` to build and parse codes.
- Identification code format now includes item id, location code, compact title segment, and year.
- Item creation flows now generate/update identification codes in service/action layers.
- Added tests for identification code formatting and parsing behavior.

#### 3) Public redirect by identification code

- Added `IdentificationCodeRedirectController`.
- Added route `GET /codes/{code}` to resolve a validated item by identification code and redirect to the item detail page.
- Added feature test coverage for redirect success/failure paths.

#### 4) QR code lifecycle and admin actions

- Added `ItemQrCodeService` for QR generation, retrieval, compatibility checks, and deletion.
- QR target URL points to the identification-code route.
- Admin item area now includes QR actions (regenerate/delete/copy link/copy image/print).
- Added frontend JS for QR action interactions.
- Extended item image type usage to include QR code handling.

#### 5) Contribution flow refactor

- Removed action classes that previously handled contribution-completion and mail dispatch.
- Introduced:
  - `CatalogContributionCompletionService`
  - `CatalogContributionReceivedMailService`
- `StoreItemContributionAction` now delegates completion behavior and QR generation responsibilities more explicitly.
- Improved resilience around post-contribution email failures while preserving session cleanup.

### Query/Search and Admin Infrastructure Updates

- `AdminIndexQueryBuilder` was expanded with:
  - LIKE subquery search support.
  - Numeric exact-filter guards.
  - Improved sort/search flexibility for translated/location-aware fields.
- `AdminIndexConfig` and `AdminIndexTableView` updated to expose the new index behaviors.
- Public `ItemIndexQueryBuilder` now handles strict location filtering and maintains existing search/sort semantics with translation-aware SQL.

### Data, Config, and Deployment Adjustments

- Updated migrations for languages/items/item_images and removed legacy migrations no longer needed in this setup.
- Updated seeders/factories to support location-aware item data.
- Updated staging/production env examples.
- Updated `phpunit.xml` defaults for test execution environment.
- README expanded with guidance for:
  - Language setup flow.
  - Catalog location reference-data behavior.
  - MySQL-focused testing considerations.

### Frontend and View Layer Changes

- Updated admin and public catalog Blade templates to show/use:
  - Location fields.
  - Identification code data.
  - QR code controls and warnings.
- Updated shared JS utilities (search form, enhanced select, release lock behaviors) and styles for new UI requirements.

### Test Coverage Added/Updated

New or updated tests cover:

- Identification code generation/parsing.
- Redirect resolution by identification code.
- Catalog location default resolution.
- Catalog index filtering by location.
- Translation fallback behavior adjustments.
- Contribution date and string helper behavior updates.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **FEAT**

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
