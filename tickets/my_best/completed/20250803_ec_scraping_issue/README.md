---
file_type: "ticket_summary"
ticket_id: "TKT-20250803-003"
title: "ECサイトスクレイピングの不安定問題"
company: "My Best"
reporter: "Yuna Kamachi"
create_date: "2025-08-03"
update_date: "2025-08-03"
status: "解決済"
category: "技術的問題"
priority: "中"
assigned_to: "國松"
related_members: ["miyatti", "maru-san", "Minami Sasaki"]
estimated_hours: 4
final_resolution_date: "2025-08-03"
customer_confirmation: "安定して動作確認済み"
issued_at: "2025-08-03"
due_date: ""
ball_holder: "クローズ"
---

# チケット: ECサイトスクレイピングの不安定問題

## 基本情報
- **チケットID**: TKT-20250803-003
- **タイトル**: ECサイトスクレイピングの不安定問題
- **会社名**: My Best
- **報告者**: Yuna Kamachi
- **担当者**: 國松
- **作成日**: 2025-08-03
- **ステータス**: 解決済
- **優先度**: 中

## 問題概要
3ECサイト（Amazon、楽天、Yahoo）から商品データを抽出する処理が約50%の確率で失敗

### 具体的エラー
- **Amazon**: 503エラー（ボット検出）
- **Yahoo**: Request timed out
- **楽天**: 正常動作

## 原因
FireCrawlプラグインの機能制限により、適切なUser-Agentやプロキシ設定、タイムアウト等の細かな制御が難しく、アクセス制限の回避ができていなかった。

## 解決策

### 実装された解決策
1. **FireCrawlプラグイン** → **HTTP リクエスト + FireCrawl API直接実行**に変更
2. 適切なUser-Agent、プロキシ設定を実装
3. タイムアウトを80秒に延長
4. 日本向け地域設定を追加

### 設定変更内容
- プロキシ: "auto"で自動回避
- User-Agent: Safari/MacOS設定
- タイムアウト: 80,000ms
- 地域: JP、言語: ja-JP

## 結果確認

### Yuna Kamachi (2025-08-03 18:24)
「修正したところ、今日は4本出力したのですが安定してうまくいっています！」

→ **解決確認済み**

## 学習事項
- プラグイン版より直接API実行の方が柔軟性が高い
- 適切なヘッダー設定でアクセス制限を回避可能
- FireCrawl APIの多機能性を活用することで安定性向上

詳細は `inquiry.md` と `response.md` を参照。

## 再発防止・運用メモ（要点）
- プラグインではなくHTTPリクエスト＋API直接実行の方針を基本とする
- UA/ヘッダ/タイムアウト/ロケール/プロキシの設定値はレポジトリに記録・共有

## 再発防止・運用メモ
※必要に応じて追記
