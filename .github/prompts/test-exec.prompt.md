---
agent: agent
model: GPT-5.4 (copilot)
tools: [search, edit/editFiles, edit/createFile, vscode/runCommand, execute/runInTerminal]
---

テストを実行し、テスト結果を報告してください。

## 対象領域
- ユーザーから対象領域の指示がある場合は、その領域に関連するテストを優先して実行すること。
- 対象領域の指示がない場合は、実行可能なテスト全体を対象とすること。

## 実行手順
1. テストプロジェクトをビルドする
2. 対象領域に応じてテストを実行する
3. テスト結果（成功数、失敗数、失敗したテストの詳細）を報告する

## 失敗時の対応
テストが失敗した場合:
1. 失敗したテストケースの詳細を確認する
2. 失敗の原因を調査する
3. 原因が実装コードにある場合のみ、以下の対応を行う

### 重要な制約
- **テストコードの修正は禁止** - テストコードに問題があると思われる場合でも、テストコードを変更してはならない

### 原因が実装コードにある場合
- 実装コードを調査し、以下の文書の範囲内で実装を修正する:
  - 仕様書: `/docs/features/<FeatureName>/<FeatureName>_spec.md`、`/docs/common/Common_Design.md` および関連する分割文書
  - 設計書: `/docs/features/<FeatureName>/<FeatureName>_design.md`、`/docs/common/Common-<LayerName>_Design.md` および関連する分割文書
- 仕様・設計の範囲外の修正が必要な場合は、修正を行わず、問題点を報告する
- 実装コードを修正した場合は、同じ対象範囲のテストを再実行し、結果を再報告する