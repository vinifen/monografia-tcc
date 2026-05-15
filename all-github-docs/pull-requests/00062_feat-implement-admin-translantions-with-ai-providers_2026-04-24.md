---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 62
github_pull_request_id: 3564765099
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/62
state: closed
draft: False
author: vinifen
created_at: 2026-04-22T01:22:06Z
updated_at: 2026-04-24T22:07:20Z
merged_at: 2026-04-24T22:06:19Z
closed_at: 2026-04-24T22:06:19Z
head_ref: @vinifen/feat/61/translation-with-ai
base_ref: develop
title: "✨ feat: implement admin translantions with ai providers"
---

# ✨ feat: implement admin translantions with ai providers

# ✨ Implement admin translantions with ai providers
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #61 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
```md
## 1. Executive summary

This branch delivers **AI-assisted translation in the admin panel** for catalog and taxonomy entities that already use per-locale translation tabs. Administrators can translate form fields toward a target locale using **OpenAI-compatible chat completions**, with **multiple providers** (Groq, OpenRouter, GitHub Models), **configurable failover order**, optional **manual provider selection**, rate limiting, structured logging, and broad automated test coverage.

A follow-up commit on the same branch **refactors** the first implementation: dedicated per-provider HTTP client classes are replaced by a **single generic HTTP client** and **environment-driven provider blocks** in `config/ai.php`, making it easier to add or reorder providers without new PHP classes.

Relative to `origin/main`, the branch is **nine commits ahead** and touches a large surface area (hundreds of files), because it also incorporates **Laravel 13**, **Turnstile antibot**, expanded **tests**, and related hotfixes merged from the development line—not only the AI translation feature.

---

## 2. What changed vs `origin/main` (high level)

| Area | Summary |
|------|---------|
| **Admin AI translation** | New `POST /admin/ai/translate-content` endpoint, registry of translatable resources/fields, prompts, JSON decoding of model output, UI on translation tabs (jQuery), EN/PT strings, SCSS for loading/disclaimer states. |
| **Providers & HTTP** | `config/ai.php` defines provider blocks (URL, keys, timeouts, models, temperature, optional headers, human labels). `AI_CHAT_COMPLETION_CHAIN` controls Auto mode order. `AiChatCompletionHttpClient` performs requests; `AdminChatCompletionAction` walks the chain or a forced provider. |
| **Safety & ops** | Per-admin throttle `admin-ai-translate` (default 3/min from `AI_RATE_LIMIT_PER_MINUTE`), max source size `AI_TRANSLATION_MAX_SOURCE_CHARS`, 503 when AI is disabled or not configured, 422 for user-facing translation errors and unavailable forced provider. |
| **Documentation** | `docs/sdd.md` and `docs/prd.md` updated; `.env.example` and Coolify env examples extended with AI variables. |
| **Tests** | Feature tests for the controller; unit tests for HTTP client, chain resolution, provider catalog/labels, JSON decoder, etc. |
| **Bundled with branch** | Laravel 13 upgrade, Cloudflare Turnstile antibot, collaborator/catalog test suites and related changes—review separately if merging only the AI slice. |

---

## 3. Feature review: admin AI translation (#61)

### 3.1 User flow

- Authenticated admins see AI actions on **translation tabs** for: items, extras, item categories, tags, and tag categories (partials wired from each resource’s `translation-tabs` blade).
- The layout exposes `data-admin-ai-translate-url` when at least one provider is **ready** (enabled, non-empty API credential where required, and at least one model).
- JavaScript (`resources/js/pages/admin/ai/admin-content-translation.js`) collects the current tab’s translatable fields, supports modes such as filling empty targets vs overwriting, optional **provider dropdown** (Auto vs a configured slug), shows progress and a disclaimer with **provider label + model** returned by the API.

### 3.2 Backend contract

- **Route:** `admin.ai.translate-content` → `AdminContentTranslationController::translate`, middleware `throttle:admin-ai-translate`.
- **Request validation:** `AdminContentTranslationRequest` — resource key, target locale, mode, optional provider, translations payload bounded by `AdminContentTranslationRegistry` field specs and `Language` rules.
- **Response (success):** JSON with `translations`, `provider`, `provider_label`, `model`, `requested_provider`.
- **Errors:** `AiTranslationUserException` → 422 with translated `message`; other throwables → 500 with generic internal error; blocked endpoint → 503.

### 3.3 Core types (maintainability)

| Component | Role |
|-----------|------|
| `AdminContentTranslationRegistry` | Single source of truth for which **resources** and **fields** exist, with max lengths and short descriptions for prompts. |
| `AdminContentTranslationPrompts` | System/user prompt construction for the model. |
| `AdminChatCompletionAction` | Orchestrates `handle()` / `translateContent()` using `TriesAdminChatCompletionProviders` and `TranslatesAdminContent`. |
| `AdminAi`, `AdminAiChatCompletionChain`, `AdminAiProviderCatalog` | Config-derived chain order, readiness, labels (`human_label` from env), and catalog of slugs. |
| `AdminChatCompletionHttpRequestFactory` | Builds typed `ChatCompletionHttpRequest` DTOs per provider slug from `config/ai.php`. |
| `AiChatCompletionHttpClient` | Shared OpenAI-compatible POST + response handling. |
| `ModelJsonContentDecoder` | Parses model JSON (including fenced code blocks) into field-keyed translations. |
| `AdminContentTranslationHttp` | Centralized JSON guard responses and structured `Log::info` for success/user_error/provider_error. |

This separation keeps the controller thin and makes provider behavior testable in isolation.

### 3.4 Provider chain and “forced provider”

- **Auto:** Iterates `AdminAi::chatCompletionChainSlugs()`; the **first** chain entry may receive UI-selected models where applicable; later steps use configured models only. Recoverable failures can accumulate until the chain is exhausted, then a composed user exception is thrown.
- **Forced:** User picks a slug; if that provider is not **ready**, the controller returns 422 before calling the model. If ready, only that provider is called; failures map to a clear “selected provider failed” style message.

### 3.5 Security and abuse

- Throttle keyed by **admin user id** (fallback IP), separate from the general `web-admin` bucket.
- Large payloads are capped by `ai.translation.max_source_chars` (documented as UTF-8 byte length).
- API keys stay server-side; the browser only receives provider **slug**, **label**, and **model** after a successful call.

---

## 4. Evolution across the two feature commits

1. **`46e3b40` — “implement admin translations with ai providers”**  
   Introduced the end-to-end feature: separate `Groq` / `OpenRouter` / `GitHubModels` client classes, fallback traits, controller, registry, prompts, views, JS, config, tests, and env examples.

2. **`9fd2e37` — “implement multiple ia providers support from env”**  
   Consolidates HTTP into `AiChatCompletionHttpClient`, moves request construction to `AdminChatCompletionHttpRequestFactory`, adds `AdminAiChatCompletionChain`, refines `AdminAi` and prompts, enhances the **admin UI** (e.g. provider selection and disclaimer metadata), expands controller/feature tests, and removes the three dedicated client classes in favor of **data-driven** provider blocks.

Net effect: **same product behavior**, cleaner extension path for new providers.

---

## 5. Testing

- **Feature:** `AdminContentTranslationControllerTest` covers happy paths, validation, blocking when not configured, forced provider behavior, rate limiting interaction, and error paths.
- **Unit:** `AiChatCompletionHttpClientTest`, `AdminAiChatCompletionChainTest`, `AdminAiProviderCatalogTest`, `AdminAiProviderLabelTest`, `ModelJsonContentDecoderTest`, and related support tests.

The suite aligns with the new HTTP stack and chain resolution logic.

---

## 6. Documentation and configuration

- **`docs/sdd.md`** documents the endpoint, config keys, main classes, and UI data attributes (including note that UI labels use `human_label` from env).
- **`.env.example`** lists `AI_*`, per-provider keys, URLs, timeouts, models, and optional headers (e.g. OpenRouter referer/title, GitHub API version).
- **Deploy examples** under `docs/deploy/` mention AI-related variables for staging/production.

---

## 7. Review notes (risks and suggestions)

| Topic | Note |
|-------|------|
| **Merge scope** | Merging this branch into `main` brings Laravel 13, Turnstile, and large test additions—not only AI. Plan merge/rebase strategy accordingly. |
| **Operational** | Provider availability and quotas depend on third parties; chain order and `*_ENABLED` flags are the main levers for graceful degradation. |
| **Typo in commit message** | `46e3b40` subject says “tranlantions”; no functional impact. |
| **Model output** | Translation quality and JSON adherence vary by model; `ModelJsonContentDecoder` and user-facing exceptions mitigate malformed output. |
| **jQuery** | Front-end follows existing admin stack (`admin.js`); consistent with the codebase. |

---

## 8. Conclusion

The branch successfully implements **ticket #61**: configurable, multi-provider **AI translation assist** for admin catalog/taxonomy content, with solid separation of concerns, throttling, logging, i18n, and tests. The second commit improves **maintainability** by generalizing HTTP and provider configuration. Reviewers should treat the **full diff vs `main`** as a combination of **platform upgrades** and **this feature**, and validate deployment env vars and provider keys before enabling in production.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **FEAT**

### ⏳ Time spent:
- **16 HOURS** (approximate)

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
