---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 45
github_pull_request_id: 3463445325
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/45
state: closed
draft: False
author: vinifen
created_at: 2026-03-29T23:38:19Z
updated_at: 2026-04-04T00:06:12Z
merged_at: 2026-04-04T00:01:18Z
closed_at: 2026-04-04T00:01:18Z
head_ref: @vinifen/feat/44/multiple-languages
base_ref: develop
title: "✨ feat: multiple languages support"
---

# ✨ feat: multiple languages support

# ✨ Multiple languages support
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #44
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- **restructuring to accept multiple languages:**

```md

## High-level goals

- Store translatable text in dedicated `*_translations` tables keyed by `language_id`, instead of single-language columns on the main entities.
- Align app locale (`pt_BR`, `en`, etc.) with rows in `languages`, including a **`neutral`** code for locale-agnostic copy.
- Resolve which translation to show using a **single ordered fallback chain** shared by Eloquent (`TranslationResolution`) and MySQL list queries (`FIELD(l.code, …)` via `TranslationDisplaySql`).
- Let visitors **switch catalog language** via session (`POST /locale`) without changing only Laravel’s default locale behavior in isolation.

---

## Database & migrations

### Migration batch replacement

- **Removed** the old dated migration set (`2026_03_01_*` and `2026_03_01_100000_*`).
- **Added** a new ordered set prefixed `2026_03_29_*` (plus `2026_03_29_100000_create_item_images_table.php`).

### New / changed schema (conceptual)

| Area | Change |
|------|--------|
| **`languages`** | New table; seeded with `pt_BR`, `en`, and `neutral`. |
| **Item categories** | Base table holds non-translatable data; **`item_category_translations`** holds `name` (and ties to `language_id`). |
| **Tag categories** | Same pattern with **`tag_category_translations`**. |
| **Items** | Core row keeps dates, codes, validation, relations; **`item_translations`** holds `name`, `description`, `history`, `detail`. |
| **Tags** | Tag row holds validation and category; **`tag_translations`** hold display name per language. |
| **Extras** | Extra row holds relations/validation; **`extra_translations`** hold `info`. |
| **Pivot** | **`item_tag`** table (replacing prior naming in the old migration set). |

Other tables (admins, collaborators, locks, sessions, item components, item images) are recreated in the new batch with compatible structure for the updated FK graph (items/categories/tags depend on `languages` where needed).

### Tables added (new)

| Table | Purpose / main columns |
|-------|-------------------------|
| **`languages`** | `code` (unique), `name`; seeded: `pt_BR`, `en`, `neutral`. |
| **`item_category_translations`** | `item_category_id`, `language_id`, `name`; unique `(item_category_id, language_id)`. |
| **`tag_category_translations`** | `tag_category_id`, `language_id`, `name`; unique `(tag_category_id, language_id)`; migration seeds default labels for the two seeded categories. |
| **`item_translations`** | `item_id`, `language_id`, `name`, `description`, `history`, `detail`; unique `(item_id, language_id)`. |
| **`tag_translations`** | `tag_id`, `language_id`, `name`; unique `(tag_id, language_id)`. |
| **`extra_translations`** | `extra_id`, `language_id`, `info`; unique `(extra_id, language_id)`. |

### Tables modified (columns moved or removed vs `2026_03_01_*`)

These tables **keep the same name** but their columns changed relative to the previous migration batch.

| Table | Before (approx.) | After (approx.) |
|-------|------------------|-----------------|
| **`item_categories`** | `id`, `name`, timestamps | `id`, timestamps only — `name` lives in **`item_category_translations`**. |
| **`tag_categories`** | `id`, `name`, timestamps | `id`, timestamps only — `name` lives in **`tag_category_translations`**; base migration still inserts two category rows (labels come from the translations migration). |
| **`items`** | `name`, `description`, `history`, `detail`, `date`, `identification_code`, **`image`**, `validation`, `category_id`, `collaborator_id`, timestamps | `date`, `identification_code`, `validation`, `category_id`, `collaborator_id`, timestamps — translatable strings in **`item_translations`**; single **`image`** column removed (use **`item_images`**). |
| **`tags`** | `name`, `validation`, `tag_category_id`, timestamps | `validation`, `tag_category_id`, timestamps — `name` in **`tag_translations`**. |
| **`extras`** | `info`, `item_id`, `collaborator_id`, `validation`, timestamps | `item_id`, `collaborator_id`, `validation`, timestamps — `info` in **`extra_translations`**. |

### Tables unchanged in shape (recreated in new migration files)

Same logical columns as in the old batch; only the migration filename / ordering changed (and **`item_tag`** is now its own migration file instead of being created in the same file as **`tags`**).

| Table | Notes |
|-------|--------|
| **`item_tag`** | `tag_id`, `item_id`, `validation`, timestamps (pivot). |
| **`item_component`** | `item_id`, `component_id`, `validation`, timestamps. |
| **`item_images`** | `item_id`, `path`, `type` (`cover` \| `gallery`), `sort_order`, timestamps. |
| **`admins`** | `username`, `password`, timestamps. |
| **`collaborators`** | `full_name`, `contact`, `role` enum, `blocked`, timestamps. |
| **`locks`** | `lockable` morph, `admin_id`, `expiry_date`, timestamps. |
| **`sessions`** | `id`, `admin_id`, `ip_address`, `user_agent`, `payload`, `last_activity`. |

---

## Domain models

- **`Language`**: lookup helpers (`idForCode`, `tryIdForCode`, `idForPreferredFormLocale`), in-memory ID cache invalidated on save/delete.
- **Translation models**: `ItemTranslation`, `ItemCategoryTranslation`, `TagTranslation`, `TagCategoryTranslation`, `ExtraTranslation` — each linked to `Language` and parent entity.
- **Parents** (`Item`, `ItemCategory`, `Tag`, `TagCategory`, `Extra`): refactored to use `hasMany` translations, accessors/helpers, and **`resolveTranslation()`** returning `ResolvedTranslation` (see below). **`Item`** gained the bulk of the resolution and display logic updates.
- **`ItemComponent`**, **`ItemTag`**: small adjustments for the new schema/relations where applicable.

---

## Content locale & resolution (`app/Support/Content/`)

- **`ContentLanguage` enum** (`app/Enums/Content/`): canonical codes `pt_BR`, `en`, `neutral`; `defaultForForms()` and stable ordering for non-neutral locales.
- **`ContentLocaleFallback`**: maps `app()->getLocale()` to a `languages.code` (e.g. `pt` → `pt_BR`); builds **`orderedCodes()`** for fallback: current locale → neutral → `config('app.fallback_locale')` → remaining locales; exposes **`fieldListSql()`** for MySQL `FIELD()`.
- **`TranslationResolution`**: given a collection of translation rows (with `language`), picks the first match following `orderedCodes()`, with deterministic tie-break; returns **`ResolvedTranslation`** (`translation`, source code, whether it matched the “requested” locale).
- **`TranslationDisplaySql`**: correlated subqueries using `FIELD(l.code, …)` so **lists, search, and sorts** use the same fallback order as PHP (items, categories, tags, tag categories, extras).
- **`TranslatablePayload`**: support type(s) for building/saving translation payloads where used.

---

## HTTP layer

- **`SetLocaleFromSession` middleware** (appended to the `web` stack): if session key `locale` is `pt_BR` or `en`, calls `app()->setLocale(...)`.
- **`POST /locale`** (`routes/web.php`): validates allowed codes, stores `locale` in session, redirects back — pairs with the middleware for public language switching.
- **Controllers** (`ItemController`, admin item/extra controllers): adapted to load/resolve translations for show/edit/index flows.
- **Form requests & validators**: admin and catalog requests updated so translatable fields validate against the new structure (e.g. nested translation input or language-scoped rules). **`AdminStoreExtraRequest`** added for extra store validation.
- **`StoreItemContributionAction`**: creates/updates contributions using translation rows and preferred language IDs.

---

## Services & admin index

- **`ItemService`**, **`ItemCategoryService`**, **`ExtraService`**, **`TagService`**, **`TagCategoryService`**, **`ItemTagService`**: persist and query translations; tag **`findOrCreate`** accepts both `category_id` and `tag_category_id` style input (covered by a feature test).
- **`AdminIndexConfig`** / **`AdminIndexQueryBuilder`**: admin listing columns and queries updated to use resolved translation SQL or relations where needed.
- **`ItemIndexQueryBuilder`**: public catalog index uses **`TranslationDisplaySql`** for visible fields and search across translated columns.

---

## Views & frontend strings

- Catalog item **show** and partials (sidebar, timelines) pass **`ResolvedTranslation`** (or equivalent) and show copy from the resolved row.
- **`translation-fallback-notice.blade.php`**: when `ResolvedTranslation::usedFallback()` is true, shows a muted notice (via `view.catalog.translation_fallback_notice`).
- Admin item **edit** and related partials adjusted for translatable fields.
- **`lang/en` and `lang/pt_BR`**: new validation/catalog strings for the above.
- **`resources/js/i18n.js`**: minor tweak (locale alignment).

---

## Infrastructure & tooling

- **`phpstan.neon`**: updated paths/rules to include new code cleanly.
- **`config/database.php`**: comment translated to English (PHP 8.5+ PDO MySQL SSL attribute note).
- **`AdminDatabaseSessionHandler`**: small compatibility fix for the migration/session context.
- **Factories** (`Item`, `ItemCategory`, `Extra`, `Tag`): create translation rows consistent with the new schema.
- **Seeders** (`ItemCategorySeeder`, `TagCategorySeeder`): seed translation data alongside base rows.

---

## Tests (new)

| Test | Purpose |
|------|---------|
| `tests/Unit/Content/ContentLocaleFallbackTest.php` | `pt` normalizes to `pt_BR`; `orderedCodes()` starts with normalized locale. |
| `tests/Feature/Catalog/TranslationResolutionTest.php` | Item `resolveTranslation()` prefers `pt_BR` vs `en` when app locale changes. |
| `tests/Feature/Catalog/TagFindOrCreateTest.php` | `TagService::findOrCreate` deduplicates by name/category across input key variants. |

Tests skip when no PDO driver is available (mysql/sqlite).

---

## Statistics (approximate)

- **~61 files** touched in the working tree diff stats for tracked changes; **large net addition** of lines vs deletions, driven by models, services, SQL helpers, and migrations.
- **Many new untracked files**: enums, middleware, translation models, migrations, Blade partial, and tests listed in `git status`.
```

- **fix setup vite:**

```md
**Files:** `.env.example`, `docker-compose.local.yml`, `run`, `vite.config.js`

- **`vite.config.js`:** Vite listens on `0.0.0.0` in Docker; dev asset URLs and HMR use `localhost:5173`; `cors: { origin: true }` so scripts load when the app is served from nginx on another port (e.g. `:9090`); `watch.usePolling` for bind-mounted sources.
- **`docker-compose.local.yml`:** `web` service `depends_on: vite` so the Vite container starts with the stack.
- **`run`:** `npm-local-bg` only runs `npm install` in the vite container—no second `npm run dev` (avoids port conflict with the Compose-managed dev server); setup messaging updated.
- **`.env.example`:** short note that the browser must reach Vite at `http://localhost:5173`.
```

- **finish multiple language support:**

```md

Listed **oldest → newest** (reverse of default `git log` order).

### 1. Admin language switch

- **`SetLocaleFromSession`**: UI locale validation no longer uses a hardcoded enum list; it delegates to **`Language::isValidSessionUiLocale()`** so allowed session locales stay aligned with configured languages.
- **`Language` model**: initial support used by the middleware and provider (e.g. session locale validation).
- **`AppServiceProvider`**: registers / shares language-related configuration for the app.
- **Admin layout copy**: `lang/en/view/admin/layout.php`, `lang/pt_BR/view/admin/layout.php`.
- **`resources/views/components/layouts/admin.blade.php`**: admin language switcher UI.
- **`routes/web.php`**: small routing adjustments tied to admin / locale behavior.

### 2. Public language switch

- **`Language` model**: additions for the public locale switcher (e.g. listing choices for the UI).
- **`AppServiceProvider`**: further wiring for public vs admin locale behavior.
- **`lang/en/view/layout.php`**, **`lang/pt_BR/view/layout.php`**: strings for the public language control.
- **`phpstan.neon`**: adds an **ignore pattern** for PHPStan on **`Language::forLocaleSwitcher()`** return type (not a functional runtime change).
- **`resources/sass/custom.scss`**: styles for the public language switcher.
- **`resources/views/components/layouts/app.blade.php`**: public site language selector and layout integration.
- **`resources/views/components/layouts/admin.blade.php`**: minor tweaks alongside the public layout work.

### 3. Admin item edition with several languages

- **`AdminItemController`**: create/update flows handle per-locale item payload.
- **`AdminItemTranslationsRules`**: new validation rules for item translations (~111 lines added in that commit).
- **`AdminStoreItemRequest`**, **`AdminUpdateItemRequest`**: integrated with translation validation.
- **`Item` model**, **`ItemService`**: load/save translated fields across languages.
- **`Language`**: small follow-ups for item forms.
- **`lang/*/validation.php`**, **`lang/*/view/admin/catalog.php`**: messages and admin catalog strings for translations.
- **Blade**: new **`items/_partials/translation-tabs.blade.php`**; admin item **`create.blade.php`** / **`edit.blade.php`** refactored around tabbed per-language fields.

---

## Uncommitted work (working tree vs `HEAD`)

Snapshot: **`git diff --stat HEAD`** reports **95 files changed**, **1674 insertions(+), 686 deletions(-)** (plus **untracked** files listed below). Grouped by theme.

### Configuration and documentation

- **`.env.example`**, **`README.md`**: environment examples and documentation for multilingual / content-locale behavior.
- **`phpunit.xml`**: test configuration adjustments.
- **`vite.config.js`**: build config updates (bundling / inputs related to frontend changes).

### Content locale and HTTP helpers

- **`ContentLanguage` enum**: clarified or extended for content vs UI locale and form defaults.
- **`OptionalContentLocale`** (`app/Support/Http/OptionalContentLocale.php`): reads optional **`content_locale`** from the request (query/body); empty means “use site fallback”; non-empty must match **`languages.code`**, otherwise throws **`ValidationException`** with `content_locale` errors.

### Database

- Migrations adjusted: **`languages`**, **`tag_categories`**, **`tag_category_translations`**.
- **`ItemCategorySeeder`**, **`ItemFactory`**: aligned with translation data and relations.

### Models and shared concerns

- **`Item`**, **`ItemTranslation`**, **`ItemComponent`**, **`ItemTag`**, **`Extra`**, **`ItemCategory`**, **`Tag`**, **`TagCategory`**, **`Collaborator`**: translation relations, accessors, or slimmer models (e.g. categories/tags delegating shared behavior).
- **`Lock`** and **`LockService`**: **per-request cache** for **`findByModel()`** (invalidated on lock save/delete), use of **`getKey()`** for the lockable id, and **`requireUnlockedThenLock()`** so **`requireUnlocked()`** + **`lock()`** do not each query the DB separately — performance/correctness for admin edit flows (same branch as multilingual admin work, not content-locale logic per se).
- **`Language`**: further methods and integration beyond the last committed state.

**New trait:** `app/Models/Concerns/SyncsAdminFormNameTranslations.php` — **`syncTranslationsFromAdminForm()`** and related helpers for models whose main translatable admin field is **`name`** (item categories, tag categories, tags), including empty-name cleanup via deleting translation rows.

### Admin HTTP layer

- Controllers updated: **extras**, **item categories**, **item tags**, **items**, **collaborators**, **tag categories**, **tags** — load/save translations, pass locale context, use new request rules.
- **Requests**
  - **`AdminItemCategoryRequest`**, **`AdminStoreExtraRequest`**, **`AdminTagCategoryRequest`**, **`AdminItemTranslationsRules`**: multi-locale validation and structure (rules files evolved after `bfb7316`).
  - **Removed (tracked deletion):** `AdminSingleTagRequest.php`.
  - **New (untracked until committed):** `AdminExtraTranslationsRules.php`, `AdminItemCategoryTranslationsRules.php`, `AdminTagCategoryTranslationsRules.php`, `AdminTagTranslationsRules.php`, `AdminTagRequest.php`.
- **Support**
  - **`AdminEditHeadingLocale.php`**: admin edit headings / locale display helpers.
  - **`AdminTranslatableNameFormRules.php`**: shared validation for translatable `name` fields in admin forms.

### Catalog services and queries

- **`ItemService`**, **`ExtraService`**, **`ItemCategoryService`**, **`ItemTagService`**, **`TagService`**, **`TagCategoryService`**: persist and resolve translated attributes on create/update/show.
- **`ItemIndexQueryBuilder`**, **`TranslationDisplaySql`**: listing/display SQL for translation resolution.
- **`StoreItemContributionAction`**, **`ItemContributionValidator`**, **`StoreItemRequest`**, **`ComponentRequest`**, **`SingleExtraRequest`**: contribution and public item flows respect content locale where applicable.
- **`ContributionContentLocaleService`**: builds **contribution/extra form** options (`contributionLanguages`, `defaultContentLocale`) using **`Language::forAdminContentForms()`** and **`ContentLocaleFallback`**; **not** responsible for persisting the item itself (per class docblock).

### Public catalog and routes

- **`ItemController`**, **`TagController`**, **`CollaboratorController`**: resolved translations and optional **`content_locale`** on JSON/list endpoints where implemented.
- **`routes/web.php`**: route or middleware adjustments for locale-related endpoints.
- **Catalog views**: item show/create, filters, sidebars, extra modal, timelines — translated strings and locale-aware behavior.
- **Admin views**: extras, categories, tags, tag categories, items, collaborators — translation tabs and shared partials.
- **`language-tab-label.blade.php`**, **`info-popover.blade.php`**, **`custom.scss`**, **`admin.blade.php`**: shared UI for tabs/popovers/layout.

### Identity / admin services

- **`AdminService`**: small updates alongside admin/locale behavior.

### Frontend (JavaScript)

- **`i18n.js`**: client-side locale / message handling updates.
- **`section-item-selector.js`**, **`check-contact.js`**, **`component-modal.js`**, **`tag-modal.js`**: payloads or UX aligned with multilingual catalog data.
- **`popover-button.js`**: larger update (interaction / positioning / integration with new UI).

### Tests

- **Updated:** `TagFindOrCreateTest`, `TranslationResolutionTest`, `ContentLocaleFallbackTest`.
- **New (untracked):** `OptionalContentLocaleJsonTest` — asserts **422** + JSON validation errors for invalid **`content_locale`** on **`catalog.items.byCategory`** and **`catalog.tags.autocomplete`**.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **FEAT**

### ⏳ Time spent:
- **15 HOURS** (approximate)

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
