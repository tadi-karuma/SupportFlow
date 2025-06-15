# 🗂 制度DBスキーマ仕様 – SupportFlow構想用（v1）

SupportFlowでは、各種支援制度を一元的に扱うため、以下の構造に準拠したJSON形式の制度DBを想定する。

---

## 1. 最上位スキーマ構造

```json
{
  "id": "seido-001",
  "title": "高齢者生活支援給付",
  "description": "65歳以上の高齢者を対象とした生活支援のための月次給付制度",
  "provider": "福祉課",
  "jurisdiction": "福岡市",
  "scope": ["生活支援", "高齢者"],
  "valid_from": "2022-04-01",
  "valid_until": null,
  "conditions": [],
  "required_documents": [],
  "reservation_required": true,
  "entry_point_url": "https://city.fukuoka.lg.jp/welfare/elderly/support-001.html"
}
```

---

## 2. `conditions` 構成（判定条件）

```json
"conditions": [
  {
    "question_id": "q001",
    "expected": "65歳以上",
    "logic": "equals"
  },
  {
    "question_id": "q003",
    "expected": "一人暮らし",
    "logic": "equals"
  }
]
```

---

## 3. `required_documents` 構成（必要書類）

```json
"required_documents": [
  { "name": "本人確認書類", "type": "任意書式", "format": "JPEG/PDF" },
  { "name": "住民票", "type": "市役所発行", "format": "原本提出" }
]
```

---

## 4. `metadata` の推奨補足項目

```json
"metadata": {
  "last_updated": "2024-11-01",
  "version": "1.1",
  "source": "https://www.city.fukuoka.lg.jp/welfare/",
  "tags": ["市民向け", "定額給付", "65歳以上"]
}
```

---

## 5. データ連携前提

- 国制度はAPI取得（例：`api.support.go.jp/policies`）
- 地方制度は自治体ごとに構築されたJSONデータ（LGWAN対応）
- UI表示前にマージ処理を実施し、重複制度はラベル統合すること
