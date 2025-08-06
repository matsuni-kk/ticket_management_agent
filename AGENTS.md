# ⚠️ 重要: このファイルは自動生成されています
# ルールを修正する場合は .cursor/rules ディレクトリ内の .mdc ファイルを編集してください
# 直接このファイルを編集しないでください - 変更は上書きされます

# 00_master_rules.md

path_reference: "ticket_management_paths.mdc"

# ======== Ticket Management Agent マスタールール ========
# チケット管理業務を効率化し、最適な顧客対応とワークフロー管理を提供

master_triggers:
  # 1. テキスト解析・チケット生成
  - trigger: "(text analysis|ticket generation|create ticket|analyze message|テキスト解析|チケット生成)"
    priority: high
    mode: "interactive"
    steps:
      - name: "start_message"
        action: "message"
        content: "**テキスト解析・チケット生成を開始します。**\n\n顧客メッセージから情報を抽出し、標準化されたチケット形式を生成します。"
      - name: "collect_existing_info"
        action: "gather_existing_info"
        message: "既存の顧客情報を収集中..."
      - name: "ask_analysis_questions"
        action: "call .claude/agents/01_text_analysis.md => text_analysis_questions"
        message: "詳細な要件分析を実行します。"
      - name: "create_ticket_draft"
        action: "create_markdown_file"
        path: "{{patterns.draft_ticket_analysis}}"
        template_reference: "01_text_analysis.mdc => text_analysis_template"
        message: "チケットドラフトを作成中..."
        mandatory: true
      - name: "completion_message"
        action: "notify"
        message: "**テキスト解析完了。**\n\n保存先: `{{patterns.draft_ticket_analysis}}`\n\n内容を確認後、'Stock移動'で確定してください。"

  # 2. チケット分類・割り当て
  - trigger: "(ticket classification|classify ticket|assign ticket|prioritize|チケット分類|優先度付け)"
    priority: high
    mode: "interactive"
    steps:
      - name: "start_message"
        action: "message"
        content: "**チケット分類・割り当てを開始します。**\n\n多次元分析による精密な分類と最適なリソース配分を実行します。"
      - name: "collect_existing_info"
        action: "gather_existing_info"
        message: "既存のチケット情報を収集中..."
      - name: "ask_classification_questions"
        action: "call .claude/agents/02_classification.md => classification_questions"
        message: "分類基準と割り当て条件を分析します。"
      - name: "create_classification_draft"
        action: "create_markdown_file"
        path: "{{patterns.draft_ticket_classification}}"
        template_reference: "02_classification.mdc => classification_template"
        message: "分類結果を作成中..."
        mandatory: true
      - name: "completion_message"
        action: "notify"
        message: "**チケット分類・割り当て完了。**\n\n保存先: `{{patterns.draft_ticket_classification}}`\n\n分類結果と担当者配分を確認してください。"

  # 3. 進捗管理・ステータス更新
  - trigger: "(progress tracking|status update|track progress|update status|進捗管理|ステータス更新)"
    priority: medium
    mode: "interactive"
    steps:
      - name: "start_message"
        action: "message"
        content: "**進捗管理・ステータス更新を開始します。**\n\n現在のチケット状況を詳細に収集し、包括的な進捗管理を提供します。"
      - name: "collect_existing_info"
        action: "gather_existing_info"
        message: "現在の進捗状況を収集中..."
      - name: "ask_progress_questions"
        action: "call .claude/agents/03_tracking.md => tracking_questions"
        message: "進捗詳細と次のアクションを分析します。"
      - name: "create_progress_report"
        action: "create_markdown_file"
        path: "{{patterns.draft_progress_report}}"
        template_reference: "03_tracking.mdc => tracking_template"
        message: "進捗レポートを作成中..."
        mandatory: true
      - name: "completion_message"
        action: "notify"
        message: "**進捗管理レポート作成完了。**\n\n保存先: `{{patterns.draft_progress_report}}`\n\n進捗状況と次のアクションを確認してください。"

  # 4. レポート・ダッシュボード生成
  - trigger: "(generate report|dashboard|reporting|analytics report|レポート生成|ダッシュボード)"
    priority: medium
    mode: "interactive"
    steps:
      - name: "start_message"
        action: "message"
        content: "**レポート・ダッシュボード生成を開始します。**\n\nチケット管理データの包括的分析と可視化を実行します。"
      - name: "collect_existing_info"
        action: "gather_existing_info"
        message: "分析対象データを収集中..."
      - name: "ask_reporting_questions"
        action: "call .claude/agents/04_reporting.md => reporting_questions"
        message: "レポート要件と分析範囲を確認します。"
      - name: "create_analysis_report"
        action: "create_markdown_file"
        path: "{{patterns.output_analysis_report}}"
        template_reference: "04_reporting.mdc => reporting_template"
        message: "分析レポートを生成中..."
        mandatory: true
      - name: "completion_message"
        action: "notify"
        message: "**分析レポート生成完了。**\n\n保存先: `{{patterns.output_analysis_report}}`\n\n包括的分析結果と洞察を確認してください。"

  # 5. 自動化ルール・通知設定
  - trigger: "(automation setup|notification setup|automation rules|escalation|自動化設定|通知設定)"
    priority: low
    mode: "interactive"
    steps:
      - name: "start_message"
        action: "message"
        content: "**自動化ルール・通知設定を開始します。**\n\n効率的なチケット処理のための自動化システムを構築します。"
      - name: "collect_existing_info"
        action: "gather_existing_info"
        message: "現在の設定を確認中..."
      - name: "ask_automation_questions"
        action: "call .claude/agents/05_automation.md => automation_questions"
        message: "自動化要件と通知条件を設定します。"
      - name: "create_automation_config"
        action: "create_markdown_file"
        path: "{{patterns.output_automation_config}}"
        template_reference: "05_automation.mdc => automation_template"
        message: "自動化設定を作成中..."
        mandatory: true
      - name: "completion_message"
        action: "notify"
        message: "**自動化設定完了。**\n\n保存先: `{{patterns.output_automation_config}}`\n\n設定内容を確認し、システムに適用してください。"

  # 6. タスク管理
  - trigger: "(今日のタスク作成|daily task|task作成)"
    priority: medium
    steps:
      - name: "create_daily_task"
        action: "call .claude/agents/90_task_management.md => create_daily_task"
        message: "日次タスクを作成します。"

  # 7. Flow to Stock 移行
  - trigger: "(Flow確定|Stock移動|確定版作成)"
    priority: medium
    steps:
      - name: "move_to_stock"
        action: "call .claude/agents/97_flow_to_stock_rules.md => flow_to_stock_process"
        message: "Flowコンテンツを確定版としてStockに移行します。"

  # 8. Flow支援
  - trigger: "(Flow支援|作業支援|draft支援)"
    priority: low
    steps:
      - name: "flow_assist"
        action: "call .claude/agents/98_flow_assist.md => provide_flow_assistance"
        message: "Flow作業の支援を提供します。"

  # 9. ルールメンテナンス
  - trigger: "(ルール更新|rule update|ルールメンテナンス)"
    priority: low
    steps:
      - name: "rule_maintenance"
        action: "call .claude/agents/99_rule_maintenance.md => maintain_rules"
        message: "ルールの更新・メンテナンスを実行します。"

# ======== 共通設定 ========
# 自動実行設定
auto_triggers:
  - event: "ticket_created"
    trigger: "チケット分類"
    auto_confirm: false
  - event: "customer_message_received"
    trigger: "テキスト解析"
    auto_confirm: false
  - event: "status_change_required"
    trigger: "進捗管理"
    auto_confirm: false
  - event: "daily_report_time"
    trigger: "レポート生成"
    auto_confirm: false
  - event: "flow_content_ready"
    trigger: "Stock移動"
    auto_confirm: false

# デフォルト設定
defaults:
  language: "ja"
  encoding: "utf-8"
  timestamp_format: "YYYY-MM-DD-HHmm"
  
  # チケット管理デフォルト設定
  ticket_priority_levels: ["低", "中", "高", "緊急"]
  default_ticket_priority: "中"
  ticket_status_types: ["新規", "対応中", "保留", "解決済", "クローズ"]
  default_ticket_status: "新規"
  
  # 分類デフォルト設定
  classification_categories: ["技術的問題", "機能要望", "バグ報告", "サポート依頼", "その他"]
  assignment_method: "スキルベース"
  escalation_time: "24時間"
  
  # 進捗管理デフォルト設定
  progress_update_frequency: "daily"
  status_change_notification: true
  deadline_alert_advance: "3日前"
  
  # レポートデフォルト設定
  report_period: "月次"
  include_metrics: ["解決率", "平均対応時間", "顧客満足度"]
  chart_types: ["棒グラフ", "円グラフ", "時系列グラフ"]
  
  # 自動化デフォルト設定
  auto_assignment: false
  auto_escalation: true
  notification_channels: ["メール", "Slack"]
  working_hours: "9:00-18:00"
  
  # ファイル名統一規則設定
  standard_ticket_files:
    inquiry_file: "inquiry.md"      # 顧客からの問い合わせ内容
    response_file: "response.md"    # 提供した回答・解決策
    readme_file: "README.md"        # チケット概要・サマリー
    technical_analysis_file: "technical_analysis.md"  # 技術的分析
    technical_details_file: "technical_details.md"   # 技術的詳細
  
  # ファイル命名規則の説明
  file_naming_convention:
    description: "チケット内ファイルの統一規則"
    rules:
      - "inquiry.md: 顧客からの問い合わせ内容を記録"
      - "response.md: 提供した回答・解決策を記録"
      - "README.md: チケットの概要とサマリー"
      - "technical_*.md: 技術的な分析・詳細情報"
  
  # フロントマター統一規則
  frontmatter_standards:
    description: "全チケットファイルに必須のメタデータ構造"
    inquiry_frontmatter:
      file_type: "inquiry"
      ticket_id: "TKT-YYYYMMDD-XXX"
      company: "会社名"
      reporter: "報告者名"
      date: "YYYY-MM-DD"
      status: "新規/対応中/解決済"
      category: "技術的問題/機能要望/バグ報告/サポート依頼/その他"
      priority: "低/中/高/緊急"
    response_frontmatter:
      file_type: "response"
      ticket_id: "TKT-YYYYMMDD-XXX"
      responder: "回答者名"
      response_date: "YYYY-MM-DD"
      status: "初回回答/進捗報告/最終回答"
      resolution_status: "解決済/部分解決/対応中/保留"
    readme_frontmatter:
      file_type: "ticket_summary"
      ticket_id: "TKT-YYYYMMDD-XXX"
      title: "チケットタイトル"
      company: "会社名"
      reporter: "報告者名"
      create_date: "YYYY-MM-DD"
      update_date: "YYYY-MM-DD"
      status: "新規/対応中/解決済/クローズ"
      category: "技術的問題/機能要望/バグ報告/サポート依頼/その他"
      priority: "低/中/高/緊急"
      assigned_to: "担当者名"
    technical_frontmatter:
      file_type: "technical_analysis or technical_details"
      ticket_id: "TKT-YYYYMMDD-XXX"
      analyst: "分析者名"
      analysis_date: "YYYY-MM-DD"
      complexity: "低/中/高"
      tech_category: "技術カテゴリ"

# Ticket Management Agent Paths

root: "/Users/username/workspace/ticket_management_agent"

dirs:
  flow: "{{root}}/Flow"
  flow_public: "{{flow}}/Public"
  flow_private: "{{flow}}/Private"
  stock: "{{root}}/Stock"
  archived: "{{root}}/Archived"
  docs_root: "{{stock}}/documents"
  tickets_root: "{{root}}/tickets"

patterns:
  # 基本パターン
  flow_public_date: "{{flow_public}}/{{env.NOW:date:YYYY-MM-DD}}"
  stock_document: "{{docs_root}}/{{document_name}}.md"
  
  # Ticket Management specific path patterns
  # Flow workflow patterns (Draft → Review/Edit → Stock migration)
  draft_ticket_analysis: "{{flow_public_date}}/draft_ticket_analysis.md"
  draft_ticket_classification: "{{flow_public_date}}/draft_ticket_classification.md"
  draft_progress_report: "{{flow_public_date}}/draft_progress_report.md"
  
  # Direct conversion patterns (immediate final format generation)
  output_analysis_report: "{{docs_root}}/ticket_analysis_report_{{env.NOW:date:YYYY-MM-DD}}.md"
  output_automation_config: "{{docs_root}}/automation_config_{{env.NOW:date:YYYY-MM-DD}}.md"
  output_dashboard: "{{docs_root}}/dashboard_{{env.NOW:date:YYYY-MM-DD}}.md"
  
  # Stock finalized version patterns
  stock_ticket_analysis: "{{docs_root}}/ticket_analysis.md"
  stock_classification: "{{docs_root}}/ticket_classification.md"
  stock_progress_report: "{{docs_root}}/progress_report.md"
  stock_automation_config: "{{docs_root}}/automation_config.md"
  
  # Dedicated directory patterns
  tickets_dir: "{{tickets_root}}"
  reports_dir: "{{docs_root}}/reports"
  configs_dir: "{{docs_root}}/configs"
  
  # Company and ticket patterns
  company_dir: "{{tickets_root}}/{{company_name}}"
  in_progress_dir: "{{company_dir}}/in_progress"
  completed_dir: "{{company_dir}}/completed"
  ticket_folder: "{{status_dir}}/{{env.NOW:date:YYYYMMDD}}_{{ticket_name}}"
  
  # Ticket management specific patterns
  ticket_archive: "{{archived}}/tickets/{{env.NOW:date:YYYY-MM}}"
  daily_report: "{{reports_dir}}/daily_{{env.NOW:date:YYYY-MM-DD}}.md"
  weekly_report: "{{reports_dir}}/weekly_{{env.NOW:date:YYYY-'W'WW}}.md"
  monthly_report: "{{reports_dir}}/monthly_{{env.NOW:date:YYYY-MM}}.md"
  
  # Standard ticket file patterns (統一されたファイル名規則 + フロントマター)
  ticket_inquiry: "{{ticket_folder}}/inquiry.md"
  ticket_response: "{{ticket_folder}}/response.md"
  ticket_readme: "{{ticket_folder}}/README.md"
  ticket_technical_analysis: "{{ticket_folder}}/technical_analysis.md"
  ticket_technical_details: "{{ticket_folder}}/technical_details.md"
  
  # Frontmatter templates for each file type
  inquiry_template: |
    ---
    file_type: "inquiry"
    ticket_id: "{{ticket_id}}"
    company: "{{company_name}}"
    reporter: "{{reporter_name}}"
    date: "{{date}}"
    status: "{{status}}"
    category: "{{category}}"
    priority: "{{priority}}"
    ---
  
  response_template: |
    ---
    file_type: "response"
    ticket_id: "{{ticket_id}}"
    responder: "{{responder_name}}"
    response_date: "{{response_date}}"
    status: "{{response_status}}"
    resolution_status: "{{resolution_status}}"
    ---
  
  readme_template: |
    ---
    file_type: "ticket_summary"
    ticket_id: "{{ticket_id}}"
    title: "{{title}}"
    company: "{{company_name}}"
    reporter: "{{reporter_name}}"
    create_date: "{{create_date}}"
    update_date: "{{update_date}}"
    status: "{{status}}"
    category: "{{category}}"
    priority: "{{priority}}"
    assigned_to: "{{assigned_to}}"
    estimated_hours: "{{estimated_hours}}"
    ---
  
  technical_template: |
    ---
    file_type: "{{file_type}}"
    ticket_id: "{{ticket_id}}"
    analyst: "{{analyst_name}}"
    analysis_date: "{{analysis_date}}"
    complexity: "{{complexity}}"
    tech_category: "{{tech_category}}"
    ---

meta:
  agent_name: "TicketManagement"
  domain: "ticket_management"
