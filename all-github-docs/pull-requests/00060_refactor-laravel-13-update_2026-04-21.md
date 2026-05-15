---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 60
github_pull_request_id: 3552885456
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/60
state: closed
draft: False
author: vinifen
created_at: 2026-04-19T21:34:31Z
updated_at: 2026-04-24T22:07:19Z
merged_at: 2026-04-21T17:14:50Z
closed_at: 2026-04-21T17:14:50Z
head_ref: @vinifen/refactor/59/last-refactor
base_ref: develop
title: "♻️ refactor: laravel 13 update"
---

# ♻️ refactor: laravel 13 update

# ♻️ Last refactor before 1.0.0 version
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #59 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- **♻️ refactor: laravel 13 update:**
```md
# Laravel 13 Upgrade and Follow-Up Static Analysis

This document summarizes the framework upgrade to **Laravel 13** and the **PHPStan** adjustments that were required afterward. It is intended as a short handover note for maintainers.

## 1. Dependency and tooling updates (`composer.json` / `composer.lock`)

The application targets **PHP ^8.5** (compatible with Laravel 13’s minimum PHP requirement).

### Runtime (`require`)

| Package | Change (summary) |
|--------|-------------------|
| `laravel/framework` | Bumped to **^13.0** |
| `laravel/sanctum` | Bumped to **^4.3** so `illuminate/*` **^13** is allowed (Sanctum 4.3.x) |
| `laravel/tinker` | Bumped to **^3.0** (recommended for Laravel 13) |
| `laravel/ui` | Kept at **^4.6.1** (Packagist releases support Illuminate 13) |

### Development (`require-dev`)

| Package | Change (summary) |
|--------|-------------------|
| `nunomaduro/collision` | Bumped to **^8.9.3** (older Collision releases **conflict** with `laravel/framework` 13) |
| `laravel/sail` | Bumped to **^1.57** (Illuminate 13–compatible) |
| `larastan/larastan` | Bumped to **^3.9** (Laravel 13 support) |
| `spatie/laravel-ignition` | Bumped to **^2.12** |
| `nunomaduro/phpinsights` | Bumped to **^2.14** |

`phpunit/phpunit` was already on **^12.0**, which matches the official upgrade notes.

After changing `composer.json`, run **`composer install`** or **`composer update`** so `vendor/` matches `composer.lock`. If `vendor/` was owned by another user (for example root from Docker), fix ownership before running Composer on the host.

## 2. Framework-facing application changes

These align with the [official Laravel 13 upgrade guide](https://laravel.com/docs/13.x/upgrade).

### CSRF / request forgery middleware

Laravel 13 renames the CSRF middleware conceptually to **`PreventRequestForgery`** (deprecated aliases may still exist).

- **`bootstrap/app.php`**: the web middleware stack now references `Illuminate\Foundation\Http\Middleware\PreventRequestForgery` instead of `VerifyCsrfToken`.
- **`config/sanctum.php`**: the `middleware.verify_csrf_token` entry points to the same class so SPA/stateful flows stay consistent.

### Cache configuration (security default)

- **`config/cache.php`**: added **`serializable_classes` => false** to match Laravel 13 defaults and harden cache deserialization if `APP_KEY` were ever compromised. If the application intentionally caches PHP objects, those classes must be allow-listed there.

Existing explicit defaults (for example `CACHE_PREFIX` and session cookie naming) were left as-is where the project already defined them.

## 3. PHPStan and dynamic SQL (`SqlExpr`)

### What broke after the upgrade

Laravel 13’s stubs (used by **PHPStan** via **Larastan**) treat the first argument of `DB::raw()`, `whereRaw()`, `selectRaw()`, `orderByRaw()`, and `orWhereRaw()` as **`literal-string`** (or `Expression`) in many signatures. The museum catalog builds **dynamic SQL** (MySQL `FIELD()`, correlated subqueries, locale fallbacks) using concatenation and helpers such as `TranslationDisplaySql`. Those fragments are **safe by construction** (validated table/column paths, bindings for user-driven values) but are still typed as generic `string` by static analysis, which produced a large set of **`argument.type`** errors.

### What we introduced

**`App\Support\Database\SqlExpr`** centralizes:

- A single, documented place for “trusted SQL built by the application.”
- Narrow `/** @phpstan-ignore argument.type */` usage **only** on the delegating calls to Laravel’s raw APIs.
- Generic `@template` annotations so `Builder<Item>`, `Builder<Tag>`, and so on remain valid without template covariance noise.

Helper entry points:

- `SqlExpr::raw()` → `DB::raw()`
- `SqlExpr::selectRaw()`, `orderByRaw()`, `whereRaw()`, `orWhereRaw()` → the same methods on `EloquentBuilder` / `QueryBuilder`
- `SqlExpr::relationWhereRaw()` → `Relation::whereRaw()` (used from `Item::translation()`)

### Files that call `SqlExpr`

| Area | Files |
|------|--------|
| Models | `app/Models/Catalog/Extra.php`, `Item.php`, `ItemComponent.php`, `ItemTag.php`, `app/Models/Language.php` |
| Services | `app/Services/Catalog/ItemCategoryService.php`, `ItemService.php`, `app/Services/Taxonomy/TagCategoryService.php`, `TagService.php` |
| Support | `app/Support/Admin/AdminIndexQueryBuilder.php`, `app/Support/Catalog/ItemIndexQueryBuilder.php`, `app/Support/Content/TranslationDisplaySql.php`, `app/Support/Database/SqlExpr.php` |

### `TranslationDisplaySql` typing

- Public expression helpers now type-hint **`Illuminate\Contracts\Database\Query\Expression`** (what `DB::raw()` returns).
- Subquery string builders are documented with **`@return non-falsy-string`** so `SqlExpr::raw()`’s contract stays satisfied.

**Performance:** `SqlExpr` does not change generated SQL or database workload; it is a thin wrapper for static analysis and documentation.

## 4. Style / CI housekeeping

- **PHP_CodeSniffer**: the `whereRaw` method signature in `SqlExpr.php` was wrapped across multiple lines to satisfy the **120-character** line limit (`Generic.Files.LineLength.TooLong`).
- The **`SqlExpr`** class docblock describes **when to use** this helper (PHPStan / dynamic SQL) and **when not to** (untrusted input concatenated into SQL).

```
- **♻️ refactor: last refactor:**

```md
## Documentation and naming

- **Deploy references:** `README.md` and `.env.example` now point to `docs/deploy/` (replacing obsolete `deploy-docs/` paths).
- **SPP → SDD:** Technical AI-facing doc renamed from `docs/spp.md` to **`docs/sdd.md`** (*software design document*). `docs/prd.md` and review markdown files were updated to reference `sdd.md`.
- **PHP import style:** `docs/sdd.md` documents grouped `use` statements (same namespace, brace syntax), aligned with controllers such as `ItemController` and `AdminItemController`.
- **Admin edit locks:** **`docs/internal/edit-locks.md`** explains why partial edit actions (image delete, QR regenerate/delete) call `requireUnlocked` but do **not** call `unlock`, unlike the full item `update` flow. Related PHPDoc was added on `AdminItemImageController` and `AdminItemQrCodeController`.

## Public item contribution

- **`StoreItemContributionAction`:** Constructor parameter renamed from `$requestServices` to **`$requestContext`**. Class/method docs state that **redirect and flash** remain the HTTP caller’s responsibility (e.g. `ItemController::store`).
- **`PublicCatalogContributionOutcome`:** Unknown contribution statuses no longer throw a bare `InvalidArgumentException` (HTTP 500). They **log a warning** and throw **`ValidationException`** on the `email` field with a translated message (`contribution_unexpected` in `lang/*/app/catalog.php`).
- **`PersistsContribution`:** Documents sync with `PublicCatalogContributionOutcome` for early-return statuses. **QR generation** (`ItemQrCodeService::regenerateForItem`) runs **after** the database transaction commits (same request, synchronous), avoiding holding a DB transaction during external HTTP.
- **Rate limiting:** Dedicated throttle **`catalog-item-contribution-store`** (per IP) on the public item store route, in addition to the existing public web throttle.
- **Contribution structure:** `docs/sdd.md` includes a traits table for `StoreItemContributionAction` (request context, collaborator resolution, payload prep, persistence, item creation, completion).

## Catalog contribution validation and components

- **`ComponentRequest`:** `components.*.item_id` must **`Rule::exists` on `items.id` with `validation = true`**, so POST tampering cannot link to unvalidated catalog rows.
- **`ItemComponentService::attachContributedComponents`:** Double-checks that each referenced component item exists and is **validated** before creating `item_component` rows; uses `validation.catalog.component_item_must_be_validated` when not.
- **Tests:** `ItemComponentServiceTest` and `StoreItemContributionTest` extended for validated vs unvalidated component targets.

## Admin QR code UX

- **`AdminItemQrCodeController::regenerate`:** Wrapped `regenerateForItem` in **`try/catch`**, **`report($e)`**, and redirect with **`withErrors`** and `app.catalog.item.qrcode_regenerate_failed` (EN/PT). Feature test added for HTTP failure from the QR API.

## Services and tests (misc.)

- **`CatalogItemViewDataService`:** In-request memoization for **`localeFormOptions()`** to avoid redundant work on the same service instance.
- **`ItemTagServiceTest`:** Case passing explicit **`contentLanguageId`** (`Language::idForCode('pt_BR')`); redundant `assertNotNull` removed for PHPStan.
- **`StoreItemContributionRequestContextTest`:** Stronger coverage (e.g. empty body validation) where MySQL-backed tests apply.
- **`ResolvesCollaboratorForContribution`:** If `resolveForContribution` returns `ok` without a `Collaborator` instance, the code throws **`LogicException`** instead of returning a misleading `internal_blocked`. **`PublicContributionCollaboratorSupport`** PHPDoc narrows the `ok` branch to a non-null collaborator.

## Code quality baseline

- **`declare(strict_types=1);`** added across PHP under **`app/`**, **`routes/`**, **`config/`**, **`bootstrap/`**, **`tests/`**, **`database/`**, and **`lang/`**. Entry scripts **`public/index.php`** and **`artisan`** were left unchanged (typical Laravel layout).
- **PHPStan:** Post-transaction QR block simplified so inferred types match reality (no redundant `isset` / `=== 'ok'` on a shape that is always success after the transaction closure).

## Product docs (PRD / SDD)

- **`docs/prd.md`** and **`docs/sdd.md`** changelogs updated for deploy paths, rate limits, SDD rename, strict types, validated-only public components, and the edit-lock internal note.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **REFACTOR**

### ⏳ Time spent:
- **12 HOURS** (approximate)

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
