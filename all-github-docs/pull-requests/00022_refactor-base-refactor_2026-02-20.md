---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 22
github_pull_request_id: 3298767544
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/22
state: closed
draft: False
author: vinifen
created_at: 2026-02-18T13:31:53Z
updated_at: 2026-02-21T10:45:43Z
merged_at: 2026-02-20T15:50:09Z
closed_at: 2026-02-20T15:50:09Z
head_ref: @vinifen/refactor/21/base-refactor
base_ref: develop
title: "♻️ refactor: base refactor"
---

# ♻️ refactor: base refactor

# ♻️ Base refactor
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #21
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
# Base refactor

Summary of everything done and modified in this branch: Laravel 11/12 alignment, code style (Pint), lock/conventions cleanup, and follow-up fixes after code review.

---

## 1. Laravel 11/12 migration

### Removed files

- **`app/Http/Kernel.php`** – HTTP middleware and aliases moved to `bootstrap/app.php`.
- **`app/Console/Kernel.php`** – Console bootstrap handled by `bootstrap/app.php` and `withCommands()`.
- **`app/Exceptions/Handler.php`** – Exception config (e.g. `dontFlash`) moved to `bootstrap/app.php` via `withExceptions()`.
- **`app/Providers/RouteServiceProvider.php`** – Route loading and rate limiting moved to `bootstrap/app.php` (`withRouting()`).
- **`app/Providers/AuthServiceProvider.php`** – Removed; empty and not required by Laravel 11+ default.
- **`app/Rules/Catalog/DifferentIds.php`** – Replaced by inline validation closures in the relevant Form Requests.

### Bootstrap and configuration

- **`bootstrap/app.php`**
  - Routes loaded via `withRouting(web: ..., api: ..., commands: ..., health: '/up')`.
  - Commands loaded via `withCommands(__DIR__.'/../app/Console/Commands')`.
  - Global and web/API middleware and aliases registered in `withMiddleware()`.
  - Exception handling (e.g. `dontFlash`, `AuthorizationException` render) in `withExceptions()`.
  - API rate limiter registered in `withRouting(..., then: function () { RateLimiter::for('api', ...); })` so the application exists when the facade is used.
- **`config/app.php`**
  - `AuthServiceProvider` removed from the providers list.

### Controllers and base class

- **`app/Http/Controllers/Controller.php`**
  - Reduced to a thin base (no custom logic); lock behaviour lives in the `LocksSubject` trait.
- **Admin controllers**
  - No longer extend a custom `AdminBaseController`; they extend `Controller` and use traits:
    - `BuildsAdminIndexQuery` for index search/sort.
    - `LocksSubject` where needed (edit/update/destroy for lockable resources).
  - Affected: `AdminItemController`, `AdminSectionController`, `AdminExtraController`, `AdminTagController`, `AdminCategoryController`, `AdminProprietaryController`, `AdminComponentController`, `AdminItemTagController`, `AdminUserController`.
- **Lock behaviour**
  - Lock is enforced in controllers via the **`LocksSubject`** trait (`requireUnlocked()`, `lock()`, `unlock()`), not via a global middleware. `config/lockable_routes.php` is used by `ReleaseLockController` and documented accordingly.

---

## 2. Code style and tooling

### Laravel Pint

- **`pint.json`** added with rules (e.g. `no_unused_imports`, `trailing_comma_in_multiline`) and exclusions.
- **`.github/workflows/ci.yml`** and **`scripts/ci/ci-code-quality.sh`** – `pint-test` step added to the CI pipeline.
- **`run`** script – New commands: `pint`, `pint-test`; `all-tests` and help text updated to include Pint.

### Style and PHPDoc (Pint / manual)

- Import order and spacing normalized (e.g. `Illuminate\*` before `App\*`, single space after `!` in conditions).
- Trailing commas added in arrays (Requests, Factories, Seeders, `lang`, config).
- PHPDoc updated (e.g. `@param` format with double space, removal of redundant `@return` where obvious).
- **`config/database.php`** – Spacing in MySQL options closure; **`config/debugbar.php`** – Array formatting.
- **`lang/pt_BR/validation.php`** – Reformatted (spacing/alignment only).
- **`database/migrations`** – Double semicolons fixed (`;;` → `;`) in items and item_component migrations.
- **`database/seeders`** – Unused `WithoutModelEvents` import removed (optional; behaviour unchanged unless models fire observers).
- **`run`** – `storage_link` command and help reference removed (storage is documented in `storage/doc.md`; proxy is used instead of `storage:link`).

---

## 3. Validation and Form Requests

### DifferentIds rule removed

- **`app/Rules/Catalog/DifferentIds.php`** deleted.
- **`app/Http/Requests/Catalog/SingleComponentRequest.php`** – Inline closure ensures `item_id` and `component_id` are different (same message as before).
- **`app/Http/Requests/Catalog/ItemTagRequest.php`** – Closure added so `item_id` and `tag_id` must differ (restores behaviour previously guaranteed by `DifferentIds`).

### Unique rules and ignore

- **`app/Http/Requests/Taxonomy/CategoryRequest.php`** – `Rule::unique('categories')->ignore($this->route('category'))` so updates can keep the same name.
- **`app/Http/Requests/Catalog/SectionRequest.php`** – `Rule::unique('sections')->ignore($this->route('section'))` for the same reason.
- **`app/Http/Controllers/Auth/RegisterController.php`** – Email uniqueness changed from `unique:users` to `unique:proprietaries,contact` (registration creates a `Proprietary`).

### Other request changes

- **`app/Http/Requests/Catalog/UpdateItemRequest.php`** – Message key fixed from `'data.required'` to `'date.required'`.
- Unused imports removed (e.g. `StoreItemRequest`: `File` rule; various controllers). Trailing commas and rule arrays normalized across Form Requests.

---

## 4. Controllers – behaviour and security

### Index sort direction

- **`app/Http/Controllers/Concerns/BuildsAdminIndexQuery.php`** – `applyIndexSort()` now uses the request `order` parameter directly (no longer inverts asc/desc).
- **`app/Http/Controllers/Catalog/AdminSectionController.php`**, **`AdminUserController`**, **`AdminProprietaryController`**, **`AdminCategoryController`** – Index sort updated to use `$request->order` (or equivalent) directly.

### Mass assignment and validation

- **`app/Http/Controllers/Catalog/AdminComponentController.php`** – `update()` only updates `['validation' => ! $component->validation]` (no `$request->all()`).
- **`app/Http/Controllers/Catalog/AdminItemTagController.php`** – Same pattern: `update()` only updates `['validation' => ! $itemTag->validation]`.
- **`app/Http/Controllers/Proprietary/AdminProprietaryController.php`** – On validation failure in `store()` and `update()`, response uses `withErrors($validator)` instead of `withErrors($messages)` so the user sees the real validation errors.

### Show and 404 behaviour

- All admin `show()` methods and the public item `show` use **`findOrFail($id)`** instead of `find($id)` so invalid IDs return 404 consistently.
  - Controllers: `AdminUserController`, `AdminComponentController`, `AdminItemTagController`, `AdminExtraController`, `AdminSectionController`, `AdminTagController`, `AdminCategoryController`, `AdminProprietaryController`, `ItemController`.

### Lock and users

- **`app/Http/Controllers/Identity/AdminUserController.php`** – `destroyLock()` now deletes **all** locks for the given user: `Lock::where('user_id', $id)->delete()` (previously only the first lock was removed).

---

## 5. Factories and seeders

- **`database/factories/Catalog/SectionFactory.php`** – `name` fixed from the literal string `'$this->faker->unique()->word'` to the actual call: `$this->faker->unique()->word`.
- Other factories (e.g. ItemComponent, Section, Proprietary, TagItem) – Trailing commas and minor style only; no logic change.

---

## 6. Services, models, and middleware

- **`app/Services/Catalog/ItemContributionService.php`** and **`app/Services/Catalog/ItemIndexQueryBuilder.php`** – PHPDoc and style (`!` spacing, import order); behaviour unchanged.
- **`app/Models/Catalog/Item.php`**, **`app/Models/Identity/Lock.php`** – Minor formatting/PHPDoc.
- **Middleware** – Import order and spacing only (ValidateItem, ValidateProprietary, CheckLock where present). Lock is enforced via `LocksSubject` in controllers; no `check.lock` middleware alias in `bootstrap/app.php`.

---

## 7. Routes and ItemController API

### Items resource and RESTful naming

- **`routes/web.php`**
  - Item routes kept explicit (no single resource that would hide `items/create` or the JSON endpoint):
    - `GET items` → `items.index`
    - `GET items/create` → `items.create`
    - `GET items/by-section` → `items.bySection` (JSON list of items by section for forms)
    - `GET items/{id}` → `items.show` (with `validate.item` middleware)
  - `POST items` and `POST items/extras` remain under `validate.proprietary`.

### Items “by section” endpoint

- **`app/Http/Controllers/Catalog/ItemController.php`**
  - New method **`bySection(Request $request): JsonResponse`** (replacing the previous `get` / `getItems` in QueryController): returns items filtered by `section` query parameter, ordered by name.
- **Route:** `GET items/by-section` → `ItemController@bySection`, name `items.bySection`.
- **Views and JS** – All references updated from `/get-items` / `route('items.get')` to `route('items.bySection')` and `/items/by-section` (admin extras/components/item-tags create/edit and related JS components).

### QueryController

- **`getTags`** remains in **`app/Http/Controllers/Catalog/QueryController.php`** (used by the public item form).
- **`getItems`** / **`bySection`** lives in **ItemController** under the items resource as above.

---

## 8. Configuration and docs

- **`config/lockable_routes.php`** – Comment updated to describe usage by the **LocksSubject** trait and **ReleaseLockController** (no CheckLock middleware).
- **`storage/doc.md`** – Added; documents storage and public file serving (proxy, no `storage:link`, env-specific disk).
- **`.env.example`** – Comment tweaks (e.g. “staging auth protection”); no functional changes.
- **`docker-compose.production.test.yml`** – One-line change (likely comment or minor config).

---

## 9. Files changed (summary)

About **65 files** were touched in the branch and follow-up work, including:

- **Removed:** Kernel (HTTP + Console), Handler, RouteServiceProvider, AuthServiceProvider, DifferentIds rule.
- **Added:** pint.json, storage/doc.md, and (in follow-ups) no new top-level config files.
- **Modified:** bootstrap/app.php, config (app, database, debugbar), Controllers (base + admin + Item + Query), Form Requests, Middleware, Models, Services, Factories, Seeders, Migrations, lang, routes (web, api), run script, CI workflow and scripts.

---

## 10. How to verify

- Run the test suite and CI (including `pint-test`, phpcs, phpmd, phpstan, etc.).
- Manually test: item list/create/show, item contribution form (tags, items by section), admin CRUD and lock (edit/release lock) for items, sections, tags, categories, proprietaries, extras.
- Confirm `GET items/by-section?section=...` returns JSON and is used correctly by the admin and/or public forms.
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
