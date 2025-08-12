---
file_type: "technical_details"
ticket_id: "TKT-20250812-001"
analyst: "TicketManagement Agent"
analysis_date: "2025-08-12"
complexity: "中"
tech_category: "プロンプト設計/検索クエリ/検証ルール"
issued_at: "2025-08-12"
due_date: ""
ball_holder: "当方"
---

## 検索クエリの推奨テンプレ
```text
"{brand} {product}" ["{model}"] (公式 OR "公式サイト" OR "製品情報" OR "商品情報")
site:{official_domain} OR site:{brand_site}
-公園 -イベント -施設 -スライダー -レビュー -まとめ -価格比較
```

## Identity 抽出プロンプト（例）
```text
あなたは製品ページから Product Identity を抽出するエンジンです。本文・構造化データを読み、以下のJSONだけを出力してください。
必須: brand, product_name, category, url。modelはあれば。公式サイトかどうかを official にtrue/falseで設定。

出力JSONスキーマ:
{
  "brand": string,
  "product_name": string,
  "model": string|null,
  "category": string,
  "official": boolean,
  "url": string
}
```

## Consistency バリデータ プロンプト（例）
```text
与えられた target（期待する製品）と candidate（抽出結果）が同一製品かを判定。
厳格に判定し、結果のみを次のJSONで返すこと。

入力:
target = {brand, product_name, model|null, category}
candidate = {brand, product_name, model|null, category, url}

出力:
{
  "verdict": "accept"|"reject"|"unsure",
  "confidence": number(0-1),
  "mismatch_reasons": string[]
}

判定基準:
- brand 完全一致または別名辞書一致でない場合は reject。
- category が異なる場合（例: コーヒー豆 vs インスタント）は reject。
- model 指定があり不一致なら reject。
- 情報不足は unsure。
```

## 受け入れロジック（擬似コード）
```python
def accept_candidate(target, candidate, verdict, confidence):
    if verdict != "accept" or confidence < 0.85:
        return False
    return True
```

## ドメイン許可/除外リストの初期例
- allow: `agf.co.jp`, `brand.official.*`, メーカー直販EC
- block: `*.park.*`, `*.pref.*`（施設/公園系）、一般まとめ/価格比較（必要に応じて）

## 評価計画（最小セット）
- 既知の誤取得 10件 + 正解URLを用意
- 設定A: 既存、設定B: 公式優先 + バリデータ導入 でAB
- 指標: 誤採用率（↓）、未採用率（↔︎〜↓）、処理時間（↔︎）


