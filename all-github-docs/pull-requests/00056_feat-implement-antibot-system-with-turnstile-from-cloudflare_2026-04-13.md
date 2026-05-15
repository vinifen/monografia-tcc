---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 56
github_pull_request_id: 3520545062
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/56
state: closed
draft: False
author: vinifen
created_at: 2026-04-13T01:18:00Z
updated_at: 2026-04-13T01:19:09Z
merged_at: 2026-04-13T01:18:15Z
closed_at: 2026-04-13T01:18:15Z
head_ref: @vinifen/feat/55/antibot
base_ref: develop
title: "✨ feat: implement antibot system with turnstile from cloudflare"
---

# ✨ feat: implement antibot system with turnstile from cloudflare

# ✨ Implement antibot system with turnstile from cloudflare
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #55 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
### Configuration

- **`config/antibot.php`** — Driver (`null` | `turnstile`), default and alternate POST field names for Turnstile tokens, and Turnstile `site_key`, `secret_key`, and `verify_url`.
- **`.env.example`** — Documents `ANTIBOT_DRIVER`, `ANTIBOT_RESPONSE_INPUT`, `ANTIBOT_VERIFICATION_REQUEST_RESPONSE_INPUT`, `TURNSTILE_*`, and optional `TURNSTILE_VERIFY_URL`.
- **`phpunit.xml`** — Sets `ANTIBOT_DRIVER=null` so the verifier stays inactive in CI regardless of host env.

### Server-side verification

- **`App\Support\Security\AntiBotVerifier`** — When the driver is `turnstile` and both keys are non-empty, validates the token by POSTing to Cloudflare’s siteverify endpoint (with timeouts). Network failures or invalid responses throw a **`ValidationException`** with the `antibot` error key. If inactive, validation is a no-op and no site key is exposed to views.
- **`App\Http\Middleware\VerifyAntiBotChallenge`** — Registered as middleware alias **`antibot`**. Supports an optional scope:
  - **Default** — Uses `config('antibot.response_input')` (Turnstile default: `cf-turnstile-response`).
  - **`verification-request`** — Uses `config('antibot.verification_request_response_input')` so the catalog e-mail-code AJAX flow can use a **different** field name and avoid collisions with other widgets on the same page.

### Routing and CSRF

- **`routes/web.php`**
  - **`POST`** catalog collaborator verification code request uses **`throttle:collaborator-verification-email`** and **`antibot:verification-request`**.
  - Admin login **`POST`** uses **`throttle:admin-login`** and **`antibot`**.
- **`bootstrap/app.php`** — Registers the `antibot` alias and adds both configured Turnstile field names to **`dontFlash`** so failed challenges do not flash large tokens back into the session.

### Views and front-end

- **`resources/views/components/antibot/turnstile-widget.blade.php`** — Reusable Turnstile widget include.
- **Admin login** (`resources/views/pages/admin/auth/login.blade.php`) — Renders the widget when view data is present; shows `@error('antibot')`.
- **Catalog e-mail verification** — Partial includes the widget inside a **`.js-antibot-verification-request`** wrapper; item create / extra modal pass a translated **`data-msg-antibot-before-email-code`** for client-side gating.
- **`resources/js/pages/admin/auth/login-turnstile-reset.js`** — Resets the widget when login validation fails (loaded via **`resources/js/app.js`**).
- **`resources/js/pages/catalog/collaborators/email-verification-code.js`** — Blocks the AJAX “send code” action until Turnstile is completed; resets the widget in its container after requests.

### Service provider composition

- **`AppServiceProvider`** — Boot logic split into small **`App\Providers\Concerns\*`** traits, including:
  - **`RegistersAntiBotEmailCodeComposer`** — Passes Turnstile view data to the catalog e-mail verification partial.
  - **`RegistersAdminLoginAntiBotViewComposer`** — Same for the admin login view.

### Internationalization

- **`lang/en/antibot.php`** and **`lang/pt_BR/antibot.php`** — Strings for challenge failure and “complete challenge before e-mail” messaging.

### Tests

- **`tests/Feature/AntiBot/AntiBotChallengeTest.php`** — Covers disabled driver, missing token when Turnstile is “on”, successful path with mocked siteverify, and admin login session errors when the token is missing.
- **`tests/Feature/Admin/AdminLoginTest.php`** — Admin login behaviour with anti-bot considerations.
- **`tests/Feature/Catalog/CollaboratorEmailVerificationTest.php`** — Comment/assertions aligned so mail/session tests stay stable if CI sets Turnstile env vars.

### Deployment templates

- **`deploy-docs/coolify-production.env.example`** and **`deploy-docs/coolify-staging.env.example`** — Include `ANTIBOT_DRIVER=turnstile` and placeholders for `TURNSTILE_SITE_KEY` / `TURNSTILE_SECRET_KEY`.

### Minor related notes

- **`CatalogContributionReceivedMailService`** and **`CollaboratorController`** — Docblocks/comments tying behaviour to the anti-bot middleware where relevant.

---

## 2. Other changes present on this branch (vs `main`)

These commits are **on the same branch** but are not limited to Turnstile; they matter for a full picture of `main..HEAD`:

- **Deploy documentation layout** — Coolify env examples and MinIO-oriented Docker Compose samples moved or added under **`deploy-docs/`** (with corresponding removal from **`deploy/`** in earlier history).
- **HTTPS / app URL** — **`RegistersForcedHttpsUrls`** and related **`APP_FORCE_HTTPS`** handling (from merged develop/hotfix work).
- **S3 / public files** — **`config/filesystems.php`** and **`.env.example`** clarify that public files are served via **`APP_URL/storage`** (proxy), not direct `AWS_URL`; **`AWS_URL`** removed from the example env.

---

## 3. How to enable in production

1. Create a Turnstile site in Cloudflare and obtain **site key** and **secret key**.
2. Set **`ANTIBOT_DRIVER=turnstile`**, **`TURNSTILE_SITE_KEY`**, and **`TURNSTILE_SECRET_KEY`** (see **`.env.example`** and **`deploy-docs/*`**).
3. Ensure front-end domains match Turnstile host configuration in the Cloudflare dashboard.
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
