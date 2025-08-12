---
file_type: "technical_analysis"
ticket_id: "TKT-20250803-005"
analyst: "matsuni"
analysis_date: "2025-08-03"
complexity: "中"
tech_category: "WebスクレイピングAPI・ワークフロー設計"
tools_used: ["Tavily", "価格.com", "スクレイピングシステム"]
root_cause: "Tavilyの機能特性と要件のミスマッチ"
solution_complexity: "中"
issued_at: "2025-08-03"
due_date: ""
ball_holder: "クローズ"
---

# 技術的分析 - 価格.com Tavily抽出問題

## 問題の技術的背景

### Tavilyの機能特性
Tavilyは以下の機能に特化したツール：

1. **自然言語検索**
   - キーワードベースでのURL検索
   - 関連度スコア付きの結果提供

2. **ページ要約**
   - 取得したページの内容を要約形式で提供
   - 全コンテンツではなく、重要部分の抽出

3. **制限事項**
   - 詳細なスクレイピングには不適
   - 大量データの完全取得には向かない
   - 構造化データの抽出能力が限定的

## 現在の問題分析

### 取得結果の分析
現在のTavily出力を見ると：

```json
{
  "content": "PCケース製品一覧！たくさんの製品の中から、価格やスペック、ランキング、満足度など、さまざまな条件を指定して自分にピッタリの製品を簡単に探し出すことができ",
  "score": 0.6989468,
  "title": "ホワイト(白)系のPCケース 人気売れ筋ランキング",
  "url": "https://kakaku.com/pc/pc-case/itemlist.aspx?altTitle=00005"
}
```

### 問題点
1. **コンテンツ切り捨て**: ページの概要のみで商品詳細が不足
2. **構造化データ不足**: 商品名、価格、順位などの詳細情報が取得できない
3. **不完全な抽出**: ランキング全体の情報が欠如

## 推奨される解決策

### アーキテクチャ変更

#### 現在の処理フロー
```
Tavily単体 → 不完全な結果
```

#### 推奨される処理フロー
```
1. Tavily (URL検索・ページ特定)
   ↓
2. URL抽出 (対象URLの確定)
   ↓
3. 専用スクレイピング (詳細コンテンツ取得)
   ↓
4. イテレーション処理 (複数商品の処理)
   ↓
5. LLM構造化 (データの整理・フォーマット)
```

### 実装詳細

#### Stage 1: Tavily検索
```javascript
// Tavilyで対象ページを特定
tavilyResult = tavily.search("価格.com PCケース ランキング 白い");
targetURL = tavilyResult.results[0].url;
```

#### Stage 2: 専用スクレイピング
```javascript
// FireCrawlまたは他のスクレイピングツールを使用
scrapingResult = firecrawl.scrape({
  url: targetURL,
  options: {
    formats: ["markdown", "html"],
    waitFor: 3000,
    extractSchema: {
      products: {
        name: "string",
        rank: "number", 
        price: "string",
        url: "string"
      }
    }
  }
});
```

#### Stage 3: データ処理
```javascript
// 取得したデータをLLMで構造化
structuredData = llm.process({
  input: scrapingResult.content,
  instruction: "ランキング情報を抽出し、JSON形式に整理してください",
  schema: ProductRankingSchema
});
```

## 技術的考慮事項

### パフォーマンス
- **Tavily**: 高速検索（3.8秒）
- **スクレイピング**: 追加時間（5-10秒）
- **LLM処理**: データ量に依存（3-15秒）

### 信頼性
- **Tavily**: URL特定の精度が高い（関連度スコア0.69+）
- **スクレイピング**: ページ構造変更に敏感
- **LLM**: データ構造化の品質が安定

### スケーラビリティ
- 複数ページの並列処理可能
- イテレーション処理でメモリ効率良好
- API制限に注意が必要

## 期待される改善効果

### データ取得率
- **Before**: 部分的コンテンツ（～20%）
- **After**: 完全なランキング情報（～95%）

### データ品質
- **Before**: 要約情報のみ
- **After**: 構造化された詳細データ

### 処理時間
- **Before**: 3.8秒（不完全）
- **After**: 15-25秒（完全）

## 実装優先度

1. **高**: URL特定とスクレイピングの統合
2. **中**: データ構造化とバリデーション
3. **低**: パフォーマンス最適化と並列処理

## リスク評価

### 技術リスク
- **低**: 既存技術の組み合わせ
- **中**: サイト構造変更への対応
- **低**: API制限への対処

### 運用リスク
- **低**: 処理時間の増加
- **中**: エラーハンドリングの複雑化
- **低**: メンテナンス負荷の増加