---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 41
github_pull_request_id: 3429835651
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/41
state: closed
draft: False
author: vinifen
created_at: 2026-03-22T01:00:47Z
updated_at: 2026-03-26T15:31:19Z
merged_at: 2026-03-26T15:31:01Z
closed_at: 2026-03-26T15:31:01Z
head_ref: @vinifen/refactor/40/views-componentization
base_ref: develop
title: "♻️ refactor: view structure"
---

# ♻️ refactor: view structure

# ♻️ Views componentization
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #40 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->

- **view structure:**

```md
## Blade structure and componentization

- **Layouts** moved from `resources/views/layouts/` to **`resources/views/components/layouts/`** (`app.blade.php`, `admin.blade.php`) and referenced as `<x-layouts.app>` / `<x-layouts.admin>`.
- **Page templates** live under **`resources/views/pages/`**, mirroring URL areas:
  - Public: `pages.home`, `pages.about`, `pages.catalog.items.*` (including modals, `explore-menu`, `filter-menu`).
  - Admin: `pages.admin.*` — `auth/login`, dashboard `index`, `catalog/*`, `taxonomy/*`, `identity/admins/*`, `collaborators/*`.
- **Shared UI** extracted under **`resources/views/components/ui/`**: flash messages, image modal, boolean badge, page title.
- **Admin shell** via **`components/admin/index-shell.blade.php`** (container, flash, optional heading via `page-title`).
- **Removed** old flat paths: root `home.blade.php` / `about.blade.php`, `layouts/*`, `admin/*`, `catalog/*`, `image-modal/*`, etc. (replaced by the `pages/` + `components/` layout).

## Routes (`routes/web.php`)

- **Public catalog** under prefix `catalog` with names like `catalog.items.*`, `catalog.extras.store`, tag/collaborator helpers.
- **Admin** under `admin` + `authenticate`, grouped by concern:
  - `admin.catalog.*` — items, item-categories, extras, item-components, item-tags.
  - `admin.taxonomy.*` — tags, tag-categories.
  - `admin.identity.*` — admins, release-lock, delete-lock.
  - `admin.collaborators.*` — resource CRUD.
- **Admin entry**: redirect `/admin` → `/admin/catalog/items`.
- **Auth**: `admin/auth/login` (GET/POST) with `redirectIfAuthenticated`; **logout** `POST admin/auth/logout` named `logout`.

## Application code aligned with new routes and views

- **Controllers** (admin catalog, taxonomy, identity, collaborators, catalog `ItemController`, `HomeController`) now return **`pages.*`** view names instead of the old `admin.*` / `catalog.*` / `home` paths.
- **`AdminLoginController`**: login view `pages.admin.auth.login`; default redirect `/admin/catalog/items`.
- **`RedirectIfAuthenticated`**: redirects to named route `admin.catalog.items.index`.
- **`LockService`** + **`config/lockable_routes.php`**: lock subjects keyed by **new route name prefixes** (`admin.catalog.items`, `admin.taxonomy.tags`, etc.); `resolveSubject()` maps lock `type` strings to those prefixes.
- **`resources/js/components/itemCategoryItemSelector.js`**: route/URL usage updated for the new admin catalog paths.
- **`components/release-lock-on-leave.blade.php`**: adjusted for the new release-lock route naming.

## Translations (untracked)

- **`lang/en/common.php`** and **`lang/pt_BR/common.php`**: shared strings (e.g. yes/no).

## Bugfix in collaborator views (enum in Blade)

- Admin collaborator **create / edit / index / show** pages avoid `use` inside `@php` blocks nested in component slots (invalid PHP). **`CollaboratorRole`** is referenced with the **fully qualified class name** `\App\Enums\Collaborator\CollaboratorRole`.

## Scale of the diff

- Roughly **67 files** touched in the index: large deletion count from moving views; additions are primarily under `pages/`, `components/layouts/`, `components/ui/`, plus the small lang and admin shell files above.

---

*Generated to describe the working tree state; amend or delete this file after you commit if you prefer not to keep it in the repo.*
```

- **global view componentization:**

```md
## Summary

This PR refactors Blade views and the admin “index” experience so list pages share the same building blocks (toolbar, search, sortable table, page header). Support code for search/sort options moves into typed PHP helpers under `App\Support\Admin`, and large public templates (home, about, catalog items) are split into partials. Duplicate translation keys for identical UI (notably the search submit button) are replaced with a single shared string (`view.shared.buttons.search`).

## Changes

### Admin index pages

- **New components**: `x-admin.index-toolbar` (primary “create” action + `x-admin.search-form`), `x-admin.sortable-table`, and `x-admin.page-header` for title + optional actions.
- **Removed**: `components/admin/index-shell.blade.php` and the generic `pages/admin/index.blade.php` (superseded by the per-resource index views using the shared pieces).
- **Updated index views** for: catalog items, item categories, item tags, item components, extras; collaborators; identity admins; taxonomy tags and tag categories. Create/edit/show and admin login were adjusted where they needed the new UI components or copy keys.

### Search and i18n

- The search form’s submit label is no longer passed as a Blade prop per page; the toolbar always passes `__('view.shared.buttons.search')`.
- Removed redundant `search_button` entries from `lang/*/view/admin/*.php` (catalog, taxonomy, collaborator, identity) in favor of `view.shared.buttons.search` in `lang/*/view.php`.
- Admin-facing **app** strings (`lang/*/app/*.php`) were extended or reorganized where `AdminIndexTableView` reads search/sort option labels from the `app.*` namespace.

### PHP support layer

- **Moved**: `AdminIndexConfig` and `AdminIndexQueryBuilder` from `App\Support\` to `App\Support\Admin\` (all imports updated).
- **New**: `AdminIndexTableView` — static helpers that return `searchOptions`, `sortColumns`, and `searchBooleanColumns` (and related config) for each admin index, so controllers/services don’t duplicate long label arrays in multiple places.
- **Moved**: `ItemIndexQueryBuilder` to `App\Support\Catalog\ItemIndexQueryBuilder`.
- **Controllers & services** updated in parallel: catalog (items, categories, tags, components, extras), collaborators, identity admins, taxonomy (tags, tag categories), and `HomeController` for the new home view entrypoint.

### Layouts and global UI

- **`layouts/admin`** and **`layouts/app`**: aligned with the new page header pattern and public page structure.
- **New** under `components/ui/buttons/`: `default`, `edit`, `view`, `delete`, `submit`, `validate-invalidate`, `catalog-modal-add`.
- **New**: `components/ui/info-popover.blade.php`.
- **Removed**: `components/ui/page-title.blade.php` (title/actions handled via layout + `page-header`).

### Public-facing views

- **Home**: `pages/home.blade.php` replaced by `pages/home/index.blade.php` with partials under `pages/home/_partials/` (headline, exploration cards, about snippet).
- **About**: `pages/about.blade.php` replaced by `pages/about/index.blade.php` with partials (intro, gallery, elixo, tecnolixo).
- **Catalog items**: modals moved to `_partials/create/` and `_partials/show/`; filter UI under `_partials/index/`; explore UI split into `_partials/index/explore/` (desktop, menu, mobile panel/toggle, scroll script). Removed the old single-file `explore-menu` include.

### Routes

- `GET /` **redirects** to `/home`; named route **`home`** still points to the home action on `/home`.
- **About** closure now returns `view('pages.about.index')` instead of `pages.about`.

### Tooling and tests

- **`phpstan.neon`**: paths/namespaces updated for the moved support classes.
- **`tests/Feature/ExampleTest.php`**: adjusted if assertions targeted `/` directly (redirect behavior).

## Files added

- `app/Support/Admin/AdminIndexTableView.php`
- `resources/views/components/admin/index-toolbar.blade.php`
- `resources/views/components/admin/page-header.blade.php`
- `resources/views/components/admin/sortable-table.blade.php`
- `resources/views/components/ui/buttons/catalog-modal-add.blade.php`
- `resources/views/components/ui/buttons/default.blade.php`
- `resources/views/components/ui/buttons/delete.blade.php`
- `resources/views/components/ui/buttons/edit.blade.php`
- `resources/views/components/ui/buttons/submit.blade.php`
- `resources/views/components/ui/buttons/validate-invalidate.blade.php`
- `resources/views/components/ui/buttons/view.blade.php`
- `resources/views/components/ui/info-popover.blade.php`
- `resources/views/pages/about/_partials/elixo.blade.php`
- `resources/views/pages/about/_partials/gallery.blade.php`
- `resources/views/pages/about/_partials/intro.blade.php`
- `resources/views/pages/about/_partials/tecnolixo.blade.php`
- `resources/views/pages/about/index.blade.php`
- `resources/views/pages/catalog/items/_partials/index/explore/desktop.blade.php`
- `resources/views/pages/catalog/items/_partials/index/explore/menu.blade.php`
- `resources/views/pages/catalog/items/_partials/index/explore/mobile-panel.blade.php`
- `resources/views/pages/catalog/items/_partials/index/explore/mobile-toggle.blade.php`
- `resources/views/pages/catalog/items/_partials/index/explore/scroll-script.blade.php`
- `resources/views/pages/home/_partials/about.blade.php`
- `resources/views/pages/home/_partials/exploration-cards.blade.php`
- `resources/views/pages/home/_partials/headline.blade.php`
- `resources/views/pages/home/index.blade.php`

## Files removed

- `resources/views/components/admin/index-shell.blade.php`
- `resources/views/components/ui/page-title.blade.php`
- `resources/views/pages/about.blade.php`
- `resources/views/pages/admin/index.blade.php`
- `resources/views/pages/catalog/items/explore-menu.blade.php`
- `resources/views/pages/home.blade.php`

## Files renamed (git)

- `app/Support/AdminIndexConfig.php` → `app/Support/Admin/AdminIndexConfig.php`
- `app/Support/AdminIndexQueryBuilder.php` → `app/Support/Admin/AdminIndexQueryBuilder.php`
- `app/Support/ItemIndexQueryBuilder.php` → `app/Support/Catalog/ItemIndexQueryBuilder.php`
- `resources/views/pages/catalog/items/create-modals/component-modal.blade.php` → `resources/views/pages/catalog/items/_partials/create/component-modal.blade.php`
- `resources/views/pages/catalog/items/create-modals/extra-modal.blade.php` → `resources/views/pages/catalog/items/_partials/create/extra-modal.blade.php`
- `resources/views/pages/catalog/items/create-modals/tag-modal.blade.php` → `resources/views/pages/catalog/items/_partials/create/tag-modal.blade.php`
- `resources/views/pages/catalog/items/filter-menu.blade.php` → `resources/views/pages/catalog/items/_partials/index/filter-menu.blade.php`
- `resources/views/pages/catalog/items/show-modals/extra-modal.blade.php` → `resources/views/pages/catalog/items/_partials/show/extra-modal.blade.php`
```

- **Finish views refactor:**

```md
# Uncommitted Changes Summary

This document summarizes the work currently present in the working tree and not committed yet.

## Main Focus

The current uncommitted work is a broad Blade view refactor centered on componentization, UI reuse, and cleanup of repeated markup in both the admin area and the public catalog pages.

## Shared UI Infrastructure

- Added reusable admin action button components under `resources/views/components/ui/buttons/admin/` and removed the older generic admin button views from the previous location.
- Added reusable input components for both admin and public forms under `resources/views/components/ui/inputs/`.
- Added a reusable pagination component in `resources/views/components/ui/pagination.blade.php`.
- Added reusable catalog image upload components and shared upload helper assets under `resources/views/components/ui/images/catalog/`.
- Added `resources/views/components/admin/dependent-select-fetch.blade.php` to populate dependent selects through fetch-based client-side logic.
- Updated `resources/views/components/layouts/app.blade.php` to render stacked scripts required by the new interactive components.
- Expanded `lang/en/view.php` and `lang/pt_BR/view.php` with labels/messages for password visibility and image upload flows.

## Admin Area Refactor

- Applied the refactor across admin modules such as extras, item categories, item components, item tags, items, collaborators, admins, tags, and tag categories.
- Reworked many admin create/edit forms to use the new reusable admin input components instead of repeated raw Bootstrap markup.
- Replaced old action buttons in admin index/show pages with the new namespaced admin button components.
- Updated shared admin search rendering to improve accessibility and boolean field handling.
- Refactored admin item pages heavily:
  - extracted item show sections into partials;
  - extracted create/edit image upload and preview sections into partials;
  - improved image handling presentation for cover and gallery images.
- Added reusable dependent select behavior to admin flows that need category-to-item loading, especially extras, item tags, and item components.
- Updated admin login to use reusable input/password components, including password show/hide behavior.
- Simplified repeated index configuration logic in `app/Support/Admin/AdminIndexTableView.php` through a reusable helper for common name-based indexes.
- Kept backend controller changes minimal and mostly limited to small redirect formatting/consistency adjustments.

## Public Catalog Refactor

- Refactored `catalog/items/create` to use reusable public input components and extracted partials for:
  - image upload;
  - tag/extra/component sections;
  - reusable modal add button.
- Refactored public item modals to use reusable inputs and cleaner translated labels/messages.
- Changed the component selection modal to load components by category with fetch-based select options instead of the previous autocomplete/check flow.
- Refactored `catalog/items/index` to render each card through a dedicated partial and use the shared pagination component.
- Refactored `catalog/items/show` into smaller partials, including a details sidebar and timeline section.

## Overall Result

- Less duplicated Blade markup.
- More reusable and maintainable UI building blocks.
- More consistent form, button, pagination, and image-upload behavior across admin and catalog pages.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **REFACTOR**

### ⏳ Time spent:
- **9 HOURS** (approximate)

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
