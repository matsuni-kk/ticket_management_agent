---
file_type: "technical_details"
ticket_id: "TKT-20250806-001"
analyst: "技術チーム"
analysis_date: "2025-08-08"
complexity: "中"
tech_category: "ECスクレイピング/LLM抽出/表整形"
issued_at: "2025-08-08"
due_date: "2025-08-08"
ball_holder: "先方"
---

## 検証出力抜粋（2025-08-08）
スペック抽出のJSONサンプル（先方共有の一部を転記、長文のため抜粋）。

```
{"product_name": "Nutro Supremo Dog Food for Small Adult Dogs ...", "brand": "ニュートロ", "specifications": [{"name": "対象ペット", "value": "犬"}, {"name": "推奨犬種", "value": "小型犬"}, ...]}

{"product_name": "Hill's Science Diet Chicken Dog Food, Adult ...", "brand": "ヒルズ サイエンス・ダイエット", "specifications": [{"name": "フレーバー", "value": "チキン"}, {"name": "対象年齢", "value": "成犬（1～6歳）"}, ...]}
```

備考:
- URLトレーサビリティ付与後、4カラム（カテゴリ/項目/値/URL）へ整形。
- 出力総量が8万文字を超えないようイテレーション件数と出力密度を調整。
