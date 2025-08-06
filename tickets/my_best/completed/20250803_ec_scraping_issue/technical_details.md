---
file_type: "technical_details"
ticket_id: "TKT-20250803-003"
analyst: "國松"
analysis_date: "2025-08-03"
complexity: "中"
tech_category: "WebスクレイピングAPI"
tools_used: ["Dify", "ECサイトAPI"]
error_types: ["503エラー", "アクセス制限"]
---

# 技術詳細情報

## スクレイピング結果の詳細

### Amazon - 503エラー詳細
```json
{
  "text": "[![Amazon.co.jp](https://images-fe.ssl-images-amazon.com/images/G/09/other/logo-jp.jpg)](https://www.amazon.co.jp/ref=cs_503_logo/)\n\n|     |\n| --- |\n| **ご迷惑をおかけしています！**<br>お客様のリクエストの処理中にエラーが発生しました。できるだけ早くこの問題を解決いたします。<br>注文手続きの途中でこのエラーが表示された場合は、注文は確定されていませんので、ご注意ください。<br>ご不便をおかけして申し訳ございません。<br>[![](https://images-fe.ssl-images-amazon.com/images/G/09/buttons/continue-shopping.gif)](https://www.amazon.co.jp/ref=cs_503_link/) Amazon.co.jpホームへ |",
  "files": [],
  "json": [
    {
      "data": {
        "metadata": {
          "contentType": "text/html",
          "creditsUsed": 1,
          "error": "Service Unavailable",
          "proxyUsed": "basic",
          "scrapeId": "a0d6678e-d15a-4cd8-8b2f-ca6a4a8113ea",
          "sourceURL": "https://www.amazon.co.jp/馬油シャンプー/s?k=馬油シャンプー",
          "statusCode": 503,
          "title": "\nご迷惑をおかけしています！\n"
        }
      },
      "success": true
    }
  ]
}
```

### Yahoo - タイムアウトエラー詳細
```json
{
  "text": "",
  "files": [],
  "json": [
    {
      "error": "Request timed out",
      "success": false
    }
  ]
}
```

## 推奨される技術的解決策

### 1. Amazon対策
- **User-Agent偽装**: ブラウザとして認識されるようヘッダーを設定
- **リクエスト間隔**: 1-3秒のランダムな遅延を追加
- **セッション管理**: クッキーを保持してセッションを維持
- **IPローテーション**: プロキシサービスの活用

### 2. Yahoo対策
- **タイムアウト値の増加**: 30秒以上に設定
- **リトライメカニズム**: 3回まで自動リトライ
- **並列処理の制限**: 同時接続数を1-2に制限
- **エラーハンドリング**: タイムアウト時の graceful degradation

### 3. 共通対策
- **エラーログの詳細化**: デバッグ用の詳細ログ出力
- **モニタリング**: 成功率のリアルタイム監視
- **フォールバック**: API利用への切り替えオプション