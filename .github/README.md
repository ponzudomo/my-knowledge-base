# このフォルダについて: GitHubに関する設定一覧

このフォルダには、現状
- `README.md`: 設定方法に関する勉強メモ、フォルダの使い方についての説明
- `*.instructions.md`: 各`instructions.md`のテンプレート

が入っている。たぶんこれから増える。

## todo
テンプレを使う際は、以下に沿って手直しを行うこと。
- `general.instructions.md`の、個々のリポジトリに関する説明を埋める
- 各言語の`instructions.md`に各々のプロジェクトのコーディング規約を適用させる (デフォルトでは公式ドキュメント通りの内容が書いてある)
- 中身をよく読み、各々のプロジェクトの方針に沿って書き換える (デフォルトではそれっぽいことが書いてある)

# GitHub Copilotのカスタムについて
GitHub Copilotにはカスタム指示を与えることができる。<br>
ディレクトリ内に特定の名前のファイルを置くことで、ディレクトリ全体に対して適用させられる。

基本的には`.github/copilot-instructions.md` にまとめて書かれることが多い。
`.github/instructions/*.instructions.md` にファイルを分割して設定することもできる。
この場合指示の適用範囲を個別に定めることができるため、大規模なプロジェクトや複数の言語を扱う場合に便利らしい。

### ディレクトリ構成例
```markdown
.
└── 📂 .github/
    └── 📂 instructions/
        ├── ⚙️ general.instructions.md
        ├── ⚙️ react.instructions.md
        └── ⚙️ testing.instructions.md
```

# `.instructions.md` の書き方
## 例形

```markdown
---
applyTo: '**'
---

# (名前)

## Description

## Purpose

## Usage
```

## Key Files and Folders
-

## For GitHub Copilot
-

```
### applyToの役割
- applyToはFront Matterで、この指示をどのファイルに適用するかを指定できる<br>
- globパターンが使える<br>
　  　

# 参考文献リスト
- [GitHub Copilot のリポジトリ カスタム命令を追加する - GitHub Docs](https://docs.github.com/ja/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot)
- [April 2025 (version 1.100) - Visual Studio Code](https://code.visualstudio.com/updates/v1_100)
- [Use .instructions.md files - Visual Studio Code](https://code.visualstudio.com/docs/copilot/copilot-customization#_use-instructionsmd-files)
- [GitHub Copilot の指示書が複数ファイル対応に！ルールを用途別に整理できる新機能 - Zenn](https://zenn.dev/m10maeda/articles/copilot-multi-instruction-files#github-copilot-%E3%81%AE%E6%8C%87%E7%A4%BA%E3%81%8C%E3%82%82%E3%81%A3%E3%81%A8%E6%9F%94%E8%BB%9F%E3%81%AB%EF%BC%81vscode-v1.100.0-%E3%81%AE%E6%96%B0%E6%A9%9F%E8%83%BD)
- [Visual Studio Code の git 連携機能と git コマンドについて - Qiita](https://qiita.com/satokaz/items/4660ce57ca8eb456a096)
