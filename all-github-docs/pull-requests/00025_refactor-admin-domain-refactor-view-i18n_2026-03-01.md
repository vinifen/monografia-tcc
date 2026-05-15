---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 25
github_pull_request_id: 3322470190
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/25
state: closed
draft: False
author: vinifen
created_at: 2026-02-24T20:29:37Z
updated_at: 2026-03-13T21:01:37Z
merged_at: 2026-03-01T15:17:39Z
closed_at: 2026-03-01T15:17:39Z
head_ref: @vinifen/refactor/23/24/domains-i18n
base_ref: develop
title: "♻️ refactor: admin domain, refactor view & i18n"
---

# ♻️ refactor: admin domain, refactor view & i18n

# ♻️ Admin domain, refactor view & i18n
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #24 #23 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
## i18n changes overview

Branch: `@vinifen/refactor/23/24/domains-i18n`

This document focuses on what was actually changed in this branch, with emphasis on internationalization (i18n) for PHP (Laravel) and JavaScript, plus a few small build / tooling fixes.

### 1. Laravel language files

- **Locales**
  - Two main locales:
    - `lang/pt_BR` – Brazilian Portuguese.
    - `lang/en` – English.

- **Core Laravel files**
  - Reviewed and adjusted where needed:
    - `auth.php`, `pagination.php`, `passwords.php`, `validation.php`.
  - `validation.php` (both locales):
    - Added human‑friendly field names in `attributes` (items, sections, tags, extras, proprietaries, users, etc.).
    - Added custom keys used by Form Requests and closure rules (e.g. catalog‑specific messages).

- **App‑level domain messages**
  - Domain‑oriented messages used by controllers/services:
    - `lang/*/app.php`.
    - `lang/*/app/{auth.php, catalog.php, identity.php, proprietary.php, taxonomy.php}`.
  - Used mainly for success/flash messages like `__('app.catalog.component.created')` instead of hard‑coded strings.

- **View‑oriented files**
  - **Public views** (both locales):
    - `lang/*/view.php` – entry point for view translations.
    - `lang/*/view/layout.php` – public layout (navigation, footer).
    - `lang/*/view/about.php` – About page.
    - `lang/*/view/auth.php` – public auth pages (register / verify / reset etc.).
    - `lang/*/view/catalog.php` – public catalog, items, and public modals.
    - Other public pages: `home.php`, `identity.php`, `index.php`, `proprietary.php` where needed.
  - **Admin views** (both locales):
    - `lang/*/view/admin/layout.php` – admin layout navigation, titles, common labels.
    - `lang/*/view/admin/catalog.php` – all admin catalog sections (items, components, extras, sections, item‑tags).
    - `lang/*/view/admin/proprietary.php` – admin proprietary/collaborator screens.
    - `lang/*/view/admin/taxonomy.php` – admin categories and tags pages.
    - `lang/*/view/admin/auth.php` – admin login view texts.
    - `lang/*/view/admin/identity.php`, `index.php` – admin user lists and dashboard‑style pages.

### 2. Blade templates (PHP views)

- **Public layout and static pages**
  - `resources/views/layouts/app.blade.php`:
    - Header links, mobile toggle, and footer content moved to `view.layout.*`.
  - `resources/views/about.blade.php`:
    - Title, headings, paragraphs, project descriptions, calls‑to‑action, and alt texts use `view.about.*`.

- **Public catalog and modals**
  - `resources/views/catalog/items/*.blade.php`:
    - Index, show and create views now pull all visible texts from `view.catalog.items.*`.
  - Public modals:
    - `resources/views/catalog/items/create-modals/{component-modal,tag-modal,extra-modal}.blade.php`:
      - Labels, helper tooltips, buttons and inline `alert()` messages replaced by `view.catalog.items.create_modals.*` keys.
    - `resources/views/catalog/items/show-modals/extra-modal.blade.php`:
      - Uses `view.catalog.items.show_extra.*` for “extra information” UI.

- **Public auth views**
  - `resources/views/auth/{register,verify,passwords/confirm,passwords/email,passwords/reset}.blade.php`:
    - All UI strings now come from `view.auth.*` (titles, headings, labels, CTAs, help texts).

- **Admin sections (item categories)**
  - `resources/views/admin/catalog/sections/{create,edit,index,show}.blade.php`:
    - Fully translated via `view.admin.catalog.sections.*` (titles, forms, filters, tables, confirm texts).

- **Admin proprietaries**
  - `resources/views/admin/proprietary/proprietaries/{create,edit,index,show}.blade.php`:
    - All labels, table headers, filters, booleans (“Yes/No”), and detailed item info use `view.admin.proprietary.proprietaries.*`.

- **Admin taxonomy categories**
  - `resources/views/admin/taxonomy/categories/{create,edit,index,show}.blade.php`:
    - Uses `view.admin.taxonomy.categories.*` for headings, labels, filters, and tables.

- **Admin extras and item‑tags item cards**
  - `resources/views/admin/catalog/extras/show.blade.php`.
  - `resources/views/admin/catalog/item-tags/show.blade.php`.
  - Item details in these pages re‑use `view.admin.catalog.items.show.*` keys (id, name, description, history, detail, dates, validated, section, collaborator, timestamps, yes/no, view/edit).

- **Admin auth**
  - `resources/views/admin/auth/admin-login.blade.php`:
    - Login title, labels, remember‑me and submit button use `view.admin.auth.login.*`.

### 3. Form Requests & validation

- **Catalog Form Requests**
  - Under `app/Http/Requests/Catalog/*` (e.g. `SingleTagRequest`, `SingleComponentRequest`, `ItemTagRequest`, `StoreItemRequest`, `UpdateItemRequest`, `SingleExtraRequest`, `ComponentRequest`):
    - Removed most custom `messages()` arrays where the default Laravel messages (with `validation.php` attributes) are enough.
    - Closure‑based `$fail()` calls now use translation keys (e.g. `__('validation.catalog.item_component_different')`) instead of inlined Portuguese.

- **Proprietary & other Form Requests**
  - `app/Http/Requests/Proprietary/{ProprietaryRequest, NewProprietaryRequest}` and related requests:
    - Updated to depend on `validation.php` attributes and custom messages, reducing duplicated hard‑coded texts.

### 4. JavaScript i18n

- **Translation files**
  - New shared JS translation location:
    - `lang/js/en.json`
    - `lang/js/pt_BR.json`
  - Contains:
    - `warnings.*` – all browser confirmation messages for destructive actions (delete item, tag, extra, category, section, user, proprietary, component, contribution).
    - `assistant.*` – full dialogue tree texts for the virtual assistant:
      - Home, About, Create (contribution), Index (catalog listings), Show (item details).

- **i18next setup**
  - `resources/js/i18n.js`:
    - Imports `pt_BR` and `en` from `lang/js/*.json`.
    - Reads `document.documentElement.lang` to guess the current locale.
    - Initializes `i18next` with:
      - `lng` = detected locale.
      - `fallbackLng` = `pt_BR`.

- **Warning components**
  - `resources/js/components/warnings/*.js`:
    - Now import `i18next` and call `confirm(i18next.t('warnings.some_key'))`.
    - Still support overriding via `data-confirm-message` on the trigger elements (Blade).

- **Assistant dialogues**
  - Dialogue definitions:
    - `resources/js/components/assistant-dialogues/{homeDialogue,aboutDialogue,createDialogue,indexDialogue,showDialogue}.js`.
    - Each exports `get*Dialogues(t)`, using the provided `t` (usually `i18next.t.bind(i18next)`) for all `text` and option labels.
  - Dialogue handler:
    - `resources/js/components/assistentDialogueHandler.js`:
      - Picks the correct dialogue factory based on the current route.
      - Injects `i18next`’s `t` function.
      - Uses `assistant.goodbye` key for the exit sentence.

- **Other JS tweaks**
  - `resources/js/components/releaseLockOnLeave.js`:
    - Added `/* global FormData, fetch */` to fix ESLint `no-undef` warnings for browser APIs.
  - `resources/js/app.js`:
    - Imports `./i18n` so translations are ready before other modules use `i18next`.

### 5. Docker & build pipeline

- **Dockerfiles**
  - `Dockerfile.production`, `Dockerfile.staging`, `Dockerfile.prod-local`:
    - Node `node-build` stage now copies:
      - `resources/`
      - `public/`
      - `lang/js/`
      - `vite.config.js`
    - This makes the JS translation files available to Vite inside the container and fixes previous `Could not resolve "../../lang/.../js.json"` build errors.

- **Node / NPM**
  - `package.json`:
    - Added `"i18next"` to `dependencies` to support frontend i18n.

### 6. Cleanup and consistency

- Removed older or unused language files that were superseded by the new `view.*` / `app.*` structure (for example, legacy `view/shared.php` and earlier `js` JSON locations).
- Updated selected controllers and redirects to:
  - Use the new `app.*` translation keys for success messages.
  - Stop using hard‑coded Portuguese strings in favour of translatable messages.

---

In summary, this branch makes the application bilingual (pt_BR / en) across:
- Laravel views (public + admin).
- Validation and Form Requests.
- Frontend JavaScript (confirmation dialogs + assistant).
- Docker/Node build so JS translations are always present during `npm run build`.

```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **REFACTOR**

### ⏳ Time spent:
- **7 HOURS** (approximate)

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
