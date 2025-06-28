# About `.ponzu_domo`

## Description

複数人で進めているプロジェクトにおける、私(ponzu_domo)専用の個人フォルダである。.gitignoreの対象。　
このフォルダ内のファイルは、他の開発者と共有されない。　
<br>

## Purpose

1. **要件定義**
　- {概形の把握, 状況整理, 実装方針作成} の補助
2. **タスクの自動化**
　- とりあえず書かせてから考えると圧倒的に業務効率が上がる
3. **学習の補助**
　- コードの解説　→ 理解の促進
　- 関連するキーワードの提示, 学習ソースの提案 → 学習フローの効率化
4. **作業内容の保存**
　- 変更前の状態, 変更後の状態, 変更内容, 学習メモ を同じ場所でまとめて管理したかった
　- 学習目的の個人用ローカルバージョン管理
<br>

## Usage

1.

---

## ディレクトリ構造

フォルダ内の構造は以下のようになっている。

```markdown
.
├── `compleated_tasks`/
│   └── (案件番号)
├── `memo`/
├── `tasks`/
│   └── (案件番号)/
│       ├── `before`/
│       ├── `change-summary`
│       │   ├── `overview.md`
│       │   └── (ファイルごとの修正内容)
│       ├── `file-descriptions`
│       │   ├── `overview.md`
│       │   └── (ファイルごとの解説)
│       ├── `blueprint.md`
│       ├── `copilot-instructions.md`
│       ├── `prompts.md`
│       └── `README.md`
├── `template`/
│   └── `task`/
├── `copilot-instructions.md`
└── `README.md`
```

---



---
