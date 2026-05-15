---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 29
github_pull_request_id: 3341908715
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/29
state: closed
draft: False
author: vinifen
created_at: 2026-03-01T23:10:17Z
updated_at: 2026-03-13T21:01:20Z
merged_at: 2026-03-01T23:14:31Z
closed_at: 2026-03-01T23:14:31Z
head_ref: @vinifen/feat/28/items-multiple-imagens
base_ref: develop
title: "✨ feat: multiple images on items"
---

# ✨ feat: multiple images on items

# ✨ Multiple images on items
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #28 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
## 1. Database

### 1.1 New `item_images` table

- **Migration:** `database/migrations/2026_03_01_100000_create_item_images_table.php`
- **Columns:** `id`, `item_id` (FK), `path`, `type` (`cover` | `gallery`), `sort_order`, `timestamps`
- **Index:** `(item_id, type)`

### 1.2 Legacy data migration

- **Migration:** `database/migrations/2026_03_01_100001_migrate_item_image_to_item_images_table.php`
- Copies values from `items.image` into `item_images` as `type = 'cover'` (skips external URLs).
- Drops the `image` column from the `items` table.
- English comments in the migration explain the `up()` and `down()` flow.

---

## 2. Models

### 2.1 `App\Models\Catalog\ItemImage` (new)

- Relationship `item()` (BelongsTo).
- Attribute `imageUrl()` (accessor): returns public storage URL or the `path` itself when it is already a URL.
- Static method `buildPath(Item $item, string $extension)` to generate storage paths.
- Enum `ItemImageType`: `COVER`, `GALLERY`.

### 2.2 `App\Models\Catalog\Item`

- Removed `image` from `$fillable`.
- Relationships: `images()` (HasMany), `coverImage()` (HasOne, type = cover).
- Accessor `image_url`: uses `coverImage` or the first image by `sort_order`.
- Method `normalizeSingleCover()`: ensures at most one image has `type = cover` (others are set to `gallery`).

---

## 3. Enum

- **File:** `app/Enums/ItemImageType.php`
- Cases: `COVER = 'cover'`, `GALLERY = 'gallery'`.

---

## 4. Controllers

### 4.1 `AdminItemController`

- **store:** Creates the item and, if `image` is present, saves it in `item_images` as cover. Calls `normalizeSingleCover()`.
- **update:**  
  - Processes `delete_image_ids[]`: removes listed images from storage and database.  
  - If a new cover image is uploaded (`$request->image`): removes old covers and saves the new one.  
  - If `set_cover_image_id` is set: promotes the given image to cover (only updates `type`/`sort_order`, no file deletion).  
  - Processes `gallery_images[]`: saves new images as `gallery`.  
  - Calls `normalizeSingleCover()`.
- **destroy:** Deletes all item images (storage + records) and the item.
- **destroyImage:** Extra route to delete a single image (kept for compatibility; in the edit form, deletion is done via `delete_image_ids` on submit).
- Image logic in update extracted into private methods (PHPMD): `processDeleteImageIds`, `processCoverImage`, `processGalleryImages`, `deleteItemImageFromStorage`, `storeNewCoverImage`, `promoteImageToCover`.

### 4.2 `ItemController` (public contribution)

- **store:** Uses `cover_image` and `gallery_images` from the request and passes them to `ItemContributionService`.

---

## 5. Services

### 5.1 `ItemContributionService`

- **store:**  
  - Resolves collaborator; validates blocked status and role.  
  - Creates item; saves cover (`cover_image`) and gallery (`gallery_images`) in `item_images`.  
  - Calls `normalizeSingleCover()`; saves tags, extras, and components.
- Private methods to reduce complexity (PHPMD): `resolveCollaborator`, `storeItemImages`, `storeCoverImage`, `storeGalleryImages`.
- PHPMD suppression: `CouplingBetweenObjects` (orchestration service).

### 5.2 `ItemIndexQueryBuilder`

- `baseQuery()`: eager loads `coverImage` instead of using the `image` column.

---

## 6. Validation (Form Requests)

### 6.1 `StoreItemRequest` (public contribution)

- `cover_image`: required, image, jpeg/png/jpg/webp, max 10MB.
- `gallery_images`: optional, array of images with the same rules.
- English docblock comment explaining cover vs gallery.

### 6.2 `UpdateItemRequest` (admin)

- `image`: optional (new cover).
- `gallery_images`: optional, array of images.
- `delete_image_ids`: optional, array of integers existing in `item_images`.
- `set_cover_image_id`: optional, integer existing in `item_images` (promote image to cover).

---

## 7. Routes

- **DELETE** `admin/items/{item}/images/{image}` → `AdminItemController@destroyImage` (name: `admin.items.images.destroy`).
- Route split across two lines in `routes/web.php` to satisfy PHPCS (line &lt; 120 characters).

---

## 8. Views

### 8.1 Admin – item edit (`admin/catalog/items/edit.blade.php`)

- **Cover** zone: shows the current cover (if any) inside the input; “Replace” button to change it.
- **Gallery** zone: drag-and-drop to add multiple images.
- “Current images” block: thumbnails with badge (Cover / Gallery), **Set as cover** button (star SVG icon) on gallery images, delete button (removes from DOM and sends `delete_image_ids[]` on submit).
- New images (preview) use a different badge colour (`bg-info`).
- Hidden field `set_cover_image_id` and container `admin-delete-image-ids` for submit.
- JS: when a new cover is chosen, the current cover thumbnail is hidden; new cover is inserted at the start of the list; removing an image only adds its id to `delete_image_ids[]` and removes the thumb (persisted on submit).

### 8.2 Admin – item show (`admin/catalog/items/show.blade.php`)

- “Cover” section with the first cover-type image (or first image).
- “Gallery” section with the remaining images.

### 8.3 Public – item create (`catalog/items/create.blade.php`)

- **cover_image** (required): drag-and-drop, preview with “Cover” badge, “Replace” button.
- **gallery_images** (optional): multi-file drag-and-drop, previews with “Gallery” badge.
- Preview block below the fields; JS validation for required cover before submit.
- Dynamic inputs for `gallery_images[]` injected into the form before submit.

### 8.4 Other views

- Listings and home use the item’s `coverImage` / `image_url`.

---

## 9. Translations (lang)

- Keys for cover/gallery, buttons (Replace, Set as cover, Delete), error messages, and image-area text in `pt_BR` and `en` (admin and catalog).

---

## 10. Seeders and factories

### 10.1 `ItemImageFactory`

- States `cover()` and `gallery()`; `path` generated with UUID.

### 10.2 `ItemFactory`

- No `image` field; state `withImages(int $total)` to create 1 cover + N gallery images.

### 10.3 `ItemSeeder`

- Creates items; for each item saves 1 cover and, for a subset of items, 0–4 gallery images, using seed file or fallback.

---

## 11. Code quality

### 11.1 PHPStan

- Use of `get()->each()` with `@var` to type the collection as `ItemImage`.
- Treating `$file->get()` as `string|false` before `Storage::put`.
- `normalizeSingleCover()`: null check for `$first` before using `$first->id`.
- `ItemImage::imageUrl()`: docblock `@return Attribute<string, never>`.
- Array typing in `ItemContributionService` (`@param array<string, mixed>`, `array<int, UploadedFile>`).
- Rules in `phpstan.neon`: HasOne, instanceof always true, `@SuppressWarnings` tag.

### 11.2 PHPMD

- Refactoring of `AdminItemController::update()` and `ItemContributionService::store()` into smaller methods.
- Suppressions: `TooManyPublicMethods` on `Item`, `CouplingBetweenObjects` on `ItemContributionService`.

### 11.3 PHPCS

- Long line in `routes/web.php` split (route `admin.items.images.destroy`).

---

## 12. Business rules

- **Single cover per item:** enforced by `normalizeSingleCover()` after create/update (admin and contribution).
- **Image deletion (admin):** by id in `delete_image_ids[]` on edit form submit; removes from storage and database.
- **Promote gallery to cover:** via `set_cover_image_id`; only updates `type` and `sort_order`, no file deletion.
- **New cover (upload):** removes old covers from storage and database and saves the new one.

---

## 13. Naming

- **Public contribution:** `cover_image` (cover) and `gallery_images` (gallery) in the request and view.
- **Admin:** `image` kept for the new cover upload in the edit form; `gallery_images` for new gallery images.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **FEAT**

### ⏳ Time spent:
- **3 HOURS** (approximate)

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
