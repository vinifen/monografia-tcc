# Database model — v1 (Tankensho)

ER diagram from Laravel migrations in `e-museu-tankensho-primeira-versao-feita/database/migrations/`.

`created_at` and `updated_at` exist on most domain tables but are omitted here for readability.

```mermaid
erDiagram
    PROPRIETARIES {
        bigint id PK
        string full_name
        string contact
        bool blocked
        bool is_admin
    }

    USERS {
        bigint id PK
        string username
        string password
        bool is_admin
    }

    PASSWORD_RESETS {
        string email
        string token
        timestamp created_at
    }

    FAILED_JOBS {
        bigint id PK
        string uuid UK
        text connection
        text queue
        longtext payload
        longtext exception
        timestamp failed_at
    }

    SECTIONS {
        bigint id PK
        string name
    }

    CATEGORIES {
        bigint id PK
        string name
    }

    ITEMS {
        bigint id PK
        string name
        text description
        text history
        text detail
        date date
        string identification_code
        string image
        bool validation
        bigint section_id FK
        bigint proprietary_id FK
    }

    TAGS {
        bigint id PK
        text name
        bool validation
        bigint category_id FK
    }

    TAG_ITEM {
        bigint id PK
        bigint tag_id FK
        bigint item_id FK
        bool validation
    }

    EXTRAS {
        bigint id PK
        text info
        bigint item_id FK
        bigint proprietary_id FK
        bool validation
    }

    ITEM_COMPONENT {
        bigint id PK
        bigint item_id FK
        bigint component_id FK
        bool validation
    }

    SESSIONS {
        string id PK
        bigint user_id FK
        string ip_address
        text user_agent
        longtext payload
        int last_activity
    }

    LOCKS {
        bigint id PK
        string lockable_type
        bigint lockable_id
        bigint user_id FK
        timestamp expiry_date
    }

    SECTIONS ||--o{ ITEMS : has
    PROPRIETARIES ||--o{ ITEMS : owns
    PROPRIETARIES ||--o{ EXTRAS : owns
    CATEGORIES ||--o{ TAGS : groups
    ITEMS ||--o{ TAG_ITEM : tagged
    TAGS ||--o{ TAG_ITEM : tags
    ITEMS ||--o{ EXTRAS : has
    ITEMS ||--o{ ITEM_COMPONENT : parent
    ITEMS ||--o{ ITEM_COMPONENT : component
    USERS ||--o{ LOCKS : owns
```

## Notes

- `locks` uses a polymorphic relation (`lockable_type`, `lockable_id`).
- `item_component` is a self-relation on `items` (`item_id` → `component_id`).
- `password_resets`, `failed_jobs`, and `sessions` are Laravel infrastructure; no FK lines to domain tables except `sessions.user_id` → `users` (nullable index in migration).
