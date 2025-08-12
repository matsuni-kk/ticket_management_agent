---
file_type: "inquiry"
ticket_id: "TKT-20250806-002"
company: "My Best"
reporter: "Kaho Nagaso"
date: "2025-08-06"
status: "対応中"
category: "技術的問題"
priority: "中"
related_tickets: ["TKT-20250803-004", "TKT-20250806-001"]
related_systems: ["Dify", "Fire Crawl", "商品ピックアップ", "LLM重複除去"]
technical_issue: "LLM入力値制限によるデータ処理不可"
issued_at: "2025-08-06"
due_date: ""
ball_holder: "当方"
---

# 問い合わせ内容 - Fire Crawl商品重複除去の入力値制限問題

## 問い合わせ者: Kaho Nagaso
## 問い合わせ日時: 2025-08-06 10:40

@matsuni
お疲れ様です！
先日作成いただいた、fire crawl版の商品ピックアップのdifyですが、重複している商品を1つに統合させるのがコードだとなかなかうまくいかないのでLLMにさせようとしたところデータが膨大過ぎて入力値に入らなくなってしまっており..🐻‍❄️😭

こちらどのようにしたら入力を正確にできるかご教示いただけますと幸いです🐻🙏

## 技術的詳細

### 問題の状況
- **システム**: Fire Crawl版の商品ピックアップDify
- **処理**: 重複商品の統合処理
- **課題**: コードベースでの重複除去が困難
- **代替手法**: LLMによる重複除去を試行
- **エラー**: データ量が膨大でLLMの入力値制限に抵触

### 出力値の分析
```json
{
  "text": "{\"description\":\"A list of final, deduplicated products.\",\"properties\":{\"final_products\":{\"type\":\"array\",\"description\":\"An array of product objects, where each object represents a unique product with its aggregated information.\",\"items\":{\"type\":\"object\",\"properties\":{\"product_name\":{\"type\":\"string\",\"description\":\"The most representative name for the product group.\"},\"urls\":{\"type\":\"array\",\"items\":{\"type\":\"string\"},\"description\":\"A list of all unique URLs for the product group.\"},\"amazon_rank\":{\"type\":\"string\",\"description\":\"The best (lowest) Amazon rank for the product group. '順位なし' if no rank is available.\"},\"rakuten_rank\":{\"type\":\"string\",\"description\":\"The best (lowest) Rakuten rank for the product group. '順位なし' if no rank is available.\"},\"yahoo_rank\":{\"type\":\"string\",\"description\":\"The best (lowest) Yahoo Shopping rank for the product group. '順位なし' if no rank is available.\"},\"kakaku_rank\":{\"type\":\"string\",\"description\":\"The best (lowest) Kakaku.com rank for the product group. '順位なし' if no rank is available.\"}},\"required\":[\"product_name\",\"urls\",\"amazon_rank\",\"rakuten_rank\",\"yahoo_rank\",\"kakaku_rank\"]}}},\"required\":[\"final_products\"],\"type\":\"object\"}",
  "usage": {
    "prompt_tokens": 649032,
    "prompt_unit_price": "1.25",
    "prompt_price_unit": "0.000001",
    "prompt_price": "0.81129",
    "completion_tokens": 1773,
    "completion_unit_price": "10",
    "completion_price_unit": "0.000001",
    "completion_price": "0.01773",
    "total_tokens": 650805,
    "total_price": "0.82902",
    "currency": "USD",
    "latency": 112.10313068100004
  },
  "finish_reason": "STOP"
}
```

### トークン使用量分析
- **プロンプトトークン**: 649,032 tokens（膨大）
- **完了トークン**: 1,773 tokens
- **総トークン**: 650,805 tokens
- **総コスト**: $0.82902 USD
- **レイテンシ**: 112秒

## データ構造分析

### 期待する出力フォーマット
重複除去後の商品データ構造:
```javascript
{
  final_products: [
    {
      product_name: "商品グループの代表名",
      urls: ["URL1", "URL2", ...], // 重複商品の全URL
      amazon_rank: "最良順位", 
      rakuten_rank: "最良順位",
      yahoo_rank: "最良順位", 
      kakaku_rank: "最良順位"
    }
  ]
}
```

### 重複統合ロジック
- **商品名統合**: 最も代表的な名前を選択
- **URL集約**: 重複商品の全URLを配列で保持
- **順位統合**: 各ECサイトで最良（最小値）の順位を採用
- **"順位なし"**: 順位データが無い場合のデフォルト値

## 関連チケット
- **TKT-20250803-004**: EC商品順位誤認識問題（解決済み）
  - 同一報告者（Kaho Nagaso）
  - Dify・EC順位システム関連
  - 商品データ処理の実績あり

- **TKT-20250806-001**: ECスペック抽出機能開発（進行中）
  - 同一システム（商品データ処理）
  - 大量データ処理の共通課題

## 確認済み事項
- Fire Crawl版商品ピックアップDifyが稼働中
- コードベースでの重複除去実装が困難
- LLMアプローチで技術的制約に直面
- 重複除去ロジック自体の設計は完成済み