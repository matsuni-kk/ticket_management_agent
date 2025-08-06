---
file_type: "inquiry"
ticket_id: "TKT-20250803-003"
company: "My Best"
reporter: "Yuna Kamachi"
date: "2025-08-03"
status: "解決済"
category: "技術的問題"
priority: "中"
related_members: ["miyatti", "maru-san", "Minami Sasaki"]
---

# 問い合わせ内容 - ECサイトスクレイピング問題

## 報告者: Yuna Kamachi
## 問い合わせ日時: 2025-08-03

## 問題概要
3ECサイト（Amazon、楽天、Yahoo）から商品ページを40件抽出する処理が約50%の確率で失敗

## 具体的エラー

### Amazon
- **エラー**: 503 Service Unavailable（ボット検出）
- **原因**: AIとして識別されアクセスブロック

### Yahoo
- **エラー**: Request timed out
- **試行済み対策**: パラレルモード1に変更（改善なし）

### 楽天
- **ステータス**: 正常動作

## 試行した解決策
- User-Agentヘッダー設定を検討したが設定場所不明
- Yahoo のタイムアウト対策でパラレルモード調整したが効果なし

## 求める解決策
- 安定したスクレイピング実行（成功率向上）
- User-Agent等の設定方法
- Amazon、Yahooのアクセス制限回避方法