---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 39
github_pull_request_id: 3426731642
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/39
state: closed
draft: False
author: vinifen
created_at: 2026-03-20T20:36:10Z
updated_at: 2026-03-20T20:42:28Z
merged_at: 2026-03-20T20:40:58Z
closed_at: 2026-03-20T20:40:58Z
head_ref: hotfix/view-item-&-migrates
base_ref: main
title: "🔥 hotfix: migrates & view items"
---

# 🔥 hotfix: migrates & view items

# 🔥Migrates & view items
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #N/A
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
## Public catalog — item show (`items.show`)

- **`Tag` model**: Added `category()` as an alias of `tagCategory()` so views can use `tag->category` (matches existing Blade usage).
- **`Item` model**: Added `scopeWithCatalogShowRelations()` to eager-load relations needed by the public show page (images, categories, tags, components, extras, etc.) and avoid N+1 queries.
- **`ItemService`**: `getPublicItemForShow()` uses `Item::query()->withCatalogShowRelations()->findOrFail(...)`.
- **`ItemController@show`**: Resolves the “series” tag category **by name once** (`name = 'Série'`) and passes `seriesCategoryId` to the view.
- **`show.blade.php`**: Timeline / “series” logic compares **`tag->category` id** to `seriesCategoryId` instead of hard-coding the string `'Série'` in multiple places; uses null-safe access where needed; closure uses `use ($seriesCategoryId)` so the variable is in scope inside `filter()`.

## Admin — extras index search

- **`AdminIndexConfig::extras()`**: Removed `searchBaseTable => 'items'`, which caused boolean and generic searches (including **validation**) to target the wrong table (`items` instead of `extras`). Validation filter now applies to `extras.validation`.

## Database migrations — foreign keys

Existing create-table migrations were updated so related rows are **not** deleted in cascade when a parent is removed; FK columns are **nullable** and use **`nullOnDelete()`** for:

- `items` → `item_categories`, `collaborators`
- `tags` → `tag_categories`
- `item_tag` → `tags`, `items`
- `extras` → `items`, `collaborators`
- `item_component` → `items` (both sides)
- `locks` → `admins`
- `sessions` → `admins`
- `item_images` → `items`

**Removed** migration `2026_03_01_100001_migrate_item_image_to_item_images_table.php` (data migration from `items.image` into `item_images` + dropping `items.image`). The `items` table still has an `image` column in `000005` for new installs that never ran the removed migration.

> **Note:** Changing migration files does not alter a database that was already migrated; use `migrate:fresh` or manual SQL if an existing DB still has `ON DELETE CASCADE`.

## Seeders

- **`DatabaseSeeder`**: All commented
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **HOTFIX**

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
