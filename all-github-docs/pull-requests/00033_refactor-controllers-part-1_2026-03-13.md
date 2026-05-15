---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 33
github_pull_request_id: 3360133103
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/33
state: closed
draft: False
author: vinifen
created_at: 2026-03-05T17:53:47Z
updated_at: 2026-03-13T21:01:21Z
merged_at: 2026-03-13T21:00:58Z
closed_at: 2026-03-13T21:00:59Z
head_ref: @vinifen/refactor/32/controllers
base_ref: develop
title: "♻️ refactor: controllers part 1"
---

# ♻️ refactor: controllers part 1

# ♻️ Refactor Catalog and Admin Application Layer
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #32 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- **AdminItemController & Requests:**
```md
# Refactoring Summary (uncommitted)

Short overview of the refactor done so far.

## 1. Admin Item flow → Services

- **ItemService** (new): item CRUD and list for admin.
  - `getPaginatedItemsForAdminIndex(Request)` – list with search/sort via `AdminIndexQuery`.
  - `getSectionsAndCollaborators()` – sections + collaborators for create/edit forms.
  - `createItemWithIdentificationCode(AdminStoreItemRequest, ItemContributionService)` – create item + set identification code in a transaction.
  - `updateItem(Item, array)` – update attributes + `normalizeSingleCover()`.
  - `deleteItem(Item)` – delete item.
- **ItemImagesService** (new): all item image logic.
  - Store: `storeImagesFromStoreRequest(Item, AdminStoreItemRequest)` (cover + gallery, then `normalizeSingleCover()`).
  - Update: `processDeleteImageIds`, `processCoverImage`, `processGalleryImages(Item, AdminUpdateItemRequest)`.
  - Delete: `deleteAllImagesForItem(Item)`, `deleteImage(Item, ItemImage)` (with “image belongs to item” check in service).
- **AdminItemController** uses route model binding (`Item $item`, `ItemImage $image`) and only calls the two services + lock/unlock; no `Item::` or image logic in the controller.
- **Update**: validated data filtered with `Arr::except()` instead of multiple `unset()`.

## 2. Index search/sort → Support

- **BuildsAdminIndexQuery** trait (in `Http/Controllers/Admin/Concerns`) **removed**.
- **App\Support\AdminIndexQuery** (new): static `applySearch(Builder, ...)` and `applySort(Builder, ...)` with the same config (baseTable, searchSpecial, sortSpecial).
- **ItemService** and admin index controllers (AdminItemController, AdminTagController, AdminItemTagController, AdminItemComponentController, AdminExtraController) call `AdminIndexQuery::applySearch` / `applySort` with their own config; no controller concern.

## 3. Admin Form Requests

- Admin-only requests **moved** under `App\Http\Requests\Admin\` (e.g. `Admin\Catalog\AdminStoreItemRequest`, `AdminUpdateItemRequest`, `AdminItemCategoryRequest`, `AdminTagCategoryRequest`, etc.).
- Old request files under `Catalog`, `Collaborator`, `Identity`, `Taxonomy` **deleted** (replaced by `Admin\*`).
- **AdminItemCategoryController** and **AdminTagCategoryController** now import and use the new request classes (fixes PHPStan “class not found”).

## 4. Item date nullable

- **Migration** `create_items_table`: `date` column set to `nullable`.
- **Views** (admin + public): show “Data desconhecida” / “—” when `$item->date` is null instead of checking for year `0001`.
- Backend no longer uses sentinel `0001-01-01`; null is stored when date is missing.

## 5. ItemContributionService (public flow)

- Store method **reordered**: required `ItemImagesService $itemImagesService` before optional `?array $galleryImages = null` (PHP 8.1 compatibility).
- **ItemController** (public) passes `ItemImagesService` and calls the service with the new parameter order.
- Image storage for public contribution uses `ItemImagesService` (shared with admin).

## 6. Linting / static analysis

- **Line length (phpcs)**: Long lines split in `ItemService` (docblock, method signature) and `ItemImagesService` (array_filter).
- **PHPMD**: `Item` model – `@SuppressWarnings(PHPMD.CouplingBetweenObjects)` (many relations).
- **PHPStan**:  
  - `Item::scopeForAdminList`: `@param Builder<Item> $query`.  
  - `ItemService`: generics in `@return` for paginator and collections.  
  - `AdminIndexQuery`: `@template T of Model` and `@param Builder<T> $query` so any `Builder<ConcreteModel>` is accepted.

## Files touched (summary)

- **New**: `app/Services/Catalog/ItemService.php`, `app/Services/Catalog/ItemImagesService.php`, `app/Support/AdminIndexQuery.php`, `app/Http/Requests/Admin/*`.
- **Deleted**: `app/Http/Controllers/Admin/Concerns/BuildsAdminIndexQuery.php`, several old request classes (replaced by Admin namespace).
- **Modified**: AdminItemController, AdminExtraController, AdminItemCategoryController, AdminItemComponentController, AdminItemTagController, AdminTagController, AdminTagCategoryController, AdminCollaboratorController, AdminController, ItemController; Item model; ItemContributionService; migration `create_items_table`; admin and public views for items (and related show views) for date display.
``` 

- **ItemController:**

```md

### 1. Public Item Contribution Flow

- Introduced `StoreItemContributionAction` as the single orchestrator for the public contribution flow (`app/Actions/Catalog/StoreItemContributionAction.php`).
  - `handle()` now receives explicit arrays for collaborator, item, tags, extras and components, plus optional cover image and gallery images.
  - It resolves/validates the collaborator, creates the item in a transaction with an identification code, stores cover and gallery images, attaches tags, extras, and components, then redirects back to the contribution form with a success flash message.
- `ItemController::store` (`app/Http/Controllers/Catalog/ItemController.php`) now:
  - Uses `ItemContributionValidator::validateStore()` to build the contribution payload.
  - Uses `ItemImagesService::filterValidGalleryFiles()` to clean the `gallery_images` array.
  - Calls `StoreItemContributionAction::handle(...)` directly with the validated pieces instead of building a DTO.
- `ItemImagesService` (`app/Services/Catalog/ItemImagesService.php`) gained a reusable helper:
  - `filterValidGalleryFiles(?array $galleryFiles): array` which returns only valid `UploadedFile` instances.
  - Admin image creation flow now uses this helper instead of duplicating the filter logic.
- The previous DTO `App\Data\Catalog\StoreContributionData` was removed; all data is passed as method parameters and documented via detailed PHPDoc type annotations.

### 2. Public Item Reading and Index

- `ItemService` (`app/Services/Catalog/ItemService.php`) gained two public read methods:
  - `getPublicItemForShow(string $id): Item` loads an item with its images and aborts with 403 if the item is not validated.
  - `getPublicItemsByCategory(string $itemCategoryId): Collection` returns only validated items for the given item category, ordered by name.
- `ItemController` now delegates model access to the service:
  - `show()` calls `ItemService::getPublicItemForShow($id)` instead of querying `Item` directly.
  - `byCategory()` calls `ItemService::getPublicItemsByCategory($itemCategoryId)` and returns the result as JSON.
  - `edit()` no longer type‑hints `Item` and simply aborts with 404 to avoid exposing an edit form in the public catalog.
- `ItemIndexQueryBuilder` (`app/Services/Catalog/ItemIndexQueryBuilder.php`) was cleaned up and made more explicit:
  - Still returns `['items' => LengthAwarePaginator, 'categoryName' => string]`.
  - Internals renamed for clarity (e.g. `applyItemCategoryFilter`, `applySearchFilter`, `applyTagCategoryFilter`, `applyTagFilter`, `applySort`, `resolveItemCategoryName`).

### 3. Item Category Naming and Relations

- `Item` model (`app/Models/Catalog/Item.php`) was made more explicit regarding item categories:
  - Relationship `category()` was renamed to `itemCategory()` and now explicitly uses `'category_id'` as the foreign key.
  - In the `scopeForAdminList` scope, the alias `category_name` was renamed to `item_category_name`.
- All Blade views that referred to the item category via `$item->category` or `$item->category_name` were updated:
  - Now use `$item->itemCategory` and `$item->item_category_name` where they refer to the item’s category.
  - Tag category usages (`$tagItem->tag->category`) remain unchanged, as they refer to tag categories.

### 4. Single Extra Contribution (Public)

- Created a dedicated `ExtraController` (`app/Http/Controllers/Catalog/ExtraController.php`) for public extra contributions:
  - `store()` validates the request via `ItemContributionValidator::validateSingleExtra()` and delegates creation to `ExtraService::storeSingleExtra()`.
- Adjusted public routes (`routes/web.php`):
  - Replaced `POST items/extras` (handled by `ItemController::storeSingleExtra`) with `POST /extras` handled by `ExtraController::store` (`name: extras.store`).
- Updated the public extra modal (`resources/views/catalog/items/show-modals/extra-modal.blade.php`):
  - Form action changed from `route('items.store-extra')` to `route('extras.store')`.
- Removed `storeSingleExtra()` and related imports from `ItemController`; public item controller now focuses only on items.

### 5. Admin Lists, Filters and Services

- `ItemCategoryService` (`app/Services/Catalog/ItemCategoryService.php`):
  - `getForIndex()` returns a light `select('name', 'id')` for use in filters.
  - New `getForForm()` returns all item categories ordered by name, used to populate admin item forms.
- `CollaboratorService` (`app/Services/Collaborator/CollaboratorService.php`):
  - New `getForForm()` returns collaborators ordered by `full_name` for admin dropdowns.
- `AdminItemController` (`app/Http/Controllers/Admin/Catalog/AdminItemController.php`) now:
  - Uses `ItemCategoryService::getForForm()` and `CollaboratorService::getForForm()` in `create()` and `edit()` to get form data.
  - No longer relies on `ItemService::getItemCategoriesAndCollaborators()`, which has been removed to keep responsibilities separated.
- `AdminCollaboratorController` (`app/Http/Controllers/Admin/Collaborator/AdminCollaboratorController.php`) search logic:
  - Fixed boolean filter for the `blocked` column to compare against the string `'1'` after casting, avoiding impossible strict comparisons and matching how the admin search form posts values.

### 6. Tag Queries and Admin Search Utilities

- `QueryController` (`app/Http/Controllers/Catalog/QueryController.php`) was aligned with the actual schema:
  - All tag‑related queries now use `tag_category_id` instead of `category_id` on the `tags` table:
    - `tagNameAutoComplete`, `checkTagName`, and `getTags` now filter by `tag_category_id`.
  - This fixes runtime SQL errors when browsing `/items/{id}` and using AJAX tag/category filters.
- `AdminIndexQuery` (`app/Support/AdminIndexQuery.php`) remains the generic admin search helper:
  - It is now correctly used in combination with the fixed `tag_category_id` usage and keeps supporting special columns and boolean search via config (`searchSpecial`, `booleanColumns`).

### 7. Testing and Static Analysis

- All PHPUnit tests pass (`./run all-tests`).
- PHP CodeSniffer (phpcs) is clean after adjusting:
  - Line length and function declaration style in `StoreItemContributionAction`.
- Laravel Pint is clean after removing unused imports in `ItemController`.
- PHPStan issues were addressed by:
  - Adding detailed PHPDoc for iterable parameters in `StoreItemContributionAction::handle()`.
  - Fixing strict comparison logic in `AdminCollaboratorController` for the `blocked` filter.
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
