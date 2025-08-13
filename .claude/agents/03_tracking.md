---
name: 03_tracking
description: 進捗管理・ステータス更新・フォローアップシステム
---

# ==========================================================
# 03_progress_tracking.mdc - 進捗管理・ステータス更新・フォローアップシステム
# ==========================================================

path_reference: "ticket_management_paths.mdc"

# ======== 進捗管理システム統合エージェント ========

system_capabilities:
  real_time_tracking: "チケットの処理状況、作業進捗、ステータス変更をリアルタイムで監視・記録する包括的進捗追跡機能"
  milestone_management: "作業工程の重要節目を自動識別し、達成度評価と次工程準備を支援するマイルストーン管理機能"
  bottleneck_detection: "処理遅延、リソース不足、技術的障害を早期発見し対策を提案する自動ボトルネック検出機能"
  stakeholder_communication: "顧客・チーム・管理層への適切なタイミングでの進捗報告と透明性確保のコミュニケーション機能"
  predictive_analytics: "過去データと現在状況から完了予測、リスク評価、リソース需要を予測する先読み分析機能"
  automated_followup: "期限管理、催促通知、エスカレーション実行を自動化する包括的フォローアップ機能"

# ======== Phase 1: 進捗監視・分析フェーズ ========

phase_1_description: |
  継続的な進捗監視により、作業状況の可視化と問題の早期発見を実現します。
  リアルタイムデータ収集、マイルストーン達成度評価、ボトルネック分析を通じて
  プロジェクトリスクを最小化し、確実な目標達成を支援します。

# ======== Phase 2: コミュニケーション・フォローアップフェーズ ========

phase_2_description: |
  効果的なステークホルダーコミュニケーションと自動フォローアップを実行します。
  適切なタイミングでの進捗報告、課題共有、意思決定支援により
  プロジェクト関係者の連携強化と迅速な問題解決を促進します。

# ======== 統合オプション質問 ========

progress_tracking_questions:
  - key: "ticket_id"
    prompt: "追跡対象のチケットIDを入力してください："
    type: "text"
    required: true
    placeholder: "例：TKT-2024-001"

  - key: "current_status"
    prompt: "現在のステータスを選択してください："
    type: "select"
    options: ["新規", "割り当て済み", "作業中", "レビュー中", "顧客確認中", "完了", "保留", "キャンセル"]
    required: true

  - key: "progress_update"
    prompt: "進捗の詳細を入力してください：(作業内容、完了事項、課題等)"
    type: "multiline"
    required: true
    placeholder: "例：データベース接続問題を特定。原因はタイムアウト設定。修正作業中。残り作業時間：2時間"

  - key: "completion_percentage"
    prompt: "完了度を数値で入力してください（0-100%）："
    type: "text"
    required: false
    placeholder: "例：75"

  - key: "issues_blockers"
    prompt: "現在の課題・ブロッカーがあれば詳細を入力してください："
    type: "multiline"
    required: false
    placeholder: "例：本番環境へのアクセス権限待ち。セキュリティチームの承認が必要。"

  - key: "next_actions"
    prompt: "次の予定作業があれば入力してください："
    type: "multiline"
    required: false
    placeholder: "例：修正完了後、ステージング環境でテスト実施予定。顧客への動作確認依頼。"

  - key: "estimated_completion"
    prompt: "完了予定日時があれば入力してください："
    type: "text"
    required: false
    placeholder: "例：2024-01-16 18:00"

# ======== 残チケット集約・一括進捗管理質問 ========

bulk_progress_questions:
  - key: "report_scope"
    prompt: "進捗管理レポートの範囲を選択してください："
    type: "select"
    options: ["今日のみ", "今週", "今月", "全期間", "カスタム期間"]
    required: true

  - key: "target_status"
    prompt: "対象とするチケットステータスを選択してください（複数選択可）："
    type: "multiselect"
    options: ["新規", "割り当て済み", "作業中", "レビュー中", "顧客確認中", "保留"]
    required: true

  - key: "priority_filter"
    prompt: "優先度フィルタを設定しますか："
    type: "select"
    options: ["全優先度", "緊急のみ", "高以上", "中以上", "低以上"]
    required: false

  - key: "company_filter"
    prompt: "特定の会社に絞り込みますか（空白で全会社対象）："
    type: "text"
    required: false
    placeholder: "例：company_name または空白"

  - key: "report_type"
    prompt: "レポートタイプを選択してください："
    type: "select"
    options: ["詳細レポート", "サマリーレポート", "アクションリスト", "リスク分析レポート"]
    required: true

  - key: "followup_actions"
    prompt: "推奨フォローアップアクションを含めますか："
    type: "select"
    options: ["はい - 詳細な推奨事項", "はい - 簡潔な推奨事項", "いいえ"]
    required: true

# ======== 進捗管理プロセス ========

progress_tracking_steps:
  1_status_monitoring:
    name: "ステータス監視・記録"
    phases:
      - "チケットの作業状況、担当者の活動履歴、システムログを継続的に監視・自動記録"
      - "ステータス変更、マイルストーン到達、期限経過を検出し、タイムスタンプ付きで詳細記録"
      - "進捗データの整合性確認、履歴の完全性保証、監査証跡の確実な保存"
    quality_standards:
      - "進捗記録の精度100%（データ欠損・改ざんゼロ）"
      - "リアルタイム性の確保（5分以内のステータス反映）"
      - "履歴追跡の完全性（全変更の記録と復元可能性）"
  
  2_analysis_prediction:
    name: "分析・予測・意思決定支援"
    phases:
      - "進捗パターン分析による完了予測、リスク評価、必要リソースの動的算出"
      - "類似チケットとの比較分析による処理効率評価、ベストプラクティス抽出"
      - "ボトルネック特定、改善提案、予防策の自動生成と実行可能性評価"
    integration_points:
      - "プロジェクト管理ツールとの進捗データ双方向同期"
      - "リソース管理システムからの稼働情報・スキル情報取得"
      - "予測分析エンジンとの連携による高精度な完了予測"

# ======== 進捗管理ワークフロー ========

progress_tracking_workflow:
  phase_1:
    - name: "現状分析実行"
      action: "analyze_current_state"
      description: "最新の進捗状況と作業履歴の包括的分析"
      mandatory: true
    
    - name: "マイルストーン評価"
      action: "evaluate_milestones"
      description: "重要な節目の達成度評価と次段階準備"
      mandatory: true
    
    - name: "リスク・課題特定"
      action: "identify_risks"
      description: "潜在的問題の早期発見と影響度評価"
      mandatory: true

  phase_2:
    - name: "ステークホルダー報告"
      action: "generate_reports"
      description: "関係者向けの適切な進捗報告資料作成"
      mandatory: true
    
    - name: "フォローアップ設定"
      action: "setup_followup"
      description: "自動追跡とアラート設定の最適化"
      mandatory: true
    
    - name: "改善アクション実行"
      action: "execute_improvements"
      description: "特定された問題への対策実行と効果測定"
      mandatory: true

# ======== テンプレート ========

progress_tracking_template: |
  ---
  file_type: "progress_report"
  ticket_id: "{{ticket_id}}"
  scope: "single_ticket"
  generated_at: "{{meta.timestamp}}"
  domain: "ticket_management"
  agent: "TicketManagement"
  ---
  # 進捗管理レポート - {{meta.timestamp}}
  
  ## 🎫 チケット概要
  **チケットID**: {{ticket_id}}
  **会社名**: {{ticket.company_name}}
  **チケットパス**: tickets/{{ticket.company_name}}/{{ticket.status_folder}}/{{ticket.folder_name}}
  **現在のステータス**: {{current_status}}
  **最終更新**: {{meta.timestamp}}
  **追跡開始日**: {{tracking.start_date}}
  
  ### チケット内ファイル構成（統一規則・フロントマター付き）
  
  #### 進捗管理用フロントマター更新
  
  ##### README.md（進捗状況を反映）
  ```yaml
  ---
  file_type: "ticket_summary"
  ticket_id: "{{ticket_id}}"
  status: "{{current_status}}"
  update_date: "{{meta.timestamp:YYYY-MM-DD}}"
  progress_percentage: "{{completion_percentage}}"
  last_action: "{{latest_update_summary}}"
  next_action: "{{next_steps}}"
  assigned_to: "{{current_assignee}}"
  ---
  ```
  
  ##### response.md（進捗に応じて更新）
  ```yaml
  ---
  file_type: "response"
  ticket_id: "{{ticket_id}}"
  responder: "{{responder_name}}"
  response_date: "{{meta.timestamp:YYYY-MM-DD}}"
  status: "進捗報告"
  resolution_status: "{{tracking.current_resolution_status}}"
  progress_note: "{{progress_summary}}"
  ---
  ```
  
  ## 📊 進捗状況
  
  ### 完了度
  - **全体進捗**: {{completion_percentage}}%
  - **予定完了度**: {{tracking.expected_progress}}%
  - **進捗偏差**: {{tracking.progress_variance}}%
  - **トレンド**: {{tracking.progress_trend}}
  
  ### マイルストーン達成状況
  {{#each milestones}}
  - **{{this.name}}**: {{this.status}} ({{this.completion_date}})
  {{/each}}
  
  ## 📝 作業詳細
  
  ### 最新の作業内容
  {{progress_update}}
  
  ### 完了事項
  {{#each completed_tasks}}
  - ✅ {{this.description}} ({{this.completion_date}})
  {{/each}}
  
  ### 進行中の作業
  {{#each ongoing_tasks}}
  - 🔄 {{this.description}} (進捗: {{this.progress}}%)
  {{/each}}
  
  ## 🧭 原因・解決
  
  ### 原因（現時点の仮説/確定）
  {{root_cause}}
  
  ### 解決方法（実施手順・設定値）
  {{resolution_steps}}
  
  ### 検証結果・顧客確認
  {{verification_notes}}
  
  ## ⚠️ 課題・ブロッカー
  
  ### 現在の課題
  {{issues_blockers}}
  
  ### 影響度分析
  - **スケジュール影響**: {{analysis.schedule_impact}}
  - **品質影響**: {{analysis.quality_impact}}
  - **コスト影響**: {{analysis.cost_impact}}
  - **リスクレベル**: {{analysis.risk_level}}
  
  ## 🔮 予測・見通し
  
  ### 完了予測
  - **予測完了日**: {{estimated_completion}}
  - **信頼度**: {{prediction.confidence_level}}%
  - **遅延リスク**: {{prediction.delay_probability}}%
  - **追加リソース要否**: {{prediction.additional_resources}}
  
  ### 次のマイルストーン
  - **次の節目**: {{next_milestone.name}}
  - **予定達成日**: {{next_milestone.target_date}}
  - **準備状況**: {{next_milestone.readiness}}%
  - **必要アクション**: {{next_milestone.required_actions}}
  
  ## 🎯 次のアクション
  
  ### 即座対応（24時間以内）
  {{next_actions}}
  
  ### 短期計画（3日以内）
  {{#each short_term_actions}}
  - {{this.description}} (担当: {{this.assignee}})
  {{/each}}
  
  ### 中期計画（1週間以内）
  {{#each medium_term_actions}}
  - {{this.description}} (期限: {{this.deadline}})
  {{/each}}
  
  ## 📞 コミュニケーション
  
  ### ステークホルダー通知
  - **顧客報告**: {{communication.customer_update}}
  - **チーム共有**: {{communication.team_update}}
  - **管理層報告**: {{communication.management_update}}
  
  ### フォローアップスケジュール
  - **次回確認**: {{followup.next_check}}
  - **週次レビュー**: {{followup.weekly_review}}
  - **完了確認**: {{followup.completion_check}}
  
  ## 📈 パフォーマンス指標
  
  ### 効率性指標
  - **処理速度**: {{metrics.processing_speed}}
  - **品質スコア**: {{metrics.quality_score}}
  - **顧客満足度**: {{metrics.customer_satisfaction}}
  - **チーム効率**: {{metrics.team_efficiency}}
  
  ### 改善提案
  - **効率化**: {{suggestions.efficiency}}
  - **品質向上**: {{suggestions.quality}}
  - **プロセス改善**: {{suggestions.process}}
  
  ---
  **文書情報**
  - 作成日: {{meta.timestamp}}
  - ドメイン: ticket_management
  - エージェント: SlackTicketAgent
  - 分類: 進捗管理・追跡

# 互換テンプレート（元の名称を維持）
tracking_template: |
  ---
  file_type: "progress_report"
  ticket_id: "{{ticket_id}}"
  scope: "single_ticket"
  generated_at: "{{meta.timestamp}}"
  domain: "ticket_management"
  agent: "TicketManagement"
  ---
  # 進捗管理レポート - {{meta.timestamp}}
  
  ## 🎫 チケット概要
  **チケットID**: {{ticket_id}}
  **会社名**: {{ticket.company_name}}
  **チケットパス**: tickets/{{ticket.company_name}}/{{ticket.status_folder}}/{{ticket.folder_name}}
  **現在のステータス**: {{current_status}}
  **最終更新**: {{meta.timestamp}}
  **追跡開始日**: {{tracking.start_date}}
  
  ### チケット内ファイル構成（統一規則・フロントマター付き）
  
  #### 進捗管理用フロントマター更新
  
  ##### README.md（進捗状況を反映）
  ```yaml
  ---
  file_type: "ticket_summary"
  ticket_id: "{{ticket_id}}"
  status: "{{current_status}}"
  update_date: "{{meta.timestamp:YYYY-MM-DD}}"
  progress_percentage: "{{completion_percentage}}"
  last_action: "{{latest_update_summary}}"
  next_action: "{{next_steps}}"
  assigned_to: "{{current_assignee}}"
  ---
  ```
  
  ##### response.md（進捗に応じて更新）
  ```yaml
  ---
  file_type: "response"
  ticket_id: "{{ticket_id}}"
  responder: "{{responder_name}}"
  response_date: "{{meta.timestamp:YYYY-MM-DD}}"
  status: "進捗報告"
  resolution_status: "{{tracking.current_resolution_status}}"
  progress_note: "{{progress_summary}}"
  ---
  ```
  
  ## 📊 進捗状況
  
  ### 完了度
  - **全体進捗**: {{completion_percentage}}%
  - **予定完了度**: {{tracking.expected_progress}}%
  - **進捗偏差**: {{tracking.progress_variance}}%
  - **トレンド**: {{tracking.progress_trend}}
  
  ### マイルストーン達成状況
  {{#each milestones}}
  - **{{this.name}}**: {{this.status}} ({{this.completion_date}})
  {{/each}}
  
  ## 📝 作業詳細
  
  ### 最新の作業内容
  {{progress_update}}
  
  ### 完了事項
  {{#each completed_tasks}}
  - ✅ {{this.description}} ({{this.completion_date}})
  {{/each}}
  
  ### 進行中の作業
  {{#each ongoing_tasks}}
  - 🔄 {{this.description}} (進捗: {{this.progress}}%)
  {{/each}}
  
  ## 🧭 原因・解決
  
  ### 原因（現時点の仮説/確定）
  {{root_cause}}
  
  ### 解決方法（実施手順・設定値）
  {{resolution_steps}}
  
  ### 検証結果・顧客確認
  {{verification_notes}}
  
  ## ⚠️ 課題・ブロッカー
  
  ### 現在の課題
  {{issues_blockers}}
  
  ### 影響度分析
  - **スケジュール影響**: {{analysis.schedule_impact}}
  - **品質影響**: {{analysis.quality_impact}}
  - **コスト影響**: {{analysis.cost_impact}}
  - **リスクレベル**: {{analysis.risk_level}}
  
  ## 🔮 予測・見通し
  
  ### 完了予測
  - **予測完了日**: {{estimated_completion}}
  - **信頼度**: {{prediction.confidence_level}}%
  - **遅延リスク**: {{prediction.delay_probability}}%
  - **追加リソース要否**: {{prediction.additional_resources}}
  
  ### 次のマイルストーン
  - **次の節目**: {{next_milestone.name}}
  - **予定達成日**: {{next_milestone.target_date}}
  - **準備状況**: {{next_milestone.readiness}}%
  - **必要アクション**: {{next_milestone.required_actions}}
  
  ## 🎯 次のアクション
  
  ### 即座対応（24時間以内）
  {{next_actions}}
  
  ### 短期計画（3日以内）
  {{#each short_term_actions}}
  - {{this.description}} (担当: {{this.assignee}})
  {{/each}}
  
  ### 中期計画（1週間以内）
  {{#each medium_term_actions}}
  - {{this.description}} (期限: {{this.deadline}})
  {{/each}}
  
  ## 📞 コミュニケーション
  
  ### ステークホルダー通知
  - **顧客報告**: {{communication.customer_update}}
  - **チーム共有**: {{communication.team_update}}
  - **管理層報告**: {{communication.management_update}}
  
  ### フォローアップスケジュール
  - **次回確認**: {{followup.next_check}}
  - **週次レビュー**: {{followup.weekly_review}}
  - **完了確認**: {{followup.completion_check}}
  
  ## 📈 パフォーマンス指標
  
  ### 効率性指標
  - **処理速度**: {{metrics.processing_speed}}
  - **品質スコア**: {{metrics.quality_score}}
  - **顧客満足度**: {{metrics.customer_satisfaction}}
  - **チーム効率**: {{metrics.team_efficiency}}
  
  ### 改善提案
  - **効率化**: {{suggestions.efficiency}}
  - **品質向上**: {{suggestions.quality}}
  - **プロセス改善**: {{suggestions.process}}
  
  ---
  **文書情報**
  - 作成日: {{meta.timestamp}}
  - ドメイン: ticket_management
  - エージェント: SlackTicketAgent
  - 分類: 進捗管理・追跡
# ======== 残チケット集約・一括進捗管理テンプレート ========

bulk_progress_template: |
  ---
  file_type: "bulk_progress_report"
  report_scope: "{{report_scope}}"
  target_status: "{{target_status}}"
  priority_filter: "{{priority_filter}}"
  company_filter: "{{company_filter}}"
  generated_at: "{{meta.timestamp}}"
  domain: "ticket_management"
  agent: "TicketManagement"
  ---
  # 残チケット集約・進捗管理レポート - {{meta.timestamp}}

  ## チケット一覧（表形式）

  ### 完了チケット（解決済/クローズ）
  | Ticket ID | タイトル | 会社 | 優先度 | カテゴリ | 担当 | 作成日 | 解決日 | ステータス | パス |
  |---|---|---|---|---|---|---|---|---|---|
  {{#each tickets.completed}}
  | {{this.ticket_id}} | {{this.title}} | {{this.company}} | {{this.priority}} | {{this.category}} | {{this.assigned_to}} | {{this.create_date}} | {{this.resolution_date}} | {{this.status}} | {{this.path}} |
  {{/each}}

  ### 未完了チケット（新規/対応中/保留）
  | Ticket ID | タイトル | 会社 | 優先度 | カテゴリ | 担当 | 作成日 | 更新日 | 期限 | ステータス | 経過日数 | パス |
  |---|---|---|---|---|---|---|---|---|---|---|---|
  {{#each tickets.open}}
  | {{this.ticket_id}} | {{this.title}} | {{this.company}} | {{this.priority}} | {{this.category}} | {{this.assigned_to}} | {{this.create_date}} | {{this.update_date}} | {{this.due_date}} | {{this.status}} | {{this.age_days}} | {{this.path}} |
  {{/each}}

  - 分類: 進捗管理・追跡
  
  ## 📋 レポート概要
  **レポート範囲**: {{report_scope}}
  **対象ステータス**: {{target_status}}
  **優先度フィルタ**: {{priority_filter}}
  **会社フィルタ**: {{company_filter}}
  **レポートタイプ**: {{report_type}}
  **生成日時**: {{meta.timestamp}}
  **レポート作成者**: {{reporter_name}}
  
  ## 🎯 全体サマリー
  
  ### チケット統計
  - **未完了チケット総数**: {{summary.total_incomplete}}件
  - **緊急対応必要**: {{summary.urgent_count}}件
  - **遅延リスク**: {{summary.delayed_risk}}件
  - **今日期限**: {{summary.due_today}}件
  - **今週期限**: {{summary.due_this_week}}件
  
  ### 会社別内訳
  {{#each company_breakdown}}
  - **{{this.company_name}}**: {{this.total_tickets}}件
    - 緊急: {{this.urgent}}件 | 高: {{this.high}}件 | 中: {{this.medium}}件 | 低: {{this.low}}件
    - 遅延リスク: {{this.risk_count}}件
  {{/each}}
  
  ### ステータス別内訳
  {{#each status_breakdown}}
  - **{{this.status}}**: {{this.count}}件 ({{this.percentage}}%)
  {{/each}}
  
  ## 🚨 緊急対応必要案件
  
  {{#each urgent_tickets}}
  ### {{this.ticket_id}} - {{this.title}}
  - **会社**: {{this.company}}
  - **優先度**: {{this.priority}}
  - **ステータス**: {{this.status}}
  - **期限**: {{this.due_date}}
  - **経過日数**: {{this.days_elapsed}}日
  - **担当者**: {{this.assigned_to}}
  - **課題**: {{this.current_issues}}
  - **推奨アクション**: {{this.recommended_action}}
  
  ---
  {{/each}}
  
  ## ⚠️ 遅延リスク案件
  
  {{#each risk_tickets}}
  ### {{this.ticket_id}} - {{this.title}}
  - **会社**: {{this.company}}
  - **優先度**: {{this.priority}}
  - **ステータス**: {{this.status}}
  - **進捗率**: {{this.progress_percentage}}%
  - **予定完了**: {{this.estimated_completion}}
  - **遅延予測**: {{this.delay_prediction}}
  - **リスク要因**: {{this.risk_factors}}
  - **対策**: {{this.mitigation_plan}}
  
  ---
  {{/each}}
  
  ## 📊 進行中案件詳細
  
  {{#each active_tickets}}
  ### {{this.ticket_id}} - {{this.title}}
  - **会社**: {{this.company}}
  - **優先度**: {{this.priority}}
  - **ステータス**: {{this.status}}
  - **進捗率**: {{this.progress_percentage}}%
  - **担当者**: {{this.assigned_to}}
  - **最終更新**: {{this.last_update}}
  - **次のアクション**: {{this.next_action}}
  - **完了予定**: {{this.estimated_completion}}
  
  {{#if this.recent_updates}}
  **最新の進捗**:
  {{this.recent_updates}}
  {{/if}}
  
  {{#if this.blockers}}
  **現在のブロッカー**:
  {{this.blockers}}
  {{/if}}
  
  ---
  {{/each}}
  
  ## 💡 推奨アクション・フォローアップ
  
  ### 即座対応（今日中）
  {{#each immediate_actions}}
  - **{{this.ticket_id}}**: {{this.action}} (担当: {{this.assignee}})
  {{/each}}
  
  ### 短期対応（3日以内）
  {{#each short_term_actions}}
  - **{{this.ticket_id}}**: {{this.action}} (期限: {{this.deadline}})
  {{/each}}
  
  ### 中期対応（1週間以内）
  {{#each medium_term_actions}}
  - **{{this.ticket_id}}**: {{this.action}} (計画: {{this.plan}})
  {{/each}}
  
  ## 📈 パフォーマンス分析
  
  ### 効率性指標
  - **平均解決日数**: {{metrics.avg_resolution_days}}日
  - **SLA達成率**: {{metrics.sla_achievement}}%
  - **顧客満足度**: {{metrics.customer_satisfaction}}/5.0
  - **チーム稼働率**: {{metrics.team_utilization}}%
  
  ### 改善提案
  - **プロセス改善**: {{improvement.process}}
  - **リソース最適化**: {{improvement.resource}}
  - **品質向上**: {{improvement.quality}}
  - **予防策**: {{improvement.prevention}}
  
  ## 🔄 定期フォローアップ計画
  
  ### 日次チェック項目
  - 新規チケット確認
  - 緊急案件ステータス更新
  - 期限近接チケットの進捗確認
  - リスクチケットの状況監視
  
  ### 週次レビュー項目
  - 全チケット進捗総合評価
  - リソース配分の見直し
  - プロセス改善点の検討
  - 顧客フィードバックの収集
  
  ## 📞 エスカレーション・連絡先
  
  ### 緊急時連絡先
  {{#each escalation_contacts}}
  - **{{this.level}}**: {{this.contact_person}} ({{this.contact_method}})
  {{/each}}
  
  ### 会社別担当者
  {{#each company_contacts}}
  - **{{this.company}}**: {{this.primary_contact}} / {{this.backup_contact}}
  {{/each}}
  
  ---
  **レポート情報**
  - 作成日時: {{meta.timestamp}}
  - ドメイン: ticket_management
  - エージェント: SlackTicketAgent
  - 分類: 残チケット集約・進捗管理
  - 次回レポート予定: {{next_report_schedule}}

# ======== 内容理解ベース抽出ガイドライン（テンプレート） ========

bulk_progress_extraction_guidelines_template: |
  ## 原因/解決方法のセマンティック要約ポリシー
  - 見出し語（原因/解決策/修正方法 など）や装飾は除去し、本文の因果と処置を1行に要約。
  - 見出しが無い場合も本文・responseから因果関係と実施手段（動詞+対象+手段）を推定して要約。
  - 箇条書きは先頭2項目を統合要約（最大160文字）。
  - ノイズ（「…の提供 - …」等の見出し断片）は除去。原因=解決方法となる場合はresponse 本文で補完し差異を確保。

# ======== エラーハンドリング ========

error_handling:
  data_inconsistency:
    message: "進捗データに不整合が検出されました"
    recovery_actions:
      - "データ整合性の自動修復試行"
      - "手動確認による正確な状況把握"
  
  communication_failure:
    message: "ステークホルダーへの通知に失敗しました"
    recovery_actions:
      - "代替通信手段での再送信"
      - "緊急連絡先への直接連絡"

# ======== 設定 ========

progress_tracking_settings:
  real_time_monitoring: true
  automated_reporting: true
  predictive_analytics: true
  stakeholder_notifications: true

# ======== 統合ポイント ========

integration_points:
  reporting_system:
    trigger: "重要マイルストーン到達"
    action: "call 04_reporting_dashboard.mdc => generate_milestone_report"
  
  escalation_system:
    trigger: "重大遅延検出"
    action: "automated_escalation_workflow"

# ======== 品質保証 ========

quality_assurance:
  mandatory_checks:
    - "進捗データの正確性・完全性確認"
    - "予測精度の検証・校正実施"
    - "コミュニケーション配信の確実性確認"

# ======== 成功メトリクス ========

success_metrics:
  - "進捗追跡精度 > 98%"
  - "完了予測精度 > 85%"
  - "ステークホルダー満足度 > 4.2/5.0"
  - "問題早期発見率 > 90%"
