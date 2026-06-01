# Git Commit Message Instructions

Semantic Commit Message に基づいて記述すること。日本語を使用すること。

## 形式

```
<type>(<scope>): <subject>

<body>
```

## 記述ルール

- **type**: 以下から選択する
  - feat: (new feature for the user, not a new feature for build script)
  - fix: (bug fix for the user, not a fix to a build script)
  - docs: (changes to the documentation)
  - style: (formatting, missing semi colons, etc; no production code change)
  - refactor: (refactoring production code, eg. renaming a variable)
  - test: (adding missing tests, refactoring tests; no production code change)
  - chore: (updating grunt tasks etc; no production code change)

- **scope**: 変更対象となるモジュール・コンポーネント（省略可）
  - 例: `UI`, `Database` 等

- **subject**: 必ず日本語で記述すること、40字以内

- **body**: 必ず日本語で記述すること、100字以内
