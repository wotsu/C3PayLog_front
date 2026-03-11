# 🗄️ DB設計書テンプレート

---

# 設計観点

| 項目      | 内容                                    |
| ------- | ------------------------------------- |
| 権限モデル   | RBAC |
| ID戦略    | UUID |
| 論理削除    | 無 |
| 監査ログ    | 必須 / 任意 |

---

# テーブル一覧テンプレート

| ドメイン  | テーブル名             | 役割     | Phase |
| ----- | ----------------- | ------ | ----- |
| アカウント | users             | ユーザー主体 | P0    |
| コア機能  | events          | イベント | P0    |
| コア機能  | items | 商品 | P0 |
| コア機能 | registrations | 支払い情報 | P0 |

---

# ERDテンプレート（抽象版）

```mermaid
erDiagram

    users {
        id PK
        email UNIQUE
        name
        role_id FK
        created_at
        updated_at
    }

    roles {
        id PK
        can_event_modify
        created_at
        updated_at
    }

    events {
        id PK
        title
        created_at
        updated_at
    }

    items {
        id PK
        name
        price
        event_id FK
        created_at
        updated_at
    }

    registrations {
        id PK
        user_id FK
        event_id FK
        item_id FK
        student_id
        paid_at
        created_at
    }

    users ||--o{ registrations
    events ||--o{ items
    users ||--o{ registrations
    items ||--o{ registrations
```

---

# カラム定義テンプレート

## users

| カラム        | 型         | 制約              | 説明              |
| ---------- | --------- | --------------- | --------------- |
| id         | UUID      | PK              |                 |
| email      | VARCHAR   | UNIQUE NOT NULL |                 |
| name       | VARCHAR   | NOT NULL        |                 |
| role_id    | INTEGER   | FK              |                 |
| created_at | TIMESTAMP | NOT NULL        |                 |
| updated_at | TIMESTAMP | NOT NULL        |                 |

---

## roles

| カラム        | 型         | 制約              | 説明              |
| ---------- | --------- | --------------- | --------------- |
| id         | INTEGER    | PK              |                 |
| can_event_modify | BOOLEAN |             |                 |
| created_at | TIMESTAMP | NOT NULL        |                 |
| updated_at | TIMESTAMP | NOT NULL        |                 |

---

## events

| カラム   | 型        | 制約       | 説明        |
| ----- | -------- | -------- | --------- |
| id    | UUID     | PK       |           |
| title | VARCHAR  | NOT NULL |           |
| created_at | TIMESTAMP | NOT NULL | |
| updated_at | TIMESTAMP | NOT NULL | |

---

## items

| カラム        | 型         | 制約       | 説明                    |
| ---------- | --------- | -------- | --------------------- |
| id         | UUID      | PK       |                       |
| event_id  | UUID      | FK       |                  |
| name      | VARCHAR   | NOT NULL |                       |
| price     | INTEGER   | NOT NULL |                       |
| created_at | TIMESTAMP | NOT NULL |                       |
| updated_at | TIMESTAMP | NOT NULL |                       |

---

## registrations

| カラム        | 型         | 制約       | 説明                    |
| ---------- | --------- | -------- | --------------------- |
| id         | UUID      | PK       |                       |
| user_id   | UUID      | FK       |                  |
| event_id  | UUID      | FK       |                  |
| item_id   | UUID      | FK       |                  |
| student_id | VARCHAR  |        |                  |
| paid_at   | TIMESTAMP |        |                 |
| created_at | TIMESTAMP | NOT NULL |                       |
| updated_at | TIMESTAMP | NOT NULL |                       |

---

# 権限設計テンプレート

## RBAC

* users.role_idで判定
