---
file_type: "bulk_progress_report"
report_scope: "今日"
target_status: "未完了"
priority_filter: "全優先度"
company_filter: "全社"
report_type: "サマリーレポート"
generated_at: "2025-08-13 10:32"
domain: "ticket_management"
agent: "TicketManagement"
---
# 残チケット集約・進捗管理レポート - 2025-08-13
週次: 2025-W33

## チケット一覧（表形式）

### 未完了チケット（新規/対応中/保留）
| Ticket ID | タイトル | 詳細 | 依頼者 | 優先度 | カテゴリ | 担当 | 作成日 | 更新日 | 期限 | ステータス | 原因 | 解決方法 | パス |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TKT-20250806-001 | ECスペック抽出機能開発（401エラー解決済み） | ECランキングページ401エラー問題 | Yuna Kamachi | 緊急 | 機能開発 | 技術チーム | 2025-08-06 | 2025-08-11 | 2025-08-08 | 保留 |  |  | tickets/my_best/in_progress/20250806_ec_ranking_401_error |
| TKT-20250806-002 | Fire Crawl商品重複除去の入力値制限問題 | TKT-20250806-002 | Kaho Nagaso | 中 | 技術的問題 | 技術チーム | 2025-08-06 | 2025-08-06 |  | 対応中 |  | 検索設定の再調整（top_k/閾値/ハイブリッド/Rerank） | tickets/my_best/in_progress/20250806_firecrawl_deduplication_issue |
| TKT-20250812-001 | 公式ページ検索ノードが類似商品/別型番を取得する問題 | 「★検証_紹介文（1段落目）生成」のワークフローにおいて、公式ページ検索 ノードが類似商品や別型番、別カテゴリ（例: 施設/イベント名など）を誤って採用してしまう。特に商品名が一般名詞に近い場合や、百均系など公開情報が少ない商材で誤取得が発生。 | Kano Sakuma | 中 | 技術的問題 | matsuni | 2025-08-12 | 2025-08-13 |  | 保留 | 検索クエリにブランド/カテゴリ/型番等の拘束が弱い、site: 制約未活用 | 検索設定の再調整（top_k/閾値/ハイブリッド/Rerank） | tickets/my_best/in_progress/20250812_official_page_search_wrong_product_disambiguation |