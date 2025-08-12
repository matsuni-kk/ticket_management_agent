---
name: 04_reporting
description: レポート生成・ダッシュボード・分析システム
---

# ==========================================================
# 04_reporting_dashboard.mdc - レポート生成・ダッシュボード・分析システム
# ==========================================================

path_reference: "ticket_management_paths.mdc"

# ======== レポート・ダッシュボードシステム統合エージェント ========

system_capabilities:
  comprehensive_reporting: "日次・週次・月次の包括的レポート自動生成により、チケット処理状況、チーム パフォーマンス、顧客満足度を可視化する多階層レポート機能"
  interactive_dashboard: "リアルタイムデータ更新、ドリルダウン分析、カスタムフィルターを備えた直感的なダッシュボードとBI機能"
  trend_analysis: "長期トレンド分析、季節変動検出、異常値識別による戦略的意思決定支援とパフォーマンス最適化機能"
  stakeholder_customization: "経営層・管理層・現場チーム向けの役割別カスタマイズレポートと適切な詳細度での情報提供機能"
  predictive_insights: "機械学習による需要予測、リスク予測、リソース最適化提案を含む先読み分析とインサイト提供機能"
  automated_distribution: "定期配信、異常値アラート、カスタム通知による関係者への適時適切な情報配信とコミュニケーション支援機能"

# ======== Phase 1: データ集計・分析フェーズ ========

phase_1_description: |
  多次元データ集計と高度な分析により、チケット管理の全体像を把握します。
  処理状況、パフォーマンス指標、顧客満足度を統合的に分析し、
  客観的で実用的なインサイトを抽出・整理します。

# ======== Phase 2: 可視化・配信フェーズ ========

phase_2_description: |
  分析結果の効果的な可視化と適切なステークホルダーへの配信を実行します。
  役割に応じたレポート生成、インタラクティブダッシュボード構築により
  迅速な意思決定と継続的改善を支援します。

# ======== 統合オプション質問 ========

reporting_dashboard_questions:
  - key: "report_type"
    prompt: "生成するレポートの種類を選択してください："
    type: "select"
    options: ["日次レポート", "週次レポート", "月次レポート", "カスタム期間", "リアルタイムダッシュボード", "特定分析レポート"]
    required: true

  - key: "date_range"
    prompt: "対象期間を指定してください："
    type: "text"
    required: true
    placeholder: "例：2024-01-01 to 2024-01-31, 直近7日間, 今月, 前月"

  - key: "target_audience"
    prompt: "レポートの対象者を選択してください："
    type: "select"
    options: ["経営層", "管理層", "チームリーダー", "現場担当者", "顧客", "全社共有"]
    required: true

  - key: "focus_areas"
    prompt: "重点分析領域を選択してください（複数選択可）："
    type: "multiselect"
    options: ["処理効率", "顧客満足度", "SLA遵守", "チーム パフォーマンス", "コスト分析", "品質指標", "予測分析"]
    required: false

  - key: "specific_metrics"
    prompt: "特定の測定指標があれば入力してください："
    type: "text"
    required: false
    placeholder: "例：平均解決時間, 初回解決率, 顧客満足度スコア, チケット再発率"

  - key: "comparison_period"
    prompt: "比較対象期間があれば指定してください："
    type: "text"
    required: false
    placeholder: "例：前月同期, 昨年同期, 前四半期"

  - key: "custom_filters"
    prompt: "カスタムフィルター条件があれば入力してください："
    type: "multiline"
    required: false
    placeholder: "例：優先度=高のみ, 特定顧客のみ, 技術サポートカテゴリのみ"

# ======== レポート・ダッシュボードプロセス ========

reporting_dashboard_steps:
  1_data_aggregation:
    name: "データ集計・前処理"
    phases:
      - "全チケットデータベースからの包括的データ抽出、クレンジング、正規化による高品質データセット構築"
      - "処理時間、解決率、満足度等の主要KPIの精密算出と統計的検証による信頼性確保"
      - "時系列分析、相関分析、異常値検出による多角的データ分析と洞察抽出"
    quality_standards:
      - "データ完全性100%（欠損・重複・異常値の完全除去）"
      - "計算精度99.9%以上（財務レベルの正確性）"
      - "処理速度最適化（大容量データの3分以内処理）"
  
  2_visualization_insights:
    name: "可視化・インサイト生成"
    phases:
      - "トレンドグラフ、ヒートマップ、散布図等の最適な可視化手法選択と美的・直感的表現の実現"
      - "統計的有意性検定、パターン認識、因果関係分析による科学的インサイト抽出"
      - "予測モデリング、シナリオ分析、リスク評価による戦略的示唆と実行可能な推奨事項の提供"
    integration_points:
      - "BIツール（Tableau、Power BI等）との連携によるインタラクティブ可視化"
      - "予測分析エンジンとの統合による高精度な将来予測"
      - "外部データソース（市場データ、競合情報等）との融合分析"

# ======== レポート・ダッシュボードワークフロー ========

reporting_dashboard_workflow:
  phase_1:
    - name: "データソース統合"
      action: "integrate_data_sources"
      description: "複数システムからのデータ統合と品質保証"
      mandatory: true
    
    - name: "KPI算出実行"
      action: "calculate_kpis"
      description: "重要業績指標の精密算出と検証"
      mandatory: true
    
    - name: "統計分析実行"
      action: "perform_analytics"
      description: "高度統計分析とパターン認識"
      mandatory: true

  phase_2:
    - name: "レポート生成"
      action: "generate_reports"
      description: "対象者別カスタマイズレポート作成"
      mandatory: true
    
    - name: "ダッシュボード構築"
      action: "build_dashboard"
      description: "インタラクティブダッシュボード構築"
      mandatory: true
    
    - name: "配信・共有実行"
      action: "distribute_reports"
      description: "適切な関係者への自動配信と共有"
      mandatory: true

# ======== テンプレート ========

reporting_dashboard_template: |
  ---
  file_type: "analysis_report"
  report_type: "{{report_type}}"
  date_range: "{{date_range}}"
  target_audience: "{{target_audience}}"
  generated_at: "{{meta.timestamp}}"
  domain: "ticket_management"
  agent: "TicketManagement"
  ---
  # チケット管理分析レポート - {{meta.timestamp}}
  
  ## 📊 エグゼクティブサマリー
  **期間**: {{date_range}}
  **対象**: {{target_audience}}
  **レポート種別**: {{report_type}}
  **生成日時**: {{meta.timestamp}}
  **レポート保存先**: {{docs_root}}/reports/{{meta.date:YYYY-MM-DD}}_{{report_type}}.md
  
  ### 主要指標サマリー
  - **総チケット数**: {{summary.total_tickets}}件 ({{summary.ticket_change}}%)
  - **平均解決時間**: {{summary.avg_resolution_time}}時間 ({{summary.resolution_change}}%)
  - **SLA遵守率**: {{summary.sla_compliance}}% ({{summary.sla_change}}%)
  - **顧客満足度**: {{summary.customer_satisfaction}}/5.0 ({{summary.satisfaction_change}})
  
  ## 📈 パフォーマンス分析
  
  ### チケット処理状況
  | 指標 | 当期 | 前期 | 変化率 | 目標値 | 達成度 |
  |------|------|------|--------|--------|--------|
  | 新規受信 | {{metrics.new_tickets}} | {{metrics.prev_new_tickets}} | {{metrics.new_change}}% | {{targets.new_target}} | {{metrics.new_achievement}}% |
  | 解決完了 | {{metrics.resolved_tickets}} | {{metrics.prev_resolved}} | {{metrics.resolved_change}}% | {{targets.resolved_target}} | {{metrics.resolved_achievement}}% |
  | 進行中 | {{metrics.in_progress}} | {{metrics.prev_in_progress}} | {{metrics.progress_change}}% | {{targets.progress_target}} | {{metrics.progress_achievement}}% |
  | バックログ | {{metrics.backlog}} | {{metrics.prev_backlog}} | {{metrics.backlog_change}}% | {{targets.backlog_target}} | {{metrics.backlog_achievement}}% |
  
  ### 効率性指標
  - **初回解決率**: {{efficiency.first_call_resolution}}% (目標: {{targets.fcr_target}}%)
  - **平均応答時間**: {{efficiency.avg_response_time}}分 (目標: {{targets.response_target}}分)
  - **エスカレーション率**: {{efficiency.escalation_rate}}% (目標: {{targets.escalation_target}}%以下)
  - **再オープン率**: {{efficiency.reopen_rate}}% (目標: {{targets.reopen_target}}%以下)
  
  ## 🎯 カテゴリ別分析
  
  ### 会社別処理状況
  {{#each companies}}
  #### {{this.name}}
  - **チケット数**: {{this.count}}件 ({{this.percentage}}%)
  - **完了チケット**: {{this.completed_count}}件
  - **進行中チケット**: {{this.in_progress_count}}件
  - **平均解決時間**: {{this.avg_resolution}}時間
  - **満足度**: {{this.satisfaction}}/5.0
  - **チケットパス**: tickets/{{this.name}}/
  - **ファイル構成**: inquiry.md, response.md, README.md, technical_*.md（統一規則適用）
  - **フロントマター**: 全ファイルにfile_type、ticket_id等の標準メタデータ付与
  {{/each}}
  
  ### 分類別処理状況
  {{#each categories}}
  #### {{this.name}}
  - **チケット数**: {{this.count}}件 ({{this.percentage}}%)
  - **平均解決時間**: {{this.avg_resolution}}時間
  - **満足度**: {{this.satisfaction}}/5.0
  - **主要課題**: {{this.main_issues}}
  {{/each}}
  
  ### 優先度別分析
  | 優先度 | チケット数 | 平均解決時間 | SLA遵守率 | 満足度 |
  |--------|------------|--------------|-----------|---------|
  | 緊急 | {{priority.critical.count}} | {{priority.critical.resolution}} | {{priority.critical.sla}}% | {{priority.critical.satisfaction}} |
  | 高 | {{priority.high.count}} | {{priority.high.resolution}} | {{priority.high.sla}}% | {{priority.high.satisfaction}} |
  | 中 | {{priority.medium.count}} | {{priority.medium.resolution}} | {{priority.medium.sla}}% | {{priority.medium.satisfaction}} |
  | 低 | {{priority.low.count}} | {{priority.low.resolution}} | {{priority.low.sla}}% | {{priority.low.satisfaction}} |
  
  ## 👥 チーム パフォーマンス
  
  ### 担当者別実績
  {{#each team_members}}
  #### {{this.name}}
  - **処理件数**: {{this.handled_tickets}}件
  - **平均解決時間**: {{this.avg_resolution}}時間
  - **品質スコア**: {{this.quality_score}}/10
  - **顧客評価**: {{this.customer_rating}}/5.0
  - **効率性ランク**: {{this.efficiency_rank}}/{{total_members}}位
  {{/each}}
  
  ### チーム全体指標
  - **チーム効率性**: {{team.overall_efficiency}}% (前期比: {{team.efficiency_change}}%)
  - **スキル成長率**: {{team.skill_growth}}% (研修・経験による向上)
  - **チーム満足度**: {{team.member_satisfaction}}/5.0
  - **離職リスク**: {{team.turnover_risk}}% (予測値)
  
  ## 💰 コスト・ROI分析
  
  ### 運用コスト
  - **総運用コスト**: ¥{{costs.total_cost:number}} (前期比: {{costs.cost_change}}%)
  - **チケット単価**: ¥{{costs.cost_per_ticket:number}}
  - **時間単価**: ¥{{costs.cost_per_hour:number}}
  - **効率化による削減**: ¥{{costs.efficiency_savings:number}}
  
  ### ROI指標
  - **顧客満足度ROI**: {{roi.customer_satisfaction}}%
  - **処理効率化ROI**: {{roi.efficiency_improvement}}%
  - **コスト削減効果**: ¥{{roi.cost_reduction:number}}
  - **総合ROI**: {{roi.overall_roi}}%
  
  ## 🔮 予測・トレンド分析
  
  ### 短期予測（来月）
  - **予想チケット数**: {{forecast.next_month_tickets}}件 (±{{forecast.ticket_variance}}%)
  - **予想平均解決時間**: {{forecast.next_resolution_time}}時間
  - **リソース需要**: {{forecast.resource_demand}}% (現在比)
  - **注意事項**: {{forecast.next_month_alerts}}
  
  ### 長期トレンド（四半期）
  - **成長トレンド**: {{trends.growth_pattern}}
  - **季節性**: {{trends.seasonality}}
  - **改善方向**: {{trends.improvement_areas}}
  - **投資推奨**: {{trends.investment_recommendations}}
  
  ## ⚠️ 課題・改善提案
  
  ### 特定された課題
  {{#each issues}}
  #### {{this.category}}: {{this.title}}
  - **影響度**: {{this.impact_level}}
  - **発生頻度**: {{this.frequency}}
  - **コスト影響**: ¥{{this.cost_impact:number}}
  - **推奨対策**: {{this.recommended_action}}
  - **実施期限**: {{this.action_deadline}}
  {{/each}}
  
  ### 改善アクションプラン
  {{#each improvement_actions}}
  #### {{this.priority}}優先度: {{this.title}}
  - **期待効果**: {{this.expected_benefit}}
  - **実施コスト**: ¥{{this.implementation_cost:number}}
  - **ROI期間**: {{this.roi_period}}ヶ月
  - **担当部門**: {{this.responsible_department}}
  - **開始予定**: {{this.start_date}}
  {{/each}}
  
  ## 🎖️ 成功事例・ベストプラクティス
  
  ### 優秀事例
  {{#each success_stories}}
  #### {{this.title}}
  - **概要**: {{this.description}}
  - **成果**: {{this.achievement}}
  - **適用可能性**: {{this.applicability}}
  - **水平展開**: {{this.horizontal_deployment}}
  {{/each}}
  
  ## 📅 次期アクション・フォローアップ
  
  ### 即座実行項目（1週間以内）
  {{#each immediate_actions}}
  - {{this.description}} (担当: {{this.assignee}})
  {{/each}}
  
  ### 短期改善項目（1ヶ月以内）
  {{#each short_term_improvements}}
  - {{this.description}} (期限: {{this.deadline}})
  {{/each}}
  
  ### 長期戦略項目（四半期内）
  {{#each strategic_initiatives}}
  - {{this.description}} (ROI: {{this.expected_roi}}%)
  {{/each}}
  
  ---
  **文書情報**
  - 作成日: {{meta.timestamp}}
  - ドメイン: ticket_management
  - エージェント: SlackTicketAgent
  - 分類: レポート・分析・ダッシュボード

reporting_template: |
  ---
  file_type: "analysis_report"
  report_type: "{{report_type}}"
  date_range: "{{date_range}}"
  target_audience: "{{target_audience}}"
  generated_at: "{{meta.timestamp}}"
  domain: "ticket_management"
  agent: "TicketManagement"
  ---
  # チケット管理分析レポート - {{meta.timestamp}}
  
  ## 📊 エグゼクティブサマリー
  **期間**: {{date_range}}
  **対象**: {{target_audience}}
  **レポート種別**: {{report_type}}
  **生成日時**: {{meta.timestamp}}
  **レポート保存先**: {{docs_root}}/reports/{{meta.date:YYYY-MM-DD}}_{{report_type}}.md
  
  ### 主要指標サマリー
  - **総チケット数**: {{summary.total_tickets}}件 ({{summary.ticket_change}}%)
  - **平均解決時間**: {{summary.avg_resolution_time}}時間 ({{summary.resolution_change}}%)
  - **SLA遵守率**: {{summary.sla_compliance}}% ({{summary.sla_change}}%)
  - **顧客満足度**: {{summary.customer_satisfaction}}/5.0 ({{summary.satisfaction_change}})

# ======== エラーハンドリング ========

error_handling:
  data_quality_issue:
    message: "データ品質に問題が検出されました"
    recovery_actions:
      - "データクレンジングの再実行"
      - "手動データ検証の実施"
  
  visualization_error:
    message: "可視化処理でエラーが発生しました"
    recovery_actions:
      - "代替可視化手法への切り替え"
      - "簡易版レポートの生成"

# ======== 設定 ========

reporting_dashboard_settings:
  automated_generation: true
  real_time_updates: true
  interactive_features: true
  multi_format_export: true

# ======== 統合ポイント ========

integration_points:
  automation_system:
    trigger: "異常値検出"
    action: "call 05_automation_rules.mdc => trigger_alert_automation"
  
  external_bi_tools:
    trigger: "レポート完成"
    action: "export_to_bi_platforms"

# ======== 品質保証 ========

quality_assurance:
  mandatory_checks:
    - "データ正確性・完全性の検証"
    - "計算結果の妥当性・一貫性確認"
    - "可視化の明確性・理解しやすさ確認"

# ======== 成功メトリクス ========

success_metrics:
  - "レポート精度 > 99.5%"
  - "生成速度 < 3分"
  - "ユーザー満足度 > 4.5/5.0"
  - "意思決定貢献度 > 85%"
