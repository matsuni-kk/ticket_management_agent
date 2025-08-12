---
file_type: "technical_analysis"
ticket_id: "TKT-20250812-001"
analyst: "TicketManagement Agent"
analysis_date: "2025-08-12"
complexity: "中"
tech_category: "情報検索/LLM検証/ワークフロー設計"
---

## 技術分析（誤取得の構造）

### 主因
- クエリの曖昧さ（一般名詞/施設名との同形、ブランド別名/シリーズ名の揺れ）
- ドメイン制約不足（公式>EC>ニュース等の優先順位未設定）
- 型番/カテゴリの同一性検証が無い、または弱い
- 情報量が少ない商材でランキングが外乱に敏感（百均系）

### 対策の設計方針（3段階）
1) Retrieve の厳密化
   - クエリテンプレート: `"{brand} {product}" ["{model}"] [カテゴリ語] "公式"` を基本。
   - ドメイン制約: `site:{official_domain} OR site:{brand_site}`、未特定時は許可リスト優先、無ければ一般検索。
   - 除外語: 既知の誤ヒット語を `-` で付与（例: 公園, レジャー, スライダー など）。
   - multi-query: ブランド別名/シリーズ名の同義語で複数クエリを発行し、候補を統合。
2) Extract の構造化
   - 各候補ページから Product Identity を JSON 抽出（brand, product_name, model, category, official, url）。
   - タイトル/見出し/構造化データ（JSON-LD/Product, OpenGraph）も参照して正規化。
3) Validate の同一性検証
   - 「brand一致（別名辞書含む）」「category一致」「model一致（指定時）」をスコア化し、閾値未満は reject。
   - LLM バリデータに「不一致理由」を出力させ、フォールバック制御をしやすくする。

## アーキテクチャ（候補）
1. QueryBuilder → 2. Search(Top-K) → 3. Fetch → 4. IdentityExtractor → 5. ConsistencyValidator → 6. Rerank/Select → 7. Fallback

### スコアリング例
`score = 0.4*brand_match + 0.25*category_match + 0.25*model_match + 0.10*query_overlap`

### 公式優先/除外
- allowlist: 公式ドメイン（メーカー/ブランド公式、直販）
- blocklist: レジャー/施設関連、まとめサイト等（誤取得源を観測に基づき追加）

## LLM抽出/検証の設計

### 抽出スキーマ例
```json
{
  "brand": "",
  "product_name": "",
  "model": null,
  "category": "",
  "official": false,
  "url": ""
}
```

### 検証スキーマ例
```json
{
  "target": {"brand": "", "product_name": "", "model": null, "category": ""},
  "candidate": {"brand": "", "product_name": "", "model": null, "category": "", "url": ""},
  "verdict": "accept|reject|unsure",
  "confidence": 0.0,
  "mismatch_reasons": []
}
```

### ルール例（合否基準）
- brand: 完全一致 or 別名辞書一致（例: 味の素AGF ≈ AGF）
- category: 完全一致（例: コーヒー豆 ≠ インスタント/スティック）
- model: 指定時は正規化後に完全一致（空白/ハイフン/全半角の差を無視）
- いずれか不一致 → reject、情報不足 → unsure（次候補へ）

## ケース別対策
- 「ウォーターランド」: 施設系語（公園, プール, スライダー）を除外。ドメイン許可リストを導入。
- AGF「ちょっと贅沢な珈琲店」: カテゴリをコーヒー豆で強制。インスタント/スティック関連語を除外。
- 情報が少ない百均: 公式が無い場合、公式のニュース/製品一覧/カタログPDFを代替一次情報として採用。

## 計測/運用
- テストセットを用意し、precision/recall、誤採用率、未採用率、平均応答時間を継続計測。
- ログに candidate/選定理由/拒否理由 を残し、ブロック/許可語の辞書を継続学習。


