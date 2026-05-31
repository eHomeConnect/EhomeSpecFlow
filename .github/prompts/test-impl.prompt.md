---
agent: agent
model: GPT-5.3-Codex (copilot)
tools: [search, edit/editFiles, edit/createFile, vscode/runCommand, execute/runInTerminal]
---

テストコードのコーディングを行ってください。

## 対象テストケース
- ユーザーから対象テストケースの指示がある場合は、`/docs/_plans/tasks_testimpl.md` に記載された未完了タスクのうち、対象テストケースのみを実装対象とすること。
- ユーザーから対象テストケースの指示がない場合は、`/docs/_plans/tasks_testimpl.md` に記載された未完了タスクを実装対象とすること。
- 実装が完了したテストケースは、`/docs/_plans/tasks_testimpl.md` から削除すること。

## 参照文書
- テスト実装タスク管理書: `/docs/_plans/tasks_testimpl.md`
- テスト設計書: `/docs/common/Common-*_TestDesign.md`、`/docs/features/<FeatureName>/<FeatureName>_TestDesign.md`

## 実装ルール

- 実装を完了したテストケースは `/docs/_plans/tasks_testimpl.md` から削除すること。
- 実装途中で完了できていないテストケースは `/docs/_plans/tasks_testimpl.md` に残すこと。

## コーディング規約の遵守
コーディング規約、命名規則に従うこと。