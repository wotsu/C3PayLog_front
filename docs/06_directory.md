# 📁 ディレクトリ構成図

---

# 0️⃣ 設計前提

| 項目      | 内容                                 |
| ------- | ---------------------------------- |
| リポジトリ構成 | Polyrepo  |
| アーキテクチャ |  Clean Architecture  |
| デプロイ単位   | 単一サービス |
| 言語      | TypeScript / Go |
| MVP方針   | P0に必要なディレクトリのみ |

---

# フロントエンド構成

```id="tq93md"
/
├── src/
│   ├── app/           # ルーティング層
│   ├── features/      # 機能単位モジュール
│   ├── components/    # 共通UI
│   ├── hooks/
│   ├── lib/           # APIクライアント等
│   ├── stores/        # 状態管理
│   └── types/
├── public/
├── infra/
└── docs/
```

---

## Featureベース構成

```id="t6lm52"
features/
├── auth/
│   ├── components/
│   ├── api.ts
│   ├── hooks.ts
│   └── types.ts
├── entity/
│   ├── components/
│   ├── api.ts
│   ├── hooks.ts
│   └── types.ts
```

---

# バックエンド構成

```id="9wh13c"
/
├── cmd/                # エントリポイント
├── internal/
│   ├── domain/         # エンティティ・ビジネスルール
│   ├── usecase/        # アプリケーションロジック
│   ├── infrastructure/ # DB
│   └── interface/      # HTTP層
├── migrations/
├── infra/
└── docs/
```

---

# インフラ構成

```id="v9k0mz"
infra/
└── docker/
```

---

# ドキュメント構成

```id="az1k93"
docs/
├── 01_feature_list.md
├── 02_tech_stack.md
├── 03_screen-flow.md
├── 04_permission-design.md
├── 05_erd.md
├── 06_directory.md
├── 07_infrastructure.md
├── 08_logging.md
├── 09_schedule_and_issues.md
└── designdoc.md
```
