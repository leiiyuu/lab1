```mermaid
erDiagram
    CLIENTS {
        integer id PK
        text full_name
        text phone
        text email
    }
    POINTS {
        integer id PK
        text name
        text address
        text phone
    }
    EQUIPMENT {
        integer id PK
        text name
        text category
        numeric price_day
        text status
        integer point_id FK
    }
    RENTALS {
        integer id PK
        integer client_id FK
        timestamptz starts_at
        timestamptz ends_at
        text status
        numeric total_price
        timestamptz created_at
    }
    RENTAL_ITEMS {
        integer rental_id PK, FK
        integer equipment_id PK, FK
        numeric price
    }
    DEPOSITS {
        integer id PK
        integer rental_id FK
        numeric amount
        text status
        timestamptz created_at
    }

    CLIENTS ||--o{ RENTALS : creates
    POINTS ||--o{ EQUIPMENT : stores
    RENTALS ||--o{ RENTAL_ITEMS : contains
    EQUIPMENT ||--o{ RENTAL_ITEMS : appears_in
    RENTALS ||--o{ DEPOSITS : has
```
