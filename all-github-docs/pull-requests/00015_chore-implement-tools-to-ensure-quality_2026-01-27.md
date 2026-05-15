---
repository: vinifen/e-museu-2.1.0-beta
github_pull_request_number: 15
github_pull_request_id: 3209015585
html_url: https://github.com/vinifen/e-museu-2.1.0-beta/pull/15
state: closed
draft: False
author: vinifen
created_at: 2026-01-26T00:38:46Z
updated_at: 2026-02-18T14:19:24Z
merged_at: 2026-01-27T21:08:58Z
closed_at: 2026-01-27T21:08:58Z
head_ref: @vinifen/chore/10/implement-code-quality-tools
base_ref: develop
title: "⚙️ chore: implement tools to ensure quality"
---

# ⚙️ chore: implement tools to ensure quality

# ⚙️ Implement tools to ensure quality
<!-- Put the emoji related to the type and use Title Case or Sentence case for the issue title -->

### Related Issue: #10 
<!-- Use: "Related Issue: N/A" if no issue -->

## 🔄 Change Overview

### ✨ Summary of changes:
<!-- Briefly describe what was done and why, preferably in bullet points -->

### PHPStan (v2.0) + Larastan (v3.0)
- **Packages**: `phpstan/phpstan` + `larastan/larastan`
- **Summary**: Static analysis tool for PHP that finds bugs and type errors. Larastan extends PHPStan with Laravel-specific rules and understanding. Configured at level 8.

### PHP Code Sniffer (v3.13.5)
- **Package**: `squizlabs/php_codesniffer` (via `dealerdirect/phpcodesniffer-composer-installer`)
- **Summary**: Enforces coding standards (PSR-12) and detects violations in PHP code. Configured with `phpcs.xml`.

### PHP Code Beautifier and Fixer
- **Package**: Part of `squizlabs/php_codesniffer`
- **Summary**: Automatically fixes PHP code style issues detected by PHPCS.

### Laravel Pint (v1.13)
- **Package**: `laravel/pint`
- **Summary**: Laravel's official, removes unused imports, Adds trailing commas in multiline structures.

## New PHP Tools Added

### PHP Insights (v2.13)
- **Package**: `nunomaduro/phpinsights`
- **Summary**: Aggregated PHP code quality analysis providing metrics for complexity, architecture, and best practices. Configured with Laravel preset.

### PHP Copy/Paste Detector (v8.2)
- **Package**: `systemsdk/phpcpd`
- **Summary**: Detects duplicated code in PHP files, helping identify refactoring opportunities and reduce code duplication.

### Churn PHP (v1.7)
- **Package**: `bmitch/churn-php`
- **Summary**: Analyzes PHP files to identify refactoring candidates based on change frequency and code complexity.

### PHPMD - PHP Mess Detector (v2.15)
- **Package**: `phpmd/phpmd`
- **Summary**: Detects code smells, design issues, and complexity problems. Configured with rules adjusted for Laravel conventions (facades, snake_case, etc.).

## JavaScript Tools Added

### ESLint (v9.39.2)
- **Package**: `eslint` + `@eslint/js` (v9.39.2)
- **Summary**: JavaScript linter that identifies errors, style issues, and problematic patterns. Configured with flat config and Prettier integration.

### ESLint Config Prettier (v10.1.8)
- **Package**: `eslint-config-prettier`
- **Summary**: Disables ESLint rules that conflict with Prettier, allowing seamless use together without conflicts.

### Prettier (v3.8.1)
- **Package**: `prettier`
- **Summary**: Automatic code formatter for JavaScript, SCSS, and JSON, ensuring style consistency across the project.

## Configuration Files

### Existing
- `phpcs.xml` - PHP Code Sniffer configuration (PSR-12)
- `phpstan.neon` - PHPStan configuration (Level 8)

### New
- `phpinsights.php` - PHP Insights configuration with Laravel preset
- `phpmd.xml` - PHPMD rules adjusted for Laravel (excludes false positives)
- `eslint.config.js` - ESLint configuration with flat config
- `.prettierrc.json` - Prettier configuration
- `.prettierignore` - Files ignored by Prettier
- `pint.json` - Pint config (added on https://github.com/e-museu-utfpr-gp/e-museu/pull/22)

## Updated `run` Script Commands

### Existing Commands
- `./run phpstan` - Runs PHPStan static analysis
- `./run phpcs` - Runs PHP Code Sniffer
- `./run phpcbf` - Runs PHP Code Beautifier and Fixer

### New Commands Added
- `./run phpinsights` - Runs PHP Insights
- `./run phpcpd` - Detects duplicated code
- `./run churn` - Analyzes refactoring candidates
- `./run phpmd` - Runs PHP Mess Detector
- `./run eslint` - Lints JavaScript
- `./run eslint-fix` - Automatically fixes ESLint issues
- `./run prettier` - Formats files
- `./run prettier-check` - Checks formatting without modifying files
- `./run pint` -  Removes unused imports, Adds trailing commas in multiline structures. (added on https://github.com/e-museu-utfpr-gp/e-museu/pull/22)
- `./run pint-test` - Check errors (added on https://github.com/e-museu-utfpr-gp/e-museu/pull/22)
### Fixed lint errors after included linters

### 🏷️ Type of change:
<!-- Select one or two that apply -->
- **CHORE**

### ⏳ Time spent:
- **6 HOURS** (approximate)

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
