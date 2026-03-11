# Infrastructure Guidelines`

---

# System Components

---

## Edge Layer

### CDN 

* キャッシュ
* 地理的最適化

---

## Application Layer

### Application Service

* Conoha VPS

責務：

* ビジネスロジック
* API処理
* 権限チェック（最終判定）
* TLS終端
* JWT検証

---

## Data Layer

| コンポーネント        | 用途         |
| -------------- | ---------- |
| RDB            | トランザクション   |
