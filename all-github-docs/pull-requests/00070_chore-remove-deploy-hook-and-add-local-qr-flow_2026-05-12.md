---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 70
github_pull_request_id: 3657478261
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/70
state: closed
draft: False
author: vinifen
created_at: 2026-05-10T14:19:49Z
updated_at: 2026-05-12T16:54:33Z
merged_at: 2026-05-12T16:54:32Z
closed_at: 2026-05-12T16:54:32Z
head_ref: @vinifen/chore/69/remove-deploy-finish-project
base_ref: develop
title: "⚙️ chore: remove deploy hook and add local qr flow"
---

# ⚙️ chore: remove deploy hook and add local qr flow

#  ⚙️ Remove deploy hook and add local qr flow

<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #69 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- drop deploy webhook, workflow, nginx /deploy, rate limiter, deploy config

- regenerate catalog qr via endroid + poster composition (gd, partner logos)

- wire admin/contribution flows to RegenerateItemQrCodeAction; item scope + sidebar

- refresh about/layout i18n, image modal, prd/sdd; add unit tests; add docs/github

```md
## High-level themes

1. **Deploy webhook and GitHub Actions deploy pipeline removed** — Coolify-focused docs and env templates trimmed; application no longer exposes `/deploy` or related configuration.
2. **QR code regeneration redesigned** — Moves from an external HTTP QR API to **local PNG generation** (`endroid/qr-code`), optional **printable poster composition** (GD + partner logos), and a dedicated action with clearer error handling.
3. **Public UI and content polish** — About page credits/contact structure, gallery image accessibility (`alt` strings), footer emails, and image modal refinements.
4. **Catalog public item view** — Item scope loads QR images where relevant; sidebar picks a sensible hero image when the primary URL is empty.
5. **Documentation and README** — Credits, upstream repository pointers, locale maintenance notes (including admin QR requirements), PRD/SDD updates.

---

## Deploy removal

| Area | Change |
|------|--------|
| **Routes** | `DeployWebhookController` import and deploy routes removed from `routes/web.php`. |
| **Controller** | `app/Http/Controllers/DeployWebhookController.php` deleted. |
| **Config** | `config/deploy.php` deleted. |
| **Env example** | `.env.example` — variables for Coolify deploy hook (`DEPLOY_HOOK_SECRET`, `COOLIFY_DEPLOY_*`) removed. |
| **CI** | `.github/workflows/deploy-coolify.yml` deleted. |
| **Nginx** | `docker/nginx/{production,staging,local_prod-local}/default.conf` — `location` blocks for `/deploy` removed. |
| **Rate limiting** | `app/Providers/Concerns/RegistersRateLimiters.php` — `deploy-hook` limiter removed. |
| **Staging Basic Auth** | `app/Http/Middleware/Auth/StagingBasicAuth.php` — `/deploy` path bypass removed (staging Basic Auth now applies consistently per middleware rules). |
| **Docs** | `docs/deploy-coolify/deploy-hook/doc.md` and `docs/deploy-coolify/github-actions-deploy.env.example` deleted; Coolify env example files and README deploy references adjusted accordingly. |
| **Tests** | `tests/Feature/DeployWebhookControllerTest.php` deleted; `StagingBasicAuthMiddlewareTest` updated for removed bypass behavior. |

---

## QR code regeneration (new architecture)

### New / untracked code

- **`app/Actions/Catalog/RegenerateItemQrCode/RegenerateItemQrCodeAction.php`** — Orchestrates: delete existing QR → resolve destination URL → generate PNG locally → compose printable poster → store `ItemImage` (`QRCODE`).
- **Traits under `app/Actions/Catalog/RegenerateItemQrCode/Concerns/`**  
  - `GeneratesQrCodePngLocally` — Local QR PNG via `endroid/qr-code`.  
  - `ComposesQrCodePoster` — Builds the final printable asset (GD, logos, layout).  
  - `StoresRegeneratedQrItemImage` — Persists to public disk and creates `ItemImage`.  
  - `UsesItemQrCodeService` — Shares URL/name helpers with the service layer.
- **`app/Exceptions/ItemQrRegenerateException.php`** — Typed exception with translation keys for admin-facing errors.

### Service layer

- **`app/Services/Catalog/ItemQrCodeService.php`** — **`regenerateForItem()` removed** (generation moved to the action). Adds **`pieceNameForQrPoster(Item $item)`**: resolves a display title with preference order **pt_BR → universal → other languages** (uses `ContentLanguage` and `Language::tryIdForCode`). Previous dependency on `Http`/`RuntimeException` for remote QR fetch is gone from this flow.

### Admin integration

- **`AdminItemQrCodeController`** — Calls `RegenerateItemQrCodeAction`; catches `ItemQrRegenerateException` and returns validation-style errors using translated keys.
- **`AdminItemController`**, **`UpdateAdminItemFromRequestAction`**, **`StoreItemContributionAction` / `PersistsContribution`** — All invoke **`RegenerateItemQrCodeAction::handle()`** instead of `ItemQrCodeService::regenerateForItem()` after create/update/contribution flows (best-effort `report()` where applicable).

### Dependencies

- **`composer.json` / `composer.lock`** — Adds **`endroid/qr-code` ^6**.

### Assets

- **Untracked** partner logos under `public/img/qrcode/` (`logo-unicentro-qrcode.png`, `logo-utfpr-qrcode.png`, `tecnolixo-logo-qrcode.png`) used by poster composition.

### Translations

- **`lang/en/app/catalog.php`** and **`lang/pt_BR/app/catalog.php`** — New strings for encode/compose failures (`qrcode_regenerate_failed_encode`, `qrcode_regenerate_failed_compose`), aligned with README guidance (GD + logos).

---

## Catalog model and public views

- **`app/Models/Catalog/Item.php`** — `scopeWithCatalogShowRelations` now includes **`ItemImageType::QRCODE`** in the eager-loaded `images` constraint so public pages can access QR rows when needed.
- **`resources/views/pages/catalog/items/_partials/show/item-details-sidebar.blade.php`** — Orders images by `sort_order`; if `$item->image_url` is empty, uses the first ordered image as the hero; thumbnail strip iterates the same ordered collection.

---

## Front end (About, layout, image modal)

- **About partials** (`intro`, `gallery`, `tecnolixo`, `elixo`) — Restructured for credits, dual contact emails, and per-image gallery `alt` keys driven from lang files.
- **`resources/views/components/layouts/app.blade.php`** — Footer/contact adjustments consistent with new translation keys.
- **`resources/views/components/ui/image-modal.blade.php`**, **`resources/js/shared/ui/img-modal.js`**, **`resources/sass/_image-modal.scss`**, **`resources/sass/custom.scss`** — Modal behavior and styling updates.

---

## Internationalization

- **`lang/*/view/about.php`** — Granular keys for credits blocks, repository links, contact intro/joiner/emails, section and gallery `alt` text (EN + pt_BR).
- **`lang/*/view/layout.php`** — Footer email keys for general and institutional addresses.

---

## Tests (new / modified)

### New (untracked)

- **`tests/Support/MinimalQrPng.php`** — Minimal PNG helper for unit tests.
- **`tests/Unit/Actions/Catalog/RegenerateItemQrCode/ComposesQrCodePosterTest.php`** — Poster composition tests.
- **`tests/Unit/Services/Catalog/ItemQrCodeServicePieceNameForPosterTest.php`** — `pieceNameForQrPoster` behavior.
- **`tests/Unit/Models/ContentLanguageMatchesLanguagesTableTest.php`** — Ensures every `ContentLanguage` enum case has a matching `languages.code` row (MySQL group); supports QR name resolution assumptions.

### Modified

- **`tests/Feature/Admin/Catalog/Item/AdminItemControllerTest.php`** — Adjusted for QR regeneration via action / behavior changes.
- **`tests/Feature/Middleware/StagingBasicAuthMiddlewareTest.php`** — Reflects removal of `/deploy` bypass.

---

## Product / engineering docs

- **`docs/prd.md`**, **`docs/sdd.md`** — Updated in line with current scope (details per diff).
- **`README.md`** — Credits and upstream pointers; deploy-doc links trimmed; notes on **GD**, **`endroid/qr-code`**, `public/img/qrcode/`, and locale strings for public UI.

---

## File checklist

### Modified (tracked)

`.env.example`, `README.md`,  
`app/Actions/Catalog/StoreItemContribution/Concerns/PersistsContribution.php`,  
`app/Actions/Catalog/StoreItemContribution/StoreItemContributionAction.php`,  
`app/Actions/Catalog/UpdateAdminItemFromRequestAction.php`,  
`app/Http/Controllers/Admin/Catalog/Item/AdminItemController.php`,  
`app/Http/Controllers/Admin/Catalog/Item/AdminItemQrCodeController.php`,  
`app/Http/Middleware/Auth/StagingBasicAuth.php`,  
`app/Models/Catalog/Item.php`,  
`app/Providers/Concerns/RegistersRateLimiters.php`,  
`app/Services/Catalog/ItemQrCodeService.php`,  
`composer.json`, `composer.lock`,  
`docker/nginx/local_prod-local/default.conf`,  
`docker/nginx/production/default.conf`,  
`docker/nginx/staging/default.conf`,  
`docs/deploy-coolify/coolify-production.env.example`,  
`docs/deploy-coolify/coolify-staging.env.example`,  
`docs/prd.md`, `docs/sdd.md`,  
`lang/en/app/catalog.php`, `lang/en/view/about.php`, `lang/en/view/layout.php`,  
`lang/pt_BR/app/catalog.php`, `lang/pt_BR/view/about.php`, `lang/pt_BR/view/layout.php`,  
`resources/js/shared/ui/img-modal.js`,  
`resources/sass/_image-modal.scss`, `resources/sass/custom.scss`,  
`resources/views/components/layouts/app.blade.php`,  
`resources/views/components/ui/image-modal.blade.php`,  
`resources/views/pages/about/_partials/*.blade.php`,  
`resources/views/pages/catalog/items/_partials/show/item-details-sidebar.blade.php`,  
`routes/web.php`,  
`tests/Feature/Admin/Catalog/Item/AdminItemControllerTest.php`,  
`tests/Feature/Middleware/StagingBasicAuthMiddlewareTest.php`.

### Deleted (tracked)

`.github/workflows/deploy-coolify.yml`,  
`app/Http/Controllers/DeployWebhookController.php`,  
`config/deploy.php`,  
`docs/deploy-coolify/deploy-hook/doc.md`,  
`docs/deploy-coolify/github-actions-deploy.env.example`,  
`tests/Feature/DeployWebhookControllerTest.php`.

### Untracked

`app/Actions/Catalog/RegenerateItemQrCode/` (full directory),  
`app/Exceptions/ItemQrRegenerateException.php`,  
`public/img/qrcode/*.png`,  
`tests/Support/MinimalQrPng.php`,  
`tests/Unit/Actions/Catalog/RegenerateItemQrCode/`,  
`tests/Unit/Models/ContentLanguageMatchesLanguagesTableTest.php`,  
`tests/Unit/Services/Catalog/ItemQrCodeServicePieceNameForPosterTest.php`.

---

## Operational notes

- Ensure **PHP GD** is enabled wherever QR regeneration runs (encode + poster composition).
- Deploy **`public/img/qrcode/`** logos with the app so poster composition does not fail at runtime.
- After merging, run **`composer install`** so `endroid/qr-code` is present on all environments.

```

- **🔖 release: version 2.0.0:**
```md
## QR code generation (catalog items)

### Problem

QR raster images for printable posters were fetched from a third-party HTTP API (`api.qrserver.com`), which added network dependency, latency, and operational risk.

### Change

- **Local encoding** via Composer package **`endroid/qr-code`** (GD-backed `PngWriter`), producing a **512×512** PNG with **margin 0**, **low** error correction, and **UTF-8** payload (the same public item URL as before).
- Removed the HTTP-based trait; orchestration still lives in `RegenerateItemQrCodeAction` with a new concern **`GeneratesQrCodePngLocally`**.
- **User-facing strings:** the old “external service” error key was replaced by **`qrcode_regenerate_failed_encode`** (English and Portuguese catalog lang files).
- **Tests:** feature tests no longer fake `api.qrserver.com`; they use **`Http::preventStrayRequests()`** where appropriate and drop the scenario that simulated an external HTTP 503 (no longer applicable).
- **Docs:** `README.md`, `docs/sdd.md`, and `docs/prd.md` were updated to describe local QR generation and to adjust risk notes (no third-party QR API).
- **PHPDoc:** `PersistsContribution` no longer refers to holding the transaction during “external HTTP”.

### Behaviour note

The **encoded URL and poster pipeline** (e.g. `ComposesQrCodePoster`) are unchanged in intent; pixel layout of the QR matrix may differ from the previous provider because the encoder library changed. Scanners should still read the same URL.

### Architecture note (namespace)

`RegenerateItemQrCode` remains under **`App\Actions\Catalog\…`**, not under `Admin`, because the same action runs after **public item contribution** success (`StoreItemContribution` / `PersistsContribution`) as well as from **admin** flows (manual regenerate, identification code change).

---

## Application logging

### Problem

The default `stack` channel used the **`single`** driver, appending indefinitely to `storage/logs/laravel.log`, which could grow without bound on disk.

### Change

- `config/logging.php`: **`stack`** now targets the **`daily`** channel instead of **`single`**.
- Retention is configurable with **`LOG_DAILY_DAYS`** (default **14**); Monolog removes dated log files older than that window during normal logging activity.
- `.env.example` documents `LOG_CHANNEL` and `LOG_DAILY_DAYS`.

### Operational notes

- New files follow the usual Laravel pattern (e.g. `storage/logs/laravel-YYYY-MM-DD.log`).
- A legacy monolithic `laravel.log` from the `single` driver is **not** deleted automatically; it can be removed or truncated manually once.
- For less volume in production, tune **`LOG_LEVEL`** (e.g. `error`) in addition to retention.

---

## Optional local setup reminder

After pulling dependencies, run **`composer install`** so **`endroid/qr-code`** (and its transitive packages) are present. The PHP **GD** extension is required for PNG output and for poster composition (unchanged requirement).

```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **CHORE**

### ⏳ Time spent:
- **4 HOURS** (approximate)

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
