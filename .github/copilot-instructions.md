# Copilot Instructions

## 基本

- 日本語で応答すること

## 文書群

| 文書種別 | ファイルパス | 説明 |
|---------|------------|------|
| 目標設定書 | `/docs/Target.md` | ペルソナ定義、対象プラットフォーム、利用シナリオ、期待効果、目標 |
| 共通設計書 | `/docs/common/Common_Design.md` | 技術スタック、アーキテクチャ全体像 |
| 共通レイヤー設計書 | `/docs/common/Common-<LayerName>_Design.md` | レイヤー別の設計方針、クラス/コンポーネント設計 |
| 共通レイヤーテスト設計書 | `/docs/common/Common-<LayerName>_TestDesign.md` | レイヤー別のテスト設計 |
| Feature仕様書 | `/docs/features/<FeatureName>/<FeatureName>_spec.md` | feature単位の画面仕様、画面遷移、ユースケース |
| Feature設計書 | `/docs/features/<FeatureName>/<FeatureName>_design.md` | feature単位の設計方針、クラス/コンポーネント設計 |
| Featureテスト設計書 | `/docs/features/<FeatureName>/<FeatureName>_TestDesign.md` | feature単位のテスト設計 |
| 実装タスク管理書 | `/docs/_plans/tasks_impl.md` | 未完了の実装タスク一覧 |
| テスト実装タスク管理書 | `/docs/_plans/tasks_testimpl.md` | 未完了のテスト実装タスク一覧 |

### 変更履歴欄（目標設定書、仕様書、設計書、テスト設計書）

目標設定書、仕様書、設計書、テスト設計書の冒頭には、以下の形式で変更履歴欄を作成すること。

```markdown
## 変更履歴

| 版番号 | 更新日 | 更新内容 | 更新者 |
|--------|--------|--------|--------|
| 1.1 | YYYY-MM-DD | XXXの設計を変更 | - |
| 1.0 | YYYY-MM-DD | 初版作成 | - |
```

- 文書を修正した場合は、変更履歴欄にエントリを追加し、版番号をインクリメントすること
- **変更履歴の日付**: 文書作成・修正時は、`Get-Date -Format "yyyy-MM-dd"` コマンド等で現在日付を取得し、変更履歴欄に記録すること

### 具体コードの禁止（全文書共通）

目標設定書、仕様書、設計書、テスト設計書、実装タスク管理書、テスト実装タスク管理書には、プログラムコード（C#等）を記述してはならない。構造やインターフェース、テストケースは自然言語で表現すること。

## 目標設定書ルール

### 1. 目標設定書ファイル構成ルール
- **ファイルパス**: `/docs/Target.md`
- 必須項目は「ペルソナ定義」「対象プラットフォーム」「利用シナリオ」「期待効果」「目標」とする。

## 共通文書・Feature文書ルール

### 1. ファイル構成ルール

| 文書種別 | ファイルパス | 説明 |
|---------|------------|------|
| 共通設計書 | `/docs/common/Common_Design.md` | 技術スタック、アーキテクチャ全体像 |
| 共通レイヤー設計書 | `/docs/common/Common-<LayerName>_Design.md` | レイヤー別設計 |
| 共通レイヤーテスト設計書 | `/docs/common/Common-<LayerName>_TestDesign.md` | レイヤー別テスト設計 |
| Feature仕様書 | `/docs/features/<FeatureName>/<FeatureName>_spec.md` | feature仕様 |
| Feature設計書 | `/docs/features/<FeatureName>/<FeatureName>_design.md` | feature設計 |
| Featureテスト設計書 | `/docs/features/<FeatureName>/<FeatureName>_TestDesign.md` | featureテスト設計 |
| 実装タスク管理書 | `/docs/_plans/tasks_impl.md` | 未完了の実装タスク管理 |
| テスト実装タスク管理書 | `/docs/_plans/tasks_testimpl.md` | 未完了のテスト実装タスク管理 |

- ファイル分割・変更履歴・具体コードの禁止は「文書管理」の共通ルールに従うこと。
- `<LayerName>` には `DB`、`Presentation`等のレイヤー名を使用すること。
- `<FeatureName>` は Feature を一意に表すパスカルケース名称を使用すること。

### 2. 記述原則
- **入出力例の限定**:
    - **最も一般的（ハッピーパス）なデータのみ**を1つ例示すること。
- **設計粒度の原則**:
    - DB、Service Layer、共通ユーティリティ等の横断的な基盤要素は `/docs/common/` 配下で整理すること。
    - 画面、画面遷移、画面固有のUI振る舞い、Feature固有のユースケースは `/docs/features/<FeatureName>/` 配下で整理すること。
 - **テスト設計の粒度原則**:
    - 共通レイヤーの単体テスト設計は `Common-<LayerName>_TestDesign.md` に記載すること。
    - Feature固有の単体テスト設計は `<FeatureName>_TestDesign.md` に記載すること。

### 3. README.md の更新
- ドキュメントを新規作成・改名した場合は、必ずプロジェクトルートの `README.md` にあるドキュメント一覧を最新の状態に更新すること。

### 4. 出力テンプレート

各文書には、それぞれ以下の構成を基本とすること。

#### 4.1 目標設定書（Target.md）

```markdown
# [アプリ名] - 目標設定書

**作成日**: YYYY-MM-DD
**バージョン**: vX.X  

---

## 変更履歴

---

## 1. 概要
- 本文書の目的と対象範囲

---

## 2. ペルソナ定義
- 利用者の役割
- 課題
- 利用頻度

---

## 3. 対象プラットフォーム
- 対応OS
- 実行形態
- 前提環境

---

## 4. 利用シナリオ
- 代表的な利用場面
- 利用の流れ

---

## 5. 期待効果
- 現状課題に対する改善効果
- 定性的効果

---

## 6. 目標
- 定量目標
- 定性目標
```

---

#### 4.2 共通設計書（/docs/common/Common_Design.md）

```markdown
# [アプリ名] - 共通設計書

**作成日**: YYYY-MM-DD  
**バージョン**: vX.X  

---

## 1. 概要
- 本文書の目的と対象範囲

---

## 2. 技術スタック
### 2.1 開発環境
### 2.2 フレームワーク・ライブラリ
### 2.3 対象プラットフォーム

---

## 3. アーキテクチャ全体像
### 3.1 レイヤー構成
### 3.2 通信フロー
### 3.3 依存関係
```

---

#### 4.3 共通レイヤー設計書（/docs/common/Common-<LayerName>_Design.md）

```markdown
# [アプリ名] - Common-<LayerName> 設計書

**作成日**: YYYY-MM-DD  
**バージョン**: vX.X  

---

## 変更履歴

---

## 1. 概要
- 対象レイヤー
- 対象範囲

---

## 2. 設計方針
- レイヤーの責務
- 設計上の原則
- 他レイヤーとの境界

---

## 3. クラス/コンポーネント設計
### 3.x [クラス名/コンポーネント名]
- 目的
- 責務
- プロパティ一覧
- メソッド一覧
- 入出力例
```

---

#### 4.4 共通レイヤーテスト設計書（/docs/common/Common-<LayerName>_TestDesign.md）

**目的**: 共通レイヤーの単体テスト仕様を定義する。

```markdown
# [アプリ名] - Common-<LayerName> テスト設計書

**作成日**: YYYY-MM-DD  
**バージョン**: vX.X  

---

## 変更履歴

---

## 1. 概要
- 対象レイヤー
- テスト対象範囲

## 2. テストケース詳細

| 項目 | 内容 |
|------|------|
| テストケースID | Common-Service-Test001 |
| テスト対象（ユニット） | クラス名.メソッド名 |
| テスト目的 | 正常系：○○が××されること |
| 前提条件（初期状態） | モックの設定、初期データの状態 |
| 入力（具体的な型、値） | パラメータ名: 型 = 値 |
| 期待出力（具体的な型、値） | 戻り値: 型 = 値、または状態変化の内容 |
```

---

#### 4.5 feature仕様書（/docs/features/<FeatureName>/<FeatureName>_spec.md）

**目的**: Feature単位の画面仕様、画面遷移、ユースケースを定義する。

```markdown
# [アプリ名] - <FeatureName> 仕様書

**作成日**: YYYY-MM-DD  
**バージョン**: vX.X  

---

## 変更履歴

---

## 1. 概要
- 対象feature
- 本文書の目的と対象範囲

---

## 2. 画面一覧
- 各画面の一覧表（画面名、ルート名、目的、主要機能）

---

## 3. 画面遷移図
- 画面間の遷移を図示（Mermaid等）
- 遷移条件の説明

---

## 4. 画面仕様
### 4.x [画面名]
- 目的
- 画面レイアウト（アスキーアート等）
- 表示項目
- 操作と振る舞い

---

## 5. ユースケース
### 5.x <FeatureName>-<UseCaseName>
- 目的
- 事前条件
- 基本フロー
- 入出力例（代表的なハッピーパスのみ）
```

---

#### 4.6 feature設計書（/docs/features/<FeatureName>/<FeatureName>_design.md）

**目的**: Feature単位の設計方針とクラス/コンポーネント設計を定義する。

```markdown
# [アプリ名] - <FeatureName> 設計書

**作成日**: YYYY-MM-DD  
**バージョン**: vX.X  

---

## 変更履歴

---

## 1. 概要
- 対象feature
- 本文書の目的と対象範囲

---

## 2. 設計方針
- featureの責務
- 設計原則
- 他feature/共通レイヤーとの依存関係

---

## 3. クラス/コンポーネント設計
### 3.x [クラス名/コンポーネント名]
- 目的
- 責務
- プロパティ一覧
- メソッド一覧
- 入出力例（代表的なハッピーパスのみ）
```

---

#### 4.7 featureテスト設計書（/docs/features/<FeatureName>/<FeatureName>_TestDesign.md）

**目的**: feature単位の単体テスト仕様を定義する。

```markdown
# [アプリ名] - <FeatureName> テスト設計書

**作成日**: YYYY-MM-DD  
**バージョン**: vX.X  

---

## 変更履歴

---

## 1. 概要
- 対象feature
- テスト対象範囲

---

## 2. テストケース
### [テストケースID] [テストケース名]
- テスト対象（クラス名、メソッド名）
- テスト目的
- 前提条件（初期状態）
- 入力（具体的な型、値）
- 期待出力（具体的な型、値）

```

---

#### 4.8 実装タスク管理書（/docs/_plans/tasks_impl.md）

**目的**: 未完了の実装タスクを、参照すべき設計書と紐付けて管理する。

```markdown
# タスク一覧

## DBへのカラム追加

- 対象: DB
- 内容: DBのEquipmentテーブルに説明カラムを追加する
- Status: To do
- 参照設計書: /docs/Common-DB_Design.md > 3.2 Equipmentテーブル設計
```

- 各タスクは Markdown の見出しと本文で記載し、表形式は使用しないこと。
- 見出しには prefix を付けず、実装内容のみを簡潔に記載すること。
- 本文は箇条書きとし、対象レイヤー名または対象feature名、Status、rootからのパスで記述した参照設計書、設計書セクション名をそれぞれ記載すること。
- `Status` は `To do` または `In progress` のみを使用すること。
- 完了したタスクは `/docs/_plans/tasks_impl.md` から削除すること。

---

#### 4.9 テスト実装タスク管理書（/docs/_plans/tasks_testimpl.md）

**目的**: 未完了のテスト実装タスクを、参照すべきテスト設計書と紐付けて管理する。

```markdown
# テスト実装タスク一覧

## SegmentsPageVm_LoadSegmentsAsync

- テストケースID: Common-Service-Test001
- テストケースID: [FeatureName]-Test001
```

- 本文は `テストケースID` の箇条書きのみを記載すること。
- `テストケースID` は対応するテスト設計書に記載された ID をそのまま記載すること。
- 完了したタスクは `/docs/_plans/tasks_testimpl.md` から削除すること。