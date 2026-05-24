# Diff banco v1 (Tankensho) → v2

Fonte: `database/migrations/` em cada projeto.

## Tabelas removidas (só na v1)

- `proprietaries`
- `users`
- `password_resets`
- `failed_jobs`
- `sections`
- `categories`
- `tag_item`
- `sessions`

## Tabelas adicionadas (só na v2)

- `languages`
- `admins`
- `collaborators`
- `locations`
- `item_categories`
- `item_category_translations`
- `tag_categories`
- `tag_category_translations`
- `item_translations`
- `item_images`
- `tag_translations`
- `extra_translations`

## Renomeações (tabela ou conteúdo mudou de sítio)

| v1 | v2 |
|----|-----|
| `users` | `admins` |
| `proprietaries` | `collaborators` |
| `sections` | `locations` |
| `categories` | `tag_categories` + `tag_category_translations` |
| — | `item_categories` + `item_category_translations` (novo) |
| `tag_item` | `item_tag` |

---

## Colunas removidas

### `items`

- `name`
- `description`
- `history`
- `detail`
- `image`
- `section_id`
- `proprietary_id`

### `tags`

- `name`
- `category_id`

### `extras`

- `info`
- `proprietary_id`

### `locks`

- `user_id`

---

## Colunas adicionadas

### `items`

- `category_id`
- `collaborator_id`
- `location_id`

### `tags`

- `tag_category_id`

### `extras`

- `collaborator_id`

### `locks`

- `admin_id`

---

## Colunas que mudaram (mesmo nome, regra diferente)

### `items`

- `date` — obrigatório na v1 → nullable na v2

### `extras`

- `item_id` — obrigatório + cascade na v1 → nullable + `nullOnDelete` na v2

### `item_tag` (era `tag_item`)

- `tag_id` — obrigatório + cascade → nullable + `nullOnDelete`
- `item_id` — obrigatório + cascade → nullable + `nullOnDelete`

### `item_component`

- `item_id` — obrigatório + cascade → nullable + `nullOnDelete`
- `component_id` — obrigatório + cascade → nullable + `nullOnDelete`

---

## Conteúdo que saiu de uma coluna e foi para outra tabela

| Deixou de existir em | Passou para |
|---------------------|-------------|
| `items.name`, `description`, `history`, `detail` | `item_translations` |
| `items.image` | `item_images` |
| `tags.name` | `tag_translations` |
| `extras.info` | `extra_translations` |
| `categories.name` (tags) | `tag_category_translations` |
| — | `item_category_translations` (categorias de item, novo) |
