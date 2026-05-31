# EhomeSpecFlow

GitHub Copilot を前提に、spec-driven development を進めるための repository custom instructions と prompt files をまとめたリポジトリです。

このリポジトリでは、目標設定、仕様設計、実装、テスト設計、テスト実装、テスト実行を段階的に進めるための prompt を .github/prompts に配置し、成果物を docs 配下へ蓄積します。

## 前提

- GitHub Copilotを使用していること

## リポジトリ構成

初期状態の主要構成は次のとおりです。

```text
.
├─ .github/
│  ├─ copilot-instructions.md
│  └─ prompts/
│     ├─ target.prompt.md
│     ├─ spec.prompt.md
│     ├─ impl.prompt.md
│     ├─ test-design.prompt.md
│     ├─ test-impl.prompt.md
│     └─ test-exec.prompt.md
├─ docs/
│  ├─ _plans/
│  │  ├─ tasks_impl.md
│  │  └─ tasks_testimpl.md
│  ├─ common/
│  └─ features/
└─ README.md
```

### .github 配下

| パス | 役割 |
|------|------|
| .github/copilot-instructions.md | このリポジトリ全体に常時適用される Copilot 向けルール。文書の配置規則、変更履歴、コード禁止などを定義します。 |
| .github/prompts/target.prompt.md | 目標設定書の作成・修正を行う prompt。 |
| .github/prompts/spec.prompt.md | 仕様書・設計書の作成・修正を行う prompt。 |
| .github/prompts/impl.prompt.md | 実装タスクに基づいて実装を進める prompt。 |
| .github/prompts/test-design.prompt.md | テスト設計書の作成・修正を行う prompt。 |
| .github/prompts/test-impl.prompt.md | テスト実装タスクに基づいてテストコードを実装する prompt。 |
| .github/prompts/test-exec.prompt.md | テストのビルド・実行・結果報告を行う prompt。 |

### docs 配下

docs は spec-driven development の成果物置き場です。

| パス | 役割 |
|------|------|
| docs/Target.md | 目標設定書。ペルソナ、対象プラットフォーム、利用シナリオ、期待効果、目標を管理します。 |
| docs/common/Common_Design.md | 共通設計書。技術スタックとアーキテクチャ全体像を管理します。 |
| docs/common/Common-<LayerName>_Design.md | 共通レイヤー単位の設計書です。 |
| docs/common/Common-<LayerName>_TestDesign.md | 共通レイヤー単位のテスト設計書です。 |
| docs/features/<FeatureName>/<FeatureName>_spec.md | Feature 単位の仕様書です。 |
| docs/features/<FeatureName>/<FeatureName>_design.md | Feature 単位の設計書です。 |
| docs/features/<FeatureName>/<FeatureName>_TestDesign.md | Feature 単位のテスト設計書です。 |
| docs/_plans/tasks_impl.md | 未完了の実装タスクを管理します。完了したタスクは削除します。 |
| docs/_plans/tasks_testimpl.md | 未完了のテスト実装タスクを管理します。完了したタスクは削除します。 |

## 生成されるファイル

このリポジトリを使って作業を進めると、主に docs 配下に次のファイルが生成または更新されます。

```text
docs/
├─ Target.md
├─ common/
│  ├─ Common_Design.md
│  ├─ Common-<LayerName>_Design.md
│  └─ Common-<LayerName>_TestDesign.md
├─ features/
│  ├─ <FeatureName>/
│     ├─ <FeatureName>_spec.md
│     ├─ <FeatureName>_design.md
│     └─ <FeatureName>_TestDesign.md
└─ _plans/
   ├─ tasks_impl.md
   └─ tasks_testimpl.md
```

注意点:

- docs/common と docs/features は初期状態では空でも問題ありません。
- 実際に生成されるファイル名は対象の LayerName と FeatureName に応じて増減します。
- 文書を新規作成または改名した場合、.github/copilot-instructions.md のルールに従い README の一覧も更新する運用です。

## prompt の実行方法

prompt files は自動適用ではなく、明示的に実行します。VS Code の GitHub Copilot Chat では次の方法で実行できます。

1. Chat 入力欄で / に続けて prompt 名を入力する
2. Command Palette から Chat: Run Prompt を実行して prompt を選ぶ
3. prompt ファイルをエディタで開き、タイトルバーの再生ボタンから実行する

このリポジトリでは frontmatter に name が未指定のため、slash command 名は基本的にファイル名ベースです。

| ファイル | 実行名の例 |
|------|------|
| .github/prompts/target.prompt.md | /target |
| .github/prompts/spec.prompt.md | /spec |
| .github/prompts/impl.prompt.md | /impl |
| .github/prompts/test-design.prompt.md | /test-design |
| .github/prompts/test-impl.prompt.md | /test-impl |
| .github/prompts/test-exec.prompt.md | /test-exec |

## 推奨運用手順

spec-driven development の流れとして、次の順序で実行する想定です。

### 1. 目標を定義する

- /target を実行して docs/Target.md を作成または更新します。
- プロダクトの目的、利用者、対象プラットフォーム、期待効果、目標を定義します。

### 2. 仕様書・設計書を整備する

- /spec を実行して docs/common または docs/features 配下の仕様書・設計書を作成または更新します。
- 必要に応じて docs/_plans/tasks_impl.md に未完了の実装タスクを追加します。

### 3. 実装する

- /impl を実行して docs/_plans/tasks_impl.md を参照しながら実装します。
- 完了した実装タスクは docs/_plans/tasks_impl.md から削除します。
- 設計との差分が発生した場合は、必要に応じて関連文書も更新します。

### 4. テスト設計を作る

- /test-design を実行して共通レイヤーまたは feature 単位のテスト設計書を作成または更新します。
- 対応する未完了テストは docs/_plans/tasks_testimpl.md に反映します。

### 5. テストコードを実装する

- /test-impl を実行して docs/_plans/tasks_testimpl.md に記載されたテストケースを実装します。
- 完了したテストケースは docs/_plans/tasks_testimpl.md から削除します。

### 6. テストを実行する

- /test-exec を実行してビルド、テスト実行、結果報告を行います。
- テスト失敗時は、prompt の定義に従い、原因が実装コードにある場合のみ実装修正を行います。

## 代表的な使い方

### 新機能を 0 から進める場合

1. /target でプロダクト目標または目標差分を整理する
2. /spec で対象 feature の仕様書と設計書を作る
3. /impl で実装する
4. /test-design でテスト観点を定義する
5. /test-impl でテストコードを追加する
6. /test-exec で確認する

### 既存 feature を改修する場合

1. /spec で既存仕様書・設計書を修正する
2. /impl で関連実装を変更する
3. /test-design で不足テストを補う
4. /test-impl でテストを更新する
5. /test-exec で回帰確認する

## 運用ルールの要点

- 仕様書、設計書、テスト設計書、タスク管理書には具体的なプログラムコードを書かない
- 変更した文書には変更履歴を追加し、版番号を更新する
- 日付は yyyy-MM-dd 形式で記録する
- 入出力例は代表的なハッピーパスを 1 つに絞る
- 横断的な内容は docs/common、feature 固有の内容は docs/features/<FeatureName> に分ける

## Naming

EhomeSpecFlow is the name of the original spec-driven development workflow framework maintained in this repository.

## License

MIT License