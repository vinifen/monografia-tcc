---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 35
github_pull_request_id: 3399924212
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/35
state: closed
draft: False
author: vinifen
created_at: 2026-03-14T22:07:36Z
updated_at: 2026-03-16T17:15:02Z
merged_at: 2026-03-16T13:38:39Z
closed_at: 2026-03-16T13:38:40Z
head_ref: @vinifen/refactor/34/controllers-part-2
base_ref: develop
title: "♻️ refactor: controllers part 2"
---

# ♻️ refactor: controllers part 2

# ♻️ Refactor controllers part 2
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #34 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- **Refactor admin & public catalog query:**

```md
# Refactoring: Query, Filters & Public Catalog

Summary of changes to pagination, filters, and catalog controller organization.

---

## 1. QueryController removed

- **Deleted:** `app/Http/Controllers/Catalog/QueryController.php` (non-semantic, scattered responsibilities).
- **Redistribution:** Tag endpoints → **TagController** (new), delegating to `TagService` (`index`, `autocomplete`, `checkName`). Component autocomplete/check → **ItemController** via `ItemService`. Contact check → **CollaboratorController** (new) via `CollaboratorService`.

## 2. Routes

- New/updated in `routes/web.php`: `GET /tags`, `/tags/autocomplete`, `/tags/check-name`; `/items/component-autocomplete`, `/items/check-component-name`; `/collaborators/check-contact`. Specific `items/*` routes placed **before** `items/{id}` to avoid conflicts.

## 3. Controllers → Services

- Controllers do not touch models directly; all data access goes through **Services** (and Actions where used). TagController, CollaboratorController, and ItemController inject and delegate to the corresponding services.

## 4. Support: Query builders

- **AdminIndexQueryBuilder** (`App\Support`): single `build(Builder, Request, array $config): void` — applies search + sort for admin index.
- **ItemIndexQueryBuilder** (`App\Support`): `build(Request): Builder` — builds public catalog query (validated items, filters, sort). Caller paginates.

## 5. Catalog index in Service

- Public item index logic moved from ItemController to **ItemService::getPaginatedItemsForCatalogIndex(Request)**. Uses `ItemIndexQueryBuilder::build()`, paginates (24), `withQueryString()`, `appends(['item_category','order'])`, resolves category name; returns `['items','categoryName']`. Naming aligned with admin: `getPaginatedItemsForCatalogIndex` / `getPaginatedItemsForAdminIndex`.

## 6. Filter & sort (catalog)

- Filter form: hidden input `order` with `request()->query('order', 1)` so sort is preserved when applying other filters. Paginator appends `order` and `item_category` so pagination links keep filters and sort.

## 7. Seeder / ItemTagFactory

- Public catalog requires `item_tag.validation = true`. **ItemTagFactory** now sets `'validation' => true` so seeded item–tag links show up when filtering by tag category.

## 8. Files touched

| Type       | Files |
|-----------|--------|
| Removed   | `QueryController.php` |
| Controllers | `ItemController`, `TagController`, `CollaboratorController` |
| Services  | `ItemService`, `TagService`, `CollaboratorService` |
| Support   | `AdminIndexQueryBuilder`, `ItemIndexQueryBuilder` |
| Other     | `routes/web.php`, catalog views/filter menu, modals, JS, `ItemTagFactory` |
```

- **Refactor Lock & others Admin controllers:**

```md
### Admin Authentication & Identity

- Updated `AdminLoginController` to:
  - Redirect to `/admin/items` after login.
  - Use `username` as the login identifier instead of `email` (via the `username()` override).
- Introduced/used `AdminService` in `AdminController` to:
  - Encapsulate admin index search/sort/pagination.
  - Remove raw `Admin::query()` handling from the controller.
- Started extracting **lock management** to a dedicated `LockService` (see below) and wiring it into identity controllers such as `ReleaseLockController` and related requests.

### Locking: from Trait to Service

- **Removed** the `LocksSubject` trait from admin controllers and deleted `app/Http/Controllers/Admin/Concerns/LocksSubject.php`.
- Introduced a dedicated `LockService` under `App\Services\Identity` and injected it where needed.
- Controllers that previously used `LocksSubject` now:
  - Call `LockService::requireUnlocked(...)` before edits/deletes.
  - Call `LockService::lock(...)` when entering edit forms.
  - Call `LockService::unlock(...)` on successful updates or deletes.

### Shared Admin Index Behavior

- Centralized admin index configuration into `App\Support\AdminIndexConfig` instances instead of static arrays embedded in controllers.
- Continued using `AdminIndexQueryBuilder` but now driven by `AdminIndexConfig` per resource:
  - Keeps responsibilities (search columns, custom joins, sort mapping, boolean flags) close to each domain while avoiding duplication.

### Catalog: Admin Extras

- `AdminExtraController` now delegates all data access to:
  - `ExtraService` for listing and CRUD.
  - `ItemCategoryService` and `CollaboratorService` for form dropdown data.
  - `LockService` for concurrency control on edit/update/destroy.
- Replaced manual queries and joins in `index()`:
  - Controller now calls `ExtraService::getPaginatedExtrasForAdminIndex(Request)` and passes the returned `['extras', 'count']` to the view.
- Switched from manual `findOrFail($id)` to **route model binding** (`Extra $extra`) on read/edit/update/destroy actions.

### Catalog: Admin Item Categories

- `AdminItemCategoryController` now:
  - Uses `ItemCategoryService` for index query, creation, update and deletion.
  - Uses `LockService` for edit/update/destroy.
  - Uses route model binding (`ItemCategory $itemCategory`) instead of manual lookups.
- Index logic (search/sort/pagination) moved out of the controller into `ItemCategoryService::getPaginatedItemCategoriesForAdminIndex(Request)`.

### Catalog: Admin Item Components

- Added a dedicated `ItemComponentService` for `ItemComponent` listing and CRUD.
- `AdminItemComponentController` now:
  - Delegates index logic to `ItemComponentService::getPaginatedItemComponentsForAdminIndex(Request)`.
  - Uses `ItemCategoryService` to populate form category lists.
  - Delegates create/update/delete to the service (including the validation toggle).
- Removed inline index configuration and custom joins from the controller in favor of the new service + `AdminIndexConfig`.

### Catalog: Admin Items

- `AdminItemController` was updated to:
  - Inject and use `LockService` for edit/update/destroy/image delete flows.
  - Replace trait-based locking (`LocksSubject`) with service calls.
  - Keep item create/update/delete and image management in `ItemService` / `ItemImagesService` (no direct persistence logic in the controller).
- Continued using `ItemService::getPaginatedItemsForAdminIndex(Request)` for the admin index.

### Catalog: Admin Item Tags

- `AdminItemTagController` now:
  - Uses `ItemTagService` for index query, creation, validation toggle, and deletion.
  - Uses `ItemCategoryService` and `TagCategoryService` to provide data for create forms.
  - Uses route model binding (`ItemTag $itemTag`) instead of manual `findOrFail`.
- Index logic moved into `ItemTagService::getPaginatedItemTagsForAdminIndex(Request)`, driven by `AdminIndexConfig`.

### Collaborators (Admin)

- `AdminCollaboratorController` now:
  - Uses `CollaboratorService` for index, create, update, and delete.
  - Uses `LockService` on edit/update/destroy operations.
  - Uses route model binding (`Collaborator $collaborator`) for show/edit/update/destroy.
- Search and sort previously implemented in the controller have been moved into `CollaboratorService::getPaginatedCollaboratorsForAdminIndex(Request)`.
- Creation and update now:
  - Normalize the `blocked` flag using `$request->boolean('blocked', false)`.
  - Delegate persistence to `CollaboratorService`.
- Hard‑coded Portuguese success messages were replaced with **translation keys** (`__('app.collaborator.*')`).

### Domain Services & Models

- Extended existing services (`ExtraService`, `ItemCategoryService`, `ItemService`, `ItemTagService`, `TagService`, `TagCategoryService`, `CollaboratorService`) and added new ones (`ItemComponentService`, identity services) to:
  - Own all query, pagination and persistence logic that was previously inside controllers.
  - Provide small, explicit methods such as `createX`, `updateX`, `deleteX`, and `getPaginatedXForAdminIndex`.
- Adjusted models (`Extra`, `ItemComponent`, `ItemTag`) where necessary to support the new service methods and index queries (joins, scopes, and relation accessors).

### Files Removed / Added

- **Removed**
  - `REFACTORING-QUERY-E-CATALOG.md` (older refactoring notes, now superseded by this and previous documents).
  - `app/Http/Controllers/Admin/Concerns/LocksSubject.php` (lock handling now fully serviced by `LockService`).
- **Added**
  - `app/Http/Requests/Admin/Identity/AdminReleaseLockRequest.php` (typed request for lock release operations).
  - `app/Services/Catalog/ItemComponentService.php`.
  - `app/Services/Identity/*` (lock and admin‑related identity services).
  - `app/Support/AdminIndexConfig.php` (typed configuration objects for `AdminIndexQueryBuilder`).
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **REFACTOR**

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
