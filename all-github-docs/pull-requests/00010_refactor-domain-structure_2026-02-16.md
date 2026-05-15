---
repository: e-museu-utfpr-gp/e-museu
github_pull_request_number: 10
github_pull_request_id: 3287702516
html_url: https://github.com/e-museu-utfpr-gp/e-museu/pull/10
state: closed
draft: False
author: vinifen
created_at: 2026-02-15T23:00:12Z
updated_at: 2026-02-16T14:28:56Z
merged_at: 2026-02-16T00:47:48Z
closed_at: 2026-02-16T00:47:48Z
head_ref: @vinifen/refactor/9/domains-structure
base_ref: develop
title: "♻️ refactor: domain structure"
---

# ♻️ refactor: domain structure

# ♻️ Domain Structure
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #9 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->
- **Models:**
```md
# Domain models refactor – summary

## What was done

- **Models:** Updated all 10 models to domain namespaces (`App\Models\Catalog`, `Taxonomy`, `Proprietary`, `Identity`) and fixed cross-references.
- **App:** Updated config, controllers, middleware, services, requests, and console command to use the new model classes.
- **Database:** Updated seeders and factories (imports and docblocks).
- **Factory resolution:** In `AppServiceProvider`, registered `guessFactoryNamesUsing` and `guessModelNamesUsing` so Laravel finds the right factory for each model and the right model for each factory.
- **Config & PHPMD:** Added `config/factory_model_map.php` and `config/lockable_routes.php`; `AppServiceProvider` and `CheckLock` read from config to reduce coupling (CBO).

---

## Problems and solutions

| Problem | Solution |
|--------|----------|
| **Seed fails: "Class App\Proprietary not found"** | Laravel inferred the wrong model from the factory name. Registered `guessModelNamesUsing` with a factory→model map (from config) so each factory resolves to the correct model class. |
| **Wrong factory path for models in subnamespaces** | Default resolution expected e.g. `Database\Factories\Catalog\ItemFactory`. Registered `guessFactoryNamesUsing` with a model→factory map so models point to the existing factories in `Database\Factories\`. |
| **PHPMD: CouplingBetweenObjects in CheckLock and AppServiceProvider** | Moved route→model and model→factory mappings to config files so both classes depend on config instead of many model/factory classes directly. |
```

- **Controllers:**
```md
# Controllers by domain

## What was done

- **Namespaces:** Controllers that were moved into domain subfolders (Catalog, Taxonomy, Proprietary, Identity) had their namespace updated to match the folder: `App\Http\Controllers\Catalog`, `App\Http\Controllers\Taxonomy`, `App\Http\Controllers\Proprietary`, `App\Http\Controllers\Identity`.
- **Base controller and traits:** Each of those controllers extends `AdminBaseController` or `Controller`, which remain in `App\Http\Controllers`. The moved controllers import them explicitly (`use App\Http\Controllers\AdminBaseController` or `use App\Http\Controllers\Controller`). Controllers that use `BuildsAdminIndexQuery` keep `use App\Http\Controllers\Concerns\BuildsAdminIndexQuery`.
- **Routes:** In `routes/web.php`, the `use` statements at the top were updated so that every admin and catalog controller is referenced by its new FQCN (e.g. `App\Http\Controllers\Catalog\AdminItemController`, `App\Http\Controllers\Taxonomy\AdminTagController`, `App\Http\Controllers\Proprietary\AdminProprietaryController`, `App\Http\Controllers\Identity\AdminUserController`). Route definitions (e.g. `Route::resource('admin/items', AdminItemController::class)`) were left as-is; only the imports changed so that the class names resolve correctly.

**Controllers by domain:**

| Folder      | Controllers |
|------------|-------------|
| Catalog    | ItemController, AdminItemController, AdminSectionController, AdminExtraController, AdminComponentController, AdminItemTagController, QueryController |
| Taxonomy   | AdminCategoryController, AdminTagController |
| Proprietary| AdminProprietaryController |
| Identity   | AdminUserController |

Auth controllers remain under `App\Http\Controllers\Auth` and were not changed.

---

## Problems and solutions

| Problem | Solution |
|--------|----------|
| **PSR-4 / autoload:** Files under `Http/Controllers/Catalog/` (etc.) still had `namespace App\Http\Controllers`, so the autoloader would not resolve them correctly from the new paths. | Set each controller’s namespace to match its directory (e.g. `App\Http\Controllers\Catalog` for files in `Catalog/`). |
| **Missing base class in scope:** With the new namespace, `AdminBaseController` and `Controller` are in a different namespace, so `extends AdminBaseController` would not resolve. | Added explicit `use App\Http\Controllers\AdminBaseController` or `use App\Http\Controllers\Controller` at the top of each moved controller. |
| **Routes still pointing to old class names:** `web.php` was still importing e.g. `App\Http\Controllers\AdminItemController`, which no longer exists. | Updated all controller imports in `routes/web.php` to the new FQCNs (Catalog, Taxonomy, Proprietary, Identity). No changes were needed in config or bootstrap. |
| **Admin user controller under wrong domain:** The admin user controller was initially under **Users** (resource-oriented). The domain for admin identity and concurrency is **Identity** (User, Lock). | Moved the controller to `Identity/AdminUserController.php`, set `namespace App\Http\Controllers\Identity`, updated the request import to `App\Http\Requests\Identity\UserRequest`, and updated the route import in `web.php` to `App\Http\Controllers\Identity\AdminUserController`. |

```

- **Requests:**
```md
# Requests by domain – refactor summary

## What was done

- Set namespace in all 15 Request files to match their folder: `App\Http\Requests\Catalog`, `Taxonomy`, `Proprietary`, `Identity`.
- In `ItemContributionValidator` (Catalog), added `use` for `ProprietaryRequest` and `TagRequest` (other domains). Updated all controller imports to the new Request FQCNs.

**By domain:** Catalog (10), Taxonomy (2), Proprietary (2), Identity (1).

## Problems and solutions

- **PSR-4:** Namespaces updated so autoload resolves Requests from subfolders.
- **ItemContributionValidator:** Uses ProprietaryRequest and TagRequest; added explicit `use` for both.
- **Controllers:** Imports changed from `App\Http\Requests\*` to `App\Http\Requests\{Catalog|Taxonomy|Proprietary|Identity}\*`.
```

- **Services, Rules, Middlewares & Console:**
```md
# Services, Rules, Middleware, Console by domain – refactor summary

## What was done

- **Services:** `ItemContributionService` and `ItemIndexQueryBuilder` were in `app/Services/`; namespaces set to `App\Services\Catalog`. Controller `ItemController` updated to use `App\Services\Catalog\*`.
- **Rules:** `DifferentIds` was in `app/Rules/`; namespace set to `App\Rules\Catalog`. Requests `ItemTagRequest` and `SingleComponentRequest` updated to use `App\Rules\Catalog\DifferentIds`.
- **Middleware:** Domain middlewares moved to subfolders; namespaces set to `App\Http\Middleware\Catalog` (ValidateItem), `Proprietary` (ValidateProprietary), `Identity` (CheckLock), `Auth` (Authenticate, RedirectIfAuthenticated). Aliases in `bootstrap/app.php` and `app/Http/Kernel.php` updated to these FQCNs. All admin controllers that use `CheckLock` updated to `use App\Http\Middleware\Identity\CheckLock`.
- **Console:** `CreateAdmin` was in `app/Console/Commands/`; namespace set to `App\Console\Commands\Identity`. `bootstrap/app.php` and `app/Http/Kernel.php` updated in `withCommands` / `$commands` to `\App\Console\Commands\Identity\CreateAdmin::class`.

**By area:** Services Catalog (2); Rules Catalog (1); Middleware Catalog (1), Proprietary (1), Identity (1), Auth (2); Console Identity (1).

## Problems and solutions

- **PSR-4:** Namespaces updated so autoload resolves from the new paths (Services/Catalog, Rules/Catalog, Middleware subfolders, Console/Commands/Identity).
- **Bootstrap and Kernel:** Middleware aliases (`auth`, `guest`, `validate.item`, `validate.proprietary`, `check.lock`) and the CreateAdmin command now point to the new class names.
- **Consumers:** ItemController (Services), ItemTagRequest and SingleComponentRequest (Rules), and all controllers that use CheckLock (Middleware) updated to the new imports.
```

-**Database:**
```md
# Summary: database by domain

**Seeders** and **factories** in subfolders by domain (Catalog, Taxonomy, Proprietary), with namespaces `Database\Seeders\*` and `Database\Factories\*`. **DatabaseSeeder** uses FQCN when calling seeders. **Extra** lives under Catalog (not Taxonomy). **Migrations** unchanged. **config/factory_model_map.php** updated with the new factory paths.

**Structure:** `seeders/{Catalog,Taxonomy,Proprietary}/*.php` and `factories/{Catalog,Taxonomy,Proprietary}/*.php`.
```

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **REFACTOR**

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
