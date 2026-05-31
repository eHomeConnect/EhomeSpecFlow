---
agent: agent
model: GPT-5.4 (copilot)
tools: [search, edit/editFiles, edit/createFile, vscode/runCommand, execute/runInTerminal]
description: 'テスト設計書の作成を指示する'
---

下記のルールに従い、テスト設計書の新規作成、または既存テスト設計書の修正を行ってください。

## 参照文書
- 共通設計書: docs/common/Common_Design.md、および関連する分割文書
- 共通レイヤー設計書: docs/common/Common-<LayerName>_Design.md
- Feature設計書: docs/features/<FeatureName>/<FeatureName>_design.md

**整合性**: 上記文書に定義された「入出力例」や「仕様」と完全に整合させること。

## 記述原則
- **実装の禁止**: **このフェーズでは実装（コーディング）を行わないこと。文書の作成・修正のみを実施すること。**

## 実行プロセス
1. ユーザーの指示から、対象領域を特定する。
2. 設計書を参照し、テスト対象を洗い出す。
3. 各テスト対象に対してテストケースを定義する。
4. テスト設計書の追加・修正内容に対応するよう、`/docs/_plans/tasks_testimpl.md` を更新する。