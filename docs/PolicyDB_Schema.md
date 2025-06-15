# 🗂 制度DBスキーマ仕様 – SupportFlow構想用（v1）

SupportFlowでは、国・自治体の制度情報を統合・照合するために、以下の構造に準拠したJSON形式の制度DBを想定しています。

---

## 🧱 A. 基本構造（最小単位）

各制度は以下の基本項目を含む構造です：

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

## 🔍 B. 条件定義ブロック（conditions）

対象者要件に関するロジック定義です：

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

## 📄 C. 必要書類構造（required_documents）

```json
"required_documents": [
  { "name": "本人確認書類", "type": "任意書式", "format": "JPEG/PDF" },
  { "name": "住民票", "type": "市役所発行", "format": "原本提出" }
]
```

---

## 🏷 D. メタ情報と識別属性（metadata）

更新日時・カテゴリ・対象種別など：

```json
"metadata": {
  "last_updated": "2024-11-01",
  "version": "1.1",
  "source": "https://www.city.fukuoka.lg.jp/welfare/",
  "tags": ["市民向け", "定額給付", "65歳以上"],
  "applicable_to": "individual"  // or "corporate"
}
```

---

## 🔁 E. 制度更新とデータ連携モデル

- **中央制度（国）**：API連携（例：`https://api.support.go.jp/policies`）にて配信
- **地方制度（自治体）**：各自治体内で作成・配備（例：LGWAN環境で運用）
- **UI側処理**：国＋地方のJSONデータをマージし、重複制度は `id` に基づき統合表示
- **更新責任分担**：
  - 国：国制度の改廃・API配信
  - 自治体：地方制度の定義・更新（UI上はラベル付きで明示）

---

## 🏢 F. 法人制度への拡張対応

- `metadata.applicable_to` を使用し、「individual」「corporate」どちらに適用されるかを指定
- 質問構文（`QnA_Spec.md`）と連携し、対象別の提示が可能

例（法人向け）：

```json
{
  "id": "corp_002",
  "title": "中小企業向け設備投資補助金",
  "applicable_to": "corporate",
  "conditions": [...],
  "required_documents": [...],
  "metadata": { "version": "1.0" }
}
```
