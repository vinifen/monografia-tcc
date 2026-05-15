# E-Museu — Wiki

> Digital museum platform to preserve and showcase collections tied to **electronic waste reuse** projects (UTFPR, Unicentro, and the broader community).  
> **Application version:** `2.0.0` (see the [`VERSION`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/VERSION) file in the repository).

This page is the **wiki home**: use it as an index. Product and technical depth stay in the repo under `README.md` and `docs/`.

---

## Purpose of this wiki

Gather **team processes**, a short glossary, and pages that do not fit cleanly in code — while keeping the [main repository](https://github.com/e-museu-utfpr-gp/e-museu) the source of truth for architecture and file-level versioning.

---

## Quick links (repository)

| Topic | Where |
|-------|--------|
| Local setup, Docker, `./run` | [`README.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/README.md) |
| Product requirements (scope, personas) | [`docs/prd.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/prd.md) |
| Technical design, operations, risks | [`docs/sdd.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/sdd.md) |
| Release notes (e.g. 2.0.0) | [`docs/releases/2.0.0.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/releases/2.0.0.md) |
| Data model | [`docs/database/database-model.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/database/database-model.md) |
| Deploy / Coolify / example env | [`docs/deploy-coolify/`](https://github.com/e-museu-utfpr-gp/e-museu/tree/main/docs/deploy-coolify) |
| Git branch rules | [`docs/github/branches.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/github/branches.md) |
| Commit convention | [`docs/github/commits.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/github/commits.md) |
| Storage (S3, public files) | [`docs/storage/doc.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/storage/doc.md) |

*(If your fork or org uses another URL, replace `e-museu-utfpr-gp/e-museu` in the links above.)*

---

## What the system does (summary)

- **Public:** catalog with filters, search, and sorting; item detail; institutional *About* page.
- **Public contribution:** submit a new item (metadata, images, relations) and *extras* on existing items; collaborator email verification is **optional** (`MAIL_PUBLIC_CONTRIBUTION_EMAIL_VERIFICATION_ENABLED`).
- **Curation / admin:** CRUD for items, categories, tags, extras, components, and relations; content validation; image and **QR code** management (local generation with GD + PHP library; printable poster).
- **Admin-assisted translation:** optional, via a provider chain in `config/ai.php` / `.env`.
- **Multi-locale:** content and fallback between locales (e.g. `pt_BR`, `en`); UI strings under `lang/`.

Important business rule: the public **only sees validated items** (`validation`).

---

## Main stack

- **Backend:** Laravel (PHP), Blade, Sanctum where applicable.
- **Data:** MySQL 8, Redis.
- **Frontend tooling:** Vite, modular JavaScript, Sass, Bootstrap.
- **Local environment:** Docker / Docker Compose; `./run` script (see `README.md`).

---

## First steps for developers

1. Clone the repository and follow the **Quick Start** in [`README.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/README.md).
2. Copy variables from [`.env.example`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/.env.example).
3. Run `./run setup` (or the README flow for your `APP_ENV`).
4. Before a PR: run tests and quality checks as documented in the README / SDD (`./run test`, PHPStan, etc.).

---

## Operations and releases

- **Deploy:** platform-driven (e.g. Coolify); example variables under `docs/deploy-coolify/`. The application codebase **does not** expose deploy webhooks.
- **Branches:** `main` (production) and `develop` flow; conventions in [`docs/github/branches.md`](https://github.com/e-museu-utfpr-gp/e-museu/blob/main/docs/github/branches.md).

---

## Software credits

- **2024 — first version:** Alexandre Takeshi Ogassahara — [tankesho/e-museu](https://github.com/tankesho/e-museu).
- **2026 — continued development / current upstream:** Vinicius Ferreira Novacoski and group — [e-museu-utfpr-gp/e-museu](https://github.com/e-museu-utfpr-gp/e-museu).

*(Aligned with the README and the app About page.)*

---

## Suggested wiki subpages

Add subpages as the team needs, for example:

- **Onboarding** — accounts, staging access, who to contact.
- **Glossary** — domain terms (item, extra, component, validation, collaborator).
- **Release checklist** — manual post-deploy steps, smoke tests.
- **Incidents** — how to report downtime or regressions.

On GitHub Wiki you can link internal pages with `[[Page-Name]]` from this Home.

---

## Maintenance

When product or workflow change in a meaningful way, update together:

1. This wiki (processes and links).
2. `docs/prd.md` and `docs/sdd.md` in the repository (per SDD rules).
3. `README.md` if setup, feature flags, or troubleshooting are affected.

---

*Last review of this wiki home: aligned with repository version **2.0.0**.*
