---
file_type: "company_analysis_report"
report_type: "週次レポート"
company: "My Best"
date_range: "2025-W33"
generated_at: "2025-08-13 10:50"
domain: "ticket_management"
agent: "TicketManagement"
---
# 会社別週次レポート - My Best - 2025-W33

## 概要
- 期間: 2025-W33
- 会社: My Best
- 完了チケット数: 4 件
- 未完了チケット数: 3 件

## 完了チケット（解決済/クローズ）
| Ticket ID | タイトル | 原因 | 解決策 | ステータス | パス |
|---|---|---|---|---|---|
| TKT-20250803-004 | ECサイト商品順位がすべてAmazonとして認識される問題 | 抽出ノードの`source`が一律`amazon`に固定 | 各抽出ノードで`source`をECサイト別に設定（amazon/rakuten/yahoo/kakaku） | 解決済 | tickets/my_best/completed/20250803_ec_ranking_issue |
| TKT-20250803-003 | ECサイトスクレイピングの不安定問題 | FireCrawlプラグインの機能制限（UA/プロキシ/タイムアウト柔軟性不足） | HTTPリクエストノードでFireCrawl APIを直接実行（UA/timeout/proxy/locale最適化） | 解決済 | tickets/my_best/completed/20250803_ec_scraping_issue |
| TKT-20250803-005 | 価格.com Tavily抽出でコンテンツ取得不完全問題 | Tavilyは検索＋要約特化でページ全量抽出に不向き | Tavily→URL配列化→FireCrawlイテレーション（onlyMainContent=false）→LLM統合へ変更 | 解決済 | tickets/my_best/completed/20250803_tavily_scraping_issue |
| TKT-20250808-001 | Difyナレッジの検索精度低下/ヒットしない問題 | インデックス作成ジョブのエラーで一部未インデックス化 | Embedding全量再埋め込み→インデックス再実行（rebuild） | クローズ | tickets/my_best/completed/20250808_dify_knowledge_search_issue |

## 未完了チケット（新規/対応中/保留）
| Ticket ID | タイトル | 現状ステータス | 原因（現象/制約） | 解決方針/次アクション | パス |
|---|---|---|---|---|---|
| TKT-20250806-001 | ECスペック抽出機能開発（401エラー解決済み） | 保留 | 出力肥大・イテレーション過多、FireCrawlの安定性（並列/文字数上限） | FireCrawl→HTTPリクエスト化、URL配列化→後段LLMイテレーション（スペック/口コミ）、並列5・件数制御（unique_urls[:N]） | tickets/my_best/in_progress/20250806_ec_ranking_401_error |
| TKT-20250806-002 | FireCrawl商品重複除去の入力値制限問題 | 対応中 | LLM入力値制限（約649k tokens）で巨大入力 | 分割バッチ→コード前処理で明白重複除去→LLM精密判定→最終統合（トークン/コスト監視） | tickets/my_best/in_progress/20250806_firecrawl_deduplication_issue |
| TKT-20250812-001 | 公式ページ検索ノードが類似商品/別型番を取得する問題 | 保留（先方検証待ち） | クエリ曖昧・公式ドメイン優先不足・同一性検証なし | クエリ厳密化（商材/メーカー/製品/型番＋公式語＋除外語）、`site:`制約、Identity抽出→Consistency検証（閾値0.85） | tickets/my_best/in_progress/20250812_official_page_search_wrong_product_disambiguation |

## メモ/トピック
- 類似検索の件は設定反映済みだが、先方再検証待ちのため保留維持。
- スペック抽出は並列数・イテレーション件数に依存するため、実運用に合わせたNの調整が必要。
- 重複除去はバッチサイズと前処理設計のPoC後に閾値確定（コスト/レイテンシ指標を併記予定）。
