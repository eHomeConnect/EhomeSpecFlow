---
agent: agent
model: GPT-5.4 (copilot)
tools: [search, edit/editFiles, edit/createFile, vscode/runCommand, execute/runInTerminal]
---

指示された領域のコーディングを行ってください。

## 対象領域
- ユーザーから対象タスクの指示がある場合は、docs/_plans/tasks_impl.md にある実装タスクのうち、指示内容に対応するタスクのみを対象とすること。
- ユーザーから対象タスクの指示がない場合は、docs/_plans/tasks_impl.md の全てのタスクを対象とすること。
- 対応する実装タスクが docs/_plans/tasks_impl.md に存在しない場合は、その旨を明示したうえで、関連する設計書を確認して実装対象を特定すること。

## 参照文書
- 仕様書: docs/features/<FeatureName>/<FeatureName>_spec.md、docs/common/Common_Design.md、および関連する分割文書
- 設計書: docs/features/<FeatureName>/<FeatureName>_design.md、docs/common/Common-<LayerName>_Design.md、および関連する分割文書
- 実装タスク管理書: docs/_plans/tasks_impl.md

## 実装ルール

**このフェーズではテストコードの変更は行わないこと。** 

- 実装を完了したタスクは docs/_plans/tasks_impl.md から削除すること。
- 実装途中で完了できていないタスクは docs/_plans/tasks_impl.md に残し、必要に応じて Status を維持または更新すること。

### 画面のみの実装について

以下の場合は、サービスやデータと接続せずに **画面と画面遷移のみ** を実装すること：

- ユーザーから画面のみの実装を指示された場合
- 画面の仕様や設計のみが定義されており、関連するサービス層やデータ層の仕様・設計が定義されていない場合

この場合、モックデータやスタブを使用してUIの動作確認ができる状態にすること。

### 設計書との整合性

**ユーザー指示内容が明らかに設計書に反する、または設計書に定義されていないが実装として採用するのが妥当な場合は、実装に合わせて関連する設計書も改定すること。**

設計書を更新した場合は、該当文書の変更履歴も更新すること。

## コーディング規約の遵守

関連するクラスの修正が必要な場合は、それらの修正も併せて提案すること。

コーディング規約、命名規則に従うこと。
