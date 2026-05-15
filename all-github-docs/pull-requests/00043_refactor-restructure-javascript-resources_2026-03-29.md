---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 43
github_pull_request_id: 3461707248
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/43
state: closed
draft: False
author: vinifen
created_at: 2026-03-29T01:59:10Z
updated_at: 2026-04-04T00:05:48Z
merged_at: 2026-03-29T17:07:01Z
closed_at: 2026-03-29T17:07:01Z
head_ref: @vinifen/refactor/42/javascript-restructuring
base_ref: develop
title: "♻️ refactor: restructure javascript resources"
---

# ♻️ refactor: restructure javascript resources

# ♻️ Restructure JavaScript Resources
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #42 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- **restructure js resources:**
```md
## Backend (Laravel / PHP)

- **`StoreItemContributionAction`**: Attaching components to a contributed item now follows the validated payload: each component is identified by **`item_id`** (the catalog item used as the component, stored as `component_id`), instead of resolving an item by **category + name**. Only `item_id`, `component_id`, and `validation` are persisted when creating `ItemComponent` rows.
- **`AdminItemController`**: New **`byItemCategory`** action returning JSON for admin UI (dependent selects).
- **`ItemService`**: New **`getItemsByItemCategoryForAdminSelect`**, listing items in a given item category (including non-validated) with `id` and `name`, ordered by name.
- **`routes/web.php`**: Route wiring updated for the new admin JSON endpoint (alongside existing public `items/by-category` usage).

---

## JavaScript architecture

### Build and entry points

- **`vite.config.js`** declares two inputs: **`resources/js/app.js`** (public site + shared catalog pieces) and **`resources/js/admin.js`** (admin panel only). This avoids shipping admin-only logic on public pages and keeps bundles easier to reason about.
- Both entries **`import './bootstrap'`** and **`import './i18n'`** first, so Bootstrap, jQuery, and i18next are initialized consistently.

### Public bundle — `resources/js/app.js`

- **Always loaded (static imports)**:
  - **`shared/catalog/upload-utils`** — shared upload helpers used across catalog flows.
  - **`shared/ui/img-modal`** — lightbox-style behavior for clickable catalog images.
  - **`shared/ui/popover-button`** — Bootstrap popovers and the small “info icon” interaction.
  - **`pages/catalog/items/index/explore-scroll`** — horizontal explore menu / scroll behavior on the catalog index.
  - **`pages/admin/collaborators/check-contact`** — AJAX check on collaborator contact fields. It is imported from **`app.js`** and from **`admin.js`** so both entry points cover forms rendered under public vs. admin layouts.
- **Conditionally loaded (dynamic imports + top-level `await`)** — only if **`#item-create-form`** is present:
  - **`pages/catalog/items/create/modals/tag-modal`**, **`extra-modal`**, **`component-modal`** — wizard modals for tags, extras, and components on the item contribution create form.
  - **`pages/catalog/items/create/form-session-restore`** — restores draft state from storage/session where applicable.
  - **`pages/catalog/items/create/item-images-upload`** — client-side image selection / preview / form integration for that page.
- **Rationale**: Heavy create-page code does not run on item **show** or other catalog routes; parallel **`Promise.all`** loads those modules together once the form marker exists.

### Admin bundle — `resources/js/admin.js`

- **Shared UI / catalog utilities**: `upload-utils`, `img-modal`, `popover-button` (same building blocks as public where admin needs them).
- **Admin-specific**:
  - **`shared/admin/search-form`** — admin search form behavior (previously much of this lived inline or in Blade).
  - **`shared/ui/admin-password-toggle`** — show/hide password fields in admin forms.
  - **`shared/release-lock-on-leave`** — releases edit locks on **`pagehide` / `beforeunload`** via **`sendBeacon`** / **`fetch`** with **`keepalive`**, unless the form was submitted.
  - **`pages/admin/catalog/section-item-selector`** — dependent select: loads items when an item-category (section) changes; uses **`data-*`** hooks, optional error host, reads **`data-admin-dependent-select-error`** from `<html>` for localized errors, calls the admin JSON items endpoint.
  - **`shared/admin/admin-delete-confirm`** — replaces many small **`components/warnings/delete*.js`** files: one table of **selector → i18n key**, delegated **`click`** handlers, optional **`data-confirm-message`** override.
  - **`pages/admin/catalog/items/create-images-upload`** and **`edit-images-upload`** — admin item image upload UX (preview, ordering, removal) extracted from large Blade scripts.
  - **`pages/admin/collaborators/check-contact`** — same module as above, explicitly included so admin collaborator create/edit pages bundled with **`admin.js`** run the check without relying on **`app.js`**.

### Shared modules — `resources/js/shared/`

| Area | Files (role) |
|------|----------------|
| **Admin** | **`admin-delete-confirm.js`** — consolidated delete **`confirm()`** wiring; **`search-form.js`** — admin search. |
| **Catalog** | **`upload-utils.js`**, **`catalog-item-image-upload-form.js`** — upload pipeline helpers; **`item-create-modal-helpers.js`**, **`item-create-storage.js`** — modal + session/local storage helpers for the contribution wizard; **`hide-bootstrap-modal.js`**, **`revoke-blob-url.js`** — modal teardown and object URL cleanup. |
| **UI** | **`img-modal.js`**, **`popover-button.js`**, **`admin-password-toggle.js`**. |
| **Cross-cutting** | **`release-lock-on-leave.js`** — lock release marker + **`FormData`** POST on leave. |

### Page modules — `resources/js/pages/`

- **`catalog/items/create/modals/*`** — tag, extra, and component modals (large files; encapsulate typeahead, validation, and form field sync for the contribution flow).
- **`catalog/items/create/form-session-restore.js`**, **`item-images-upload.js`** — create-page-only persistence and images.
- **`catalog/items/index/explore-scroll.js`** — explore strip scrolling.
- **`admin/catalog/section-item-selector.js`** — dependent **section → items** select (fetch, populate `<select>`, error UI, preserve selection on edit).
- **`admin/catalog/items/create-images-upload.js`**, **`edit-images-upload.js`** — admin image management.
- **`admin/collaborators/check-contact.js`** — contact field remote check.

### `bootstrap.js` (shared foundation)

- Still exposes **`window.bootstrap`** and **`window.$` / `window.jQuery`** after importing Bootstrap and jQuery.
- **Removed** the previous jQuery **`$.fn.modal`** shim around Bootstrap modals (modals are used via Bootstrap’s API / data attributes directly).
- Adds **`$.fn.modernTypeahead`**: debounced **`input`**, dropdown **`list-group`** next to the input, **`options.source(query, callback)`** for async results, Escape to close, and **`ensureTypeaheadGlobalDocumentClose`** — a **namespaced document click** handler so open typeahead dropdowns hide when clicking outside (guarded by **`window.__eMuseuTypeaheadDocCloseBound`** so it only binds once).

### `i18n.js`

- Picks locale from **`<html lang>`** (`pt*` → `pt_BR`, `en*` → `en`, else fallback **`pt_BR`**).
- Loads **`lang/js/en.json`** or **`lang/js/pt_BR.json`** via **dynamic `import()`** with **`await`** at module top level (ESM), then **`i18next.init`** with that bundle only.
- **`export default i18next`** for modules that call **`i18next.t()`** (e.g. admin delete confirmations).

### What was removed

- The entire **`resources/js/components/`** tree (per-feature files under **`warnings/`**, **`getTagsByCategory`**, **`itemCategoryItemSelector`**, **`img-modal`**, **`popOverButton`**, **`releaseLockOnLeave`**, **`checkContact`**, etc.) — behavior is either merged (**`admin-delete-confirm`**), moved under **`shared/`** or **`pages/`**, or superseded by **`section-item-selector`** + backend JSON.

---

## Blade / views

- **Admin layout** (`admin.blade.php`): Uses **`@vite`…`admin.js`**, and exposes a **`data-admin-dependent-select-error`** attribute for translated error messaging when dependent selects fail to load.
- **Removed** **`dependent-select-fetch.blade.php`**; dependent loading is handled in JS (`section-item-selector` + API).
- **Large inline scripts removed or reduced** on many admin and catalog pages (items create/edit, modals partials, upload partials, collaborators, taxonomy, extras, etc.) in favor of the Vite modules above.
- **Pagination**: Customized or overridden **Bootstrap 5** pagination view under **`resources/views/vendor/pagination/`**.
- **Catalog explore**: Inline **`scroll-script.blade.php`** removed; behavior lives in **`pages/catalog/items/index/explore-scroll.js`**.
- Minor cleanups on **`show.blade.php`**, explore **menu** partial, and other templates to match the new asset strategy.

---

## Internationalization

- **`lang/en/view/admin/layout.php`** and **`lang/pt_BR/view/admin/layout.php`**: New key **`dependent_select_load_failed`** for failed dependent-select AJAX loads.

---

## Tooling

- **`eslint.config.js`**: Declares common browser globals used by the new code (`fetch`, `FormData`, `URL`, `AbortController`, etc.) and drops the blanket **`event`** global.

---

## Static assets

- **Deleted** several images under **`public/img/`** (assistant PNGs, logo, placeholder, and uppercase **`tecno-lixo-*.JPG`**).
- **Untracked replacements**: **`tecno-lixo-2.jpg`**, **`tecno-lixo-4.jpg`**, **`tecno-lixo-5.jpg`** (lowercase extension) — likely a normalization or replacement of the removed JPGs.

---

## Net effect (high level)

- **Clear split** between **public** (`app.js`) and **admin** (`admin.js`) front-end bundles.
- **Feature-based and shared** JavaScript layout instead of a single **`components/`** dump.
- **Lazy loading** for the heavy **public item contribution** create page.
- **Backend alignment** for **components** on contributions (explicit component item id) and for **admin dependent selects** (dedicated JSON endpoint + service method).
- **Large reduction** of inline Blade JavaScript in favor of maintainable modules (~**60 files** touched in diff stat: roughly **+280 / −2031** lines in tracked changes, plus new untracked JS and vendor pagination).

```
- ** -db run param & vite fix:**

```md
### Behavior

- **`setup-hard`**, **`remove-all`**, and **`remove-all-files`** accept **`-db`**.
- Flags **`-y`**, **`-env`**, and **`-db`** can be passed in **any order** (for example: `sudo ./run setup-hard -y -db` or `sudo ./run setup-hard -db -y`).
- With **`-db`**, **`mysql_data` is not removed**; **`vendor`**, **`node_modules`**, **`public/hot`**, and **`public/build`** are still removed as before (when those steps run).

### Examples

sudo ./run setup-hard -y -db
sudo ./run setup-hard -db -y
sudo ./run remove-all -y -db
sudo ./run remove-all-files -y -db


### Warning text

When **`-db`** is set, the interactive warning for `setup-hard` / `remove-all` states that **`mysql_data` is kept**; without **`-db`**, the warning still describes a full wipe including the database volume.

### Documentation

- **`./run help`** lists **`-db`** and examples.
- **`README.md`** was updated with the same usage (Option 3 / utilities / quick reference / important notes).

---

## 2. Vite manifest error after `setup-hard` + `setup`

### Symptom

Laravel throws:

`ViteManifestNotFoundException` — `Vite manifest not found at: /var/www/public/build/manifest.json`

The error page suggests running `npm run dev` in development.

### Why it happened

1. **`remove-all` / `remove-all-files`** delete **`public/build`** (including `manifest.json`) and **`public/hot`**.
2. For **`APP_ENV=local`**, **`setup`** runs **`npm-local-bg`**, which starts the Vite dev server in Docker. Laravel’s `@vite` directive uses **`public/hot`** when the dev server is active; otherwise it falls back to **`public/build/manifest.json`**.
3. If the dev server has not started yet, or **`npm-local-bg`** only logs a warning and continues, **neither `hot` nor `manifest` may exist** when you load the app — hence the exception.

This is expected after a reset until assets are available; it is not specific to the **`-db`** flag.

### Fix in `run`

A function **`ensure-vite-assets-local`** was added and called from **`setup`** immediately after **`npm-local-bg`** (local environment only).

It:

1. Waits (polling) for **`public/hot`** or **`public/build/manifest.json`** to appear within a bounded time window.
2. If that times out, runs **`docker compose exec vite npm run build`** so **`manifest.json`** is generated (without using the same “remove hot + build” sequence as **`build-vite`**, which intentionally clears **`public/hot`** for a production-style build).

This makes the site usable right after **`setup`** even when Vite is slow to start or fails silently.

### Manual options

- **`./run build-vite`** — full production-style build (also removes `public/hot` before building, as intended for that command).
- **`./run start-vite-local`** — ensure the dev server is running if you rely on HMR and **`public/hot`**.

---

## 3. Files touched (reference)

| Area | Change |
|------|--------|
| `run` | `setup-hard` / `remove-all` / `remove-all-files`**`-db`** parsing and forwarding; **`ensure-vite-assets-local`**; **`help`** text |
| `README.md` | **`-db`** usage and **`-db`** quick reference |

---

## 4. Quick reference

| Need | Command |
|------|---------|
| Hard reset, keep DB volume | `sudo ./run setup-hard -y -db` |
| Full cleanup files, keep DB dir | `sudo ./run remove-all -y -db` |
| Only Vite production build | `./run build-vite` |
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **REFACTOR**

### ⏳ Time spent:
- **5 HOURS** (approximate)

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
