---
file_type: "inquiry"
ticket_id: "TKT-20250819-002"
company: "Loglass"
reporter: "Yukari Okabe"
date: "2025-08-15"
status: "対応中"
category: "機能改善要望"
priority: "中"
related_systems: ["Dify", "ワークフロー", "リリースノート生成", "フィードバックサイクル"]
related_files: ["workflow-dsl-Ver.1.0.3.yml", "iteration_scoring_feedback_medium_sample.yml"]
technical_focus: "ドキュメント生成精度向上のためのフィードバック機能実装"
issued_at: "2025-08-15"
due_date: ""
ball_holder: "当方"
---

# 問い合わせ内容 - Difyワークフローのフィードバックサイクル改善

## 問い合わせ者: Yukari Okabe
## 問い合わせ日時: 2025-08-15 17:32

@matsuni
ご相談です。
04_rules/dify/backup/workflow-dsl-Ver.1.0.3.yml
を中心とした、ワークフローの運用を開始したのですが、実際に生成されるドキュメントの精度をあげるべく、フィードバックサイクルを回していきたいです。

例えば以下のようなものについて（画像のリンクが切れているのは、画像パスの間違いによるものです）、解釈違いなどがあったりするので、なにが違う、ここは大事、などを蓄積していくようなイメージです。

## 参考事例

### 元のドキュメント
https://github.com/loglass/loglass-support-docs/blob/main/05_automation/release-no[…]%9B%86%E8%A8%88%E5%9F%BA%E7%9B%A4%E3%81%AB%E7%A7%BB%E8%A1%8C.md

### 生成されたリリースノート
https://github.com/loglass/loglass-support-docs/blob/main/05_automation/release-notes/current/release-note-2025-08-14%2017%3A06%3A36%20JST.md

どのようにそのFBサイクルを組み込んで行けばよいか、アドバイスいただけますでしょうか。

## 技術的詳細

### 現在の運用状況
- **使用ファイル**: workflow-dsl-Ver.1.0.3.yml
- **システム**: Difyワークフロー
- **処理内容**: リリースノート自動生成
- **課題**: 生成精度にバラつきがあり、継続的改善が必要

### 具体的な問題点
1. **解釈の相違**
   - 元ドキュメントと生成されたリリースノートの内容にズレ
   - 重要なポイントの見落とし
   - 不正確な表現や誤解釈

2. **画像リンク問題**
   - 画像パスの間違いによるリンク切れ
   - 視覚的情報の欠落

3. **フィードバック蓄積の仕組み不足**
   - 「なにが違う」「ここは大事」といった評価情報の記録方法
   - 継続的な品質改善サイクルの構築

## 期待する改善効果

### フィードバックサイクルの要素
- **差分の特定**: 元ドキュメントと生成結果の相違点を明確化
- **重要度の評価**: 各要素の重要性を評価・蓄積
- **継続的改善**: 評価結果をワークフローに反映して精度向上

### 運用上の期待
- **品質の向上**: 生成されるリリースノートの精度向上
- **効率化**: 手動確認・修正作業の削減
- **ナレッジ蓄積**: 改善ポイントの組織的な蓄積

## 確認事項
- Difyワークフローの現在の設定・構成
- GitHub連携の状況
- フィードバック情報の記録・活用希望方法
- 自動化vs手動介入のバランス

## 関連ファイル・システム
- **メインワークフロー**: workflow-dsl-Ver.1.0.3.yml
- **リポジトリ**: loglass/loglass-support-docs
- **対象ディレクトリ**: 05_automation/release-notes/
- **技術基盤**: Dify + GitHub連携