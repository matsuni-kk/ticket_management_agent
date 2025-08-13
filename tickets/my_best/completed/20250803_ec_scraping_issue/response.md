---
file_type: "response"
ticket_id: "TKT-20250803-003"
responder: "國松"
response_date: "2025-08-03"
status: "最終回答"
resolution_status: "解決済"
response_type: "解決策提示"
solution_type: "アーキテクチャ変更・API直接実行"
issued_at: "2025-08-03"
due_date: ""
ball_holder: "クローズ"
---

# 解決策の提供 - ECサイトスクレイピング問題

## 回答者: 國松
## 回答日時: 2025-08-03

## 根本原因分析
- **FireCrawlプラグイン**の機能制限により、アクセス制限回避が困難
- User-Agentやプロキシ設定の柔軟性不足

## 解決策: HTTP リクエスト + FireCrawl API直接実行

### 実装変更点
1. **FireCrawlプラグイン** → **HTTP リクエストノード**に変更
2. FireCrawl APIを直接実行（プラグインより多機能）
3. 環境変数「firecrawl_api」にAPIキー設定

### 設定内容
```bash
curl -X POST https://api.firecrawl.dev/v1/scrape \
  -H "Authorization: Bearer $FIRECRAWL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "url": "url",
    "formats": ["markdown"],
    "proxy": "auto",
    "onlyMainContent": true,
    "waitFor": 3000,
    "timeout": 80000,
    "location": {
      "country": "JP",
      "languages": ["ja-JP"]
    },
    "headers": {
      "User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/18.5 Safari/605.1.15",
      "Accept-Language": "ja-JP"
    }
  }'
```

### 効果
- **プロキシ設定**: "auto"で自動回避
- **User-Agent**: 適切なブラウザヘッダー
- **タイムアウト**: 80秒に延長
- **地域設定**: 日本向け最適化

## 顧客からの結果確認

### Yuna Kamachi (2025-08-03 18:24)
「アドバイスいただいた通りに修正したところ、今日は4本出力したのですが安定してうまくいっています！」

→ **解決確認済み**

## 注意事項
- Amazonは同一キーワード連続実行で制限される可能性
- 必要に応じてAmazon商品検索API利用を検討

## 原因
※必要に応じて追記

## 解決方法
※必要に応じて追記

## 顧客確認・検証結果
※必要に応じて追記
