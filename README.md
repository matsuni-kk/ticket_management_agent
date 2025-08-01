# Ticket Management Agent

An intelligent agent for processing customer tasks from various sources into a structured ticket management system.

## Overview

This repository contains an LLM agent system specialized for ticket management domain. 
It integrates with Cursor IDE to efficiently execute ticket management related tasks.

## Key Features

### Ticket Management Specialized Functions
- Text analysis & ticket generation from natural language
- Multi-dimensional ticket classification & assignment
- Progress tracking & status management
- Comprehensive reporting & dashboard generation
- Automation rules & notification systems

## セットアップ

### 1. リポジトリのクローン
```bash
git clone <repository-url> slack_ticket_agent
cd slack_ticket_agent
```

### 2. Cursor IDEでの利用
1. Cursor IDEでこのディレクトリを開く
2. `.cursor/rules/`ディレクトリに変換済みのルールが配置されています
3. エージェントが自動的に有効になります

### 3. ルールの更新（必要に応じて）
```bash
python scripts/convert_md_to_mdc.py
```

## 使い方

### 基本的なトリガー
- `slack_ticket初期化`: プロジェクトをセットアップ

### ディレクトリ構成
- `Flow/`: 作業中のドキュメント
- `Stock/`: 確定済みドキュメント
- `cursor_bank/`: ルールファイル（編集用）
- `.cursor/rules/`: 変換済みルール（Cursor用）

## カスタマイズ

### ルールの追加・編集
1. `cursor_bank/`内の`.md`ファイルを編集
2. `python scripts/convert_md_to_mdc.py`を実行
3. Cursorを再起動

### 新しいワークフローの追加
`cursor_bank/`に新しいルールファイルを作成し、必要なトリガーとアクションを定義してください。

## ライセンス

[ライセンス情報を追加]

## 貢献

[貢献ガイドラインを追加]
