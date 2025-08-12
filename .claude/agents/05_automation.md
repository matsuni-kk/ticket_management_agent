---
name: 05_automation
description: 自動化ルール・通知・エスカレーションシステム
---

# ==========================================================
# 05_automation_rules.mdc - 自動化ルール・通知・エスカレーションシステム
# ==========================================================

path_reference: "ticket_management_paths.mdc"

# ======== 自動化システム統合エージェント ========

system_capabilities:
  intelligent_automation: "条件ベース・学習ベースの複合的自動化ルールにより、チケット処理の90%以上を人的介入なしで実行する高度自動化機能"
  proactive_monitoring: "システム状況、処理パフォーマンス、異常パターンを24/7監視し、問題を予防的に検出・対処する予測的監視機能"
  smart_notifications: "受信者の役割・優先度・状況に応じた最適なタイミング・チャネル・内容での個別最適化通知配信機能"
  escalation_orchestration: "複雑なエスカレーション階層、条件分岐、例外処理を自動実行する包括的エスカレーション オーケストレーション機能"
  workflow_optimization: "処理パターン学習、ボトルネック特定、リソース最適化による継続的なワークフロー自動改善機能"
  compliance_assurance: "規制要件、社内規定、SLA条件の自動遵守確認と違反時の自動対処によるコンプライアンス保証機能"

# ======== Phase 1: ルール設定・監視フェーズ ========

phase_1_description: |
  包括的な自動化ルールの設定と継続的監視により、効率的なチケット処理を実現します。
  条件ベースのルール実行、パフォーマンス監視、異常検出を通じて
  人的リソースを戦略的業務に集中させ、運用品質を向上させます。

# ======== Phase 2: 通知・エスカレーション実行フェーズ ========

phase_2_description: |
  適時適切な通知配信と段階的エスカレーション実行により、確実な問題解決を保証します。
  ステークホルダーへの最適化された情報提供、自動エスカレーション実行により
  重要な課題の見逃し防止と迅速な意思決定支援を実現します。

# ======== 統合オプション質問 ========

automation_rules_questions:
  - key: "automation_type"
    prompt: "設定する自動化の種類を選択してください："
    type: "select"
    options: ["新規ルール作成", "既存ルール修正", "通知設定", "エスカレーション設定", "全体システム設定", "パフォーマンス最適化"]
    required: true

  - key: "trigger_conditions"
    prompt: "自動化のトリガー条件を詳細に入力してください："
    type: "multiline"
    required: true
    placeholder: "例：優先度=高 AND 経過時間>2時間 AND 応答なし, 顧客=VIP AND ステータス=新規, SLA期限まで4時間以内"

  - key: "automation_actions"
    prompt: "実行する自動化アクションを指定してください："
    type: "multiline"
    required: true
    placeholder: "例：マネージャーに通知, 優先度を緊急に変更, 専門チームに自動割り当て, 顧客にステータス通知"

  - key: "notification_recipients"
    prompt: "通知対象者を指定してください："
    type: "multiline"
    required: false
    placeholder: "例：担当者, チームリーダー, マネージャー, 顧客, 特定個人（田中、山田）"

  - key: "escalation_hierarchy"
    prompt: "エスカレーション階層を設定してください："
    type: "multiline"
    required: false
    placeholder: "例：Level1(担当者)→Level2(リーダー)→Level3(マネージャー)→Level4(役員), 条件別の分岐設定"

  - key: "frequency_settings"
    prompt: "実行頻度・間隔を設定してください："
    type: "text"
    required: false
    placeholder: "例：即座実行, 30分間隔, 毎日9時, 週次月曜日, 月末最終営業日"

  - key: "exception_conditions"
    prompt: "例外条件・停止条件があれば入力してください："
    type: "multiline"
    required: false
    placeholder: "例：休日は実行停止, VIP顧客は別ルール適用, システムメンテナンス中は停止"

# ======== 自動化システムプロセス ========

automation_rules_steps:
  1_rule_configuration:
    name: "ルール設定・検証"
    phases:
      - "複雑な条件分岐、例外処理、パフォーマンス要件を含む包括的自動化ルールの設計・実装・テスト"
      - "既存システムとの整合性確認、競合ルール検出、優先度調整による安定したルール実行環境構築"
      - "セキュリティ・コンプライアンス要件の確認、アクセス権限設定、監査証跡確保による安全な自動化実現"
    quality_standards:
      - "ルール実行精度99.9%以上（誤動作・漏れの完全防止）"
      - "競合・矛盾ルールゼロ（論理的一貫性の保証）"
      - "セキュリティ・コンプライアンス要件100%遵守"
  
  2_execution_monitoring:
    name: "実行・監視・最適化"
    phases:
      - "リアルタイムルール実行、結果監視、パフォーマンス測定による継続的品質保証"
      - "実行パターン分析、効果測定、改善点特定による自動化効果の最大化"
      - "機械学習による実行最適化、予測的調整、適応的改善による自己進化型自動化システム構築"
    integration_points:
      - "チケット管理システムとのリアルタイム連携による即座ルール実行"
      - "通知プラットフォーム（Slack、Email、SMS等）との統合配信"
      - "監視・ログシステムとの連携による包括的実行履歴管理"

# ======== 自動化システムワークフロー ========

automation_rules_workflow:
  phase_1:
    - name: "ルール設計実行"
      action: "design_automation_rules"
      description: "条件・アクション・例外処理の包括設計"
      mandatory: true
    
    - name: "システム整合性確認"
      action: "verify_system_integration"
      description: "既存システムとの連携・競合確認"
      mandatory: true
    
    - name: "テスト・検証実行"
      action: "test_automation_rules"
      description: "シミュレーション環境での動作検証"
      mandatory: true

  phase_2:
    - name: "本番適用実行"
      action: "deploy_automation"
      description: "本番環境への段階的適用と監視"
      mandatory: true
    
    - name: "パフォーマンス監視"
      action: "monitor_performance"
      description: "実行状況・効果・問題点の継続監視"
      mandatory: true
    
    - name: "継続改善実行"
      action: "continuous_improvement"
      description: "学習・分析に基づく自動最適化"
      mandatory: true

# ======== テンプレート ========

automation_rules_template: |
  ---
  file_type: "automation_config"
  automation_type: "{{automation_type}}"
  status: "{{automation.status}}"
  execution_mode: "{{automation.execution_mode}}"
  generated_at: "{{meta.timestamp}}"
  domain: "ticket_management"
  agent: "TicketManagement"
  ---
  # 自動化ルール設定・実行レポート - {{meta.timestamp}}
  
  ## ⚙️ 自動化概要
  **自動化種別**: {{automation_type}}
  **設定日時**: {{meta.timestamp}}
  **ステータス**: {{automation.status}}
  **実行モード**: {{automation.execution_mode}}
  **設定保存先**: {{docs_root}}/configs/automation_{{meta.date:YYYY-MM-DD}}.md
  
  ## 🎯 トリガー条件
  
  ### 基本条件
  ```
  {{trigger_conditions}}
  ```
  
  ### 詳細条件設定
  - **チケット条件**: {{conditions.ticket_criteria}}
  - **会社名条件**: {{conditions.company_criteria}}
  - **チケットパス**: tickets/{{conditions.company_name}}/{{conditions.status_folder}}/
  - **対象ファイル**: inquiry.md, response.md, README.md, technical_*.md（統一規則に基づく）
  - **フロントマター要件**: 全ファイルに標準メタデータ（file_type、ticket_id等）が必須
  - **時間条件**: {{conditions.time_criteria}}
  - **顧客条件**: {{conditions.customer_criteria}}
  - **システム条件**: {{conditions.system_criteria}}
  
  ### 例外・停止条件
  {{exception_conditions}}
  
  ## 🚀 自動化アクション
  
  ### 実行アクション
  {{automation_actions}}
  
  ### アクション詳細
  {{#each actions}}
  #### {{this.name}}
  - **種別**: {{this.type}}
  - **実行タイミング**: {{this.timing}}
  - **対象**: {{this.target}}
  - **パラメータ**: {{this.parameters}}
  - **期待結果**: {{this.expected_outcome}}
  {{/each}}
  
  ## 📢 通知・コミュニケーション
  
  ### 通知対象者
  {{notification_recipients}}
  
  ### 通知設定詳細
  {{#each notifications}}
  #### {{this.recipient_type}}
  - **通知チャネル**: {{this.channels}}
  - **通知タイミング**: {{this.timing}}
  - **通知内容**: {{this.content_template}}
  - **緊急度**: {{this.urgency_level}}
  - **配信頻度**: {{this.frequency}}
  {{/each}}
  
  ## 📈 エスカレーション階層
  
  ### エスカレーション構造
  {{escalation_hierarchy}}
  
  ### 段階別設定
  {{#each escalation_levels}}
  #### Level {{this.level}}: {{this.role}}
  - **エスカレーション条件**: {{this.trigger_condition}}
  - **実行タイミング**: {{this.timing}}
  - **通知方法**: {{this.notification_method}}
  - **権限レベル**: {{this.authority_level}}
  - **次段階条件**: {{this.next_level_condition}}
  {{/each}}
  
  ## ⏱️ 実行スケジュール
  
  ### 基本スケジュール
  - **実行頻度**: {{frequency_settings}}
  - **営業時間設定**: {{schedule.business_hours}}
  - **休日・例外日**: {{schedule.exceptions}}
  - **タイムゾーン**: {{schedule.timezone}}
  
  ### 動的調整
  - **負荷連動調整**: {{schedule.load_based_adjustment}}
  - **緊急時優先**: {{schedule.emergency_priority}}
  - **保守時間停止**: {{schedule.maintenance_pause}}
  
  ## 📊 実行状況・パフォーマンス
  
  ### 実行統計（直近30日）
  - **総実行回数**: {{performance.total_executions}}回
  - **成功率**: {{performance.success_rate}}%
  - **平均実行時間**: {{performance.avg_execution_time}}秒
  - **エラー率**: {{performance.error_rate}}%
  
  ### 効果測定
  - **処理時間短縮**: {{impact.time_savings}}時間/月
  - **人的工数削減**: {{impact.labor_reduction}}%
  - **品質向上**: {{impact.quality_improvement}}%
  - **コスト削減**: ¥{{impact.cost_savings:number}}/月
  
  ## 🔍 監視・アラート
  
  ### 監視項目
  {{#each monitoring_items}}
  - **{{this.metric}}**: {{this.current_value}} (閾値: {{this.threshold}})
  {{/each}}
  
  ### アラート設定
  - **パフォーマンス低下**: {{alerts.performance_degradation}}
  - **エラー率上昇**: {{alerts.error_rate_increase}}
  - **実行失敗**: {{alerts.execution_failure}}
  - **システム異常**: {{alerts.system_anomaly}}
  
  ## 🛠️ 保守・最適化
  
  ### 定期メンテナンス
  - **ルール見直し**: {{maintenance.rule_review_schedule}}
  - **パフォーマンス調整**: {{maintenance.performance_tuning}}
  - **システム更新**: {{maintenance.system_updates}}
  - **セキュリティ監査**: {{maintenance.security_audit}}
  
  ### 改善提案
  {{#each improvement_suggestions}}
  #### {{this.category}}
  - **現状課題**: {{this.current_issue}}
  - **改善案**: {{this.proposed_solution}}
  - **期待効果**: {{this.expected_benefit}}
  - **実装コスト**: {{this.implementation_cost}}
  - **優先度**: {{this.priority}}
  {{/each}}
  
  ## 🔒 セキュリティ・コンプライアンス
  
  ### アクセス制御
  - **実行権限**: {{security.execution_permissions}}
  - **設定変更権限**: {{security.configuration_permissions}}
  - **監視権限**: {{security.monitoring_permissions}}
  - **監査ログ**: {{security.audit_logging}}
  
  ### コンプライアンス
  - **規制要件遵守**: {{compliance.regulatory_compliance}}
  - **社内規定準拠**: {{compliance.internal_policy_compliance}}
  - **データ保護**: {{compliance.data_protection}}
  - **プライバシー保護**: {{compliance.privacy_protection}}
  
  ## 📅 今後のアクション
  
  ### 短期改善（1ヶ月以内）
  {{#each short_term_actions}}
  - {{this.description}} (担当: {{this.assignee}}, 期限: {{this.deadline}})
  {{/each}}
  
  ### 中期最適化（四半期内）
  {{#each medium_term_optimizations}}
  - {{this.description}} (ROI: {{this.expected_roi}}%)
  {{/each}}
  
  ### 長期戦略（年次）
  {{#each strategic_initiatives}}
  - {{this.description}} (投資: ¥{{this.investment:number}})
  {{/each}}
  
  ---
  **文書情報**
  - 作成日: {{meta.timestamp}}
  - ドメイン: ticket_management
  - エージェント: SlackTicketAgent
  - 分類: 自動化・通知・エスカレーション

# エイリアス（互換性のため）
automation_template: |
  ---
  file_type: "automation_config"
  automation_type: "{{automation_type}}"
  status: "{{automation.status}}"
  execution_mode: "{{automation.execution_mode}}"
  generated_at: "{{meta.timestamp}}"
  domain: "ticket_management"
  agent: "TicketManagement"
  ---
  # 自動化ルール設定・実行レポート - {{meta.timestamp}}
  
  ## ⚙️ 自動化概要
  **自動化種別**: {{automation_type}}
  **設定日時**: {{meta.timestamp}}
  **ステータス**: {{automation.status}}
  **実行モード**: {{automation.execution_mode}}

# ======== エラーハンドリング ========

error_handling:
  rule_conflict:
    message: "自動化ルールの競合が検出されました"
    recovery_actions:
      - "優先度に基づく自動調整"
      - "管理者への競合解消依頼"
  
  execution_failure:
    message: "自動化実行に失敗しました"
    recovery_actions:
      - "フォールバック手順の実行"
      - "手動処理への切り替え案内"

# ======== 設定 ========

automation_rules_settings:
  intelligent_execution: true
  performance_optimization: true
  security_compliance: true
  continuous_learning: true

# ======== 統合ポイント ========

integration_points:
  ticket_system:
    trigger: "ルール実行完了"
    action: "update_ticket_status_and_log"
  
  monitoring_system:
    trigger: "異常検出"
    action: "automated_incident_response"

# ======== 品質保証 ========

quality_assurance:
  mandatory_checks:
    - "ルール論理的一貫性・完全性確認"
    - "実行パフォーマンス・安定性確認"
    - "セキュリティ・コンプライアンス遵守確認"

# ======== 成功メトリクス ========

success_metrics:
  - "自動化実行成功率 > 99.9%"
  - "処理時間短縮率 > 70%"
  - "人的工数削減率 > 60%"
  - "システム稼働率 > 99.5%"
