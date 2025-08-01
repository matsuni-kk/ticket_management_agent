---
doc_type: root_directory
project_id: slack_ticket
created_at: {{env.NOW:date:YYYY-MM-DD}}
version: v1.0
---

# Root Directory - SlackTicket Agent

このファイルはSlackTicketエージェントのルートディレクトリを示します。

## Root Directory Path
このエージェントは独立したリポジトリとして設計されています。
クローン先のディレクトリがルートディレクトリとなります。

- Mac/Linux: `~/workspace/slack_ticket_agent`
- Windows: `C:\workspace\slack_ticket_agent`

## Agent Information
- **Agent Name**: SlackTicket
- **Domain**: slack_ticket
- **Description**: Slack投稿から顧客タスクをチケット管理システムで処理するエージェント

## Directory Structure
```
slack_ticket_agent/
├── Flow/           # 作業中のドキュメント
│   ├── Public/     # 公開可能な作業ドキュメント
│   └── Private/    # 非公開の作業ドキュメント
├── Stock/          # 確定済みドキュメント
├── Archived/       # アーカイブ
├── cursor_bank/    # ルールファイル（.md形式）
├── scripts/        # 自動化スクリプト
└── .cursor/        # Cursor設定
    └── rules/      # 変換済みルール（.mdc形式）
```

## Quick Start
1. このリポジトリをクローン
2. Cursorでこのディレクトリを開く
3. 必要に応じて `scripts/convert_md_to_mdc.py` を実行してルールを更新

## Specialized Features
### SlackTicket特化機能
- ドメイン固有のワークフロー
- 専用のドキュメントテンプレート
- 自動化されたタスク管理
