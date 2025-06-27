# GitHub Copilotのカスタム

# About

## Description

GitHub Copilotにはカスタム指示を与えることができる。
ディレクトリ内に特定の名前のファイルを置くことで、ディレクトリ全体に対して適用させられる。

## Purpose

**1. 一貫性のある開発**
- プロジェクトごとの細かい規約やコンテクストを指定できる
- なんなら適用先のファイルを指定できるので、各言語のコーディング規約まで読んでもらえる
- 自分好みのわがままな開発スタイルやフローを押しつけられる

**2. プロンプトの記述コスト削減**
- 前提情報をまとめて投げられるので、何度も同じ情報を与えずに済み効率的

**3. 学習面での補助**
- 通常はタスクを投げても学習面の面倒までは見てくれないので、個別にまとめて設定しておく必要がある
- 事前に設定をしておけば毎回指示した場所に詳細な解説を吐いてくれる
- 学習ソースを添えてもらうことも可能

## Usage

基本的には`.github/copilot-instructions.md` にまとめて書かれることが多い。

`.github/instructions/*.instructions.md` といったようにファイルを分割して設定することもできる。
この場合指示の適用範囲を個別に定めることができるため、大規模なプロジェクトや複数の言語を扱う場合に便利。

vscode側で色々設定するとなおよいらしい

### ディレクトリ構成例

```markdown
.
└── 📂 .github/
    └── 📂 instructions/
        ├── ⚙️ general.instructions.md
        ├── ⚙️ react.instructions.md
        └── ⚙️ testing.instructions.md
```

---

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

## Key Files and Folders
-

## For GitHub Copilot
-

```

### applyToの役割
- applyToはFront Matterで、この指示をどのファイルに適用するかを指定できる<br>
- globパターンが使える<br>
　  　
---

# Problem - Try

## 1. `instructions.md` の内容を忘れてしまう

### 考えられる原因

他の情報に圧迫されて、ウィンドウから追い出されているように見える
現状の仕様として、コンテキストの保持に優先順位はつけられないようである

### 対処法

- 不必要な情報は与えない
- 明示的に再読み込みを指示
- 都度セッションを再起動しコンテキストをリセット
- VSCodeのスニペットツールを活用する


## 2. ファイルを読み込んでくれない

### 考えられる原因

#### インデックス作成の遅延や失敗
Copilot Agentは、プロジェクト内のファイルを効率的に検索・参照するために裏側でファイルのインデックスを作成している。
プロジェクトが大きい場合やファイルの変更が頻繁な場合に、このインデックス作成が追いつかず、ファイルを見つけられないことがある。

#### 一時的な不具合やリソース競合
Copilot拡張機能自体の、あるいは他の拡張機能との間で一時的な不具合やリソースの競合が発生し、ファイルアクセスに失敗することがある。

#### 接続の問題
GitHubのサーバーとの通信が一時的に不安定になることで、リクエストが失敗している可能性も考えられる。

### 対処法

- 読み込ませるファイルを絞る (もしくはディレクトリ自体を整理する)
- ファイルパスを具体的に指示
- キャッシュのクリア
- Copilotガチャ

---

# 参考文献リスト
- [GitHub Copilot のリポジトリ カスタム命令を追加する - GitHub Docs](https://docs.github.com/ja/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot)
- [April 2025 (version 1.100) - Visual Studio Code](https://code.visualstudio.com/updates/v1_100)
- [Use .instructions.md files - Visual Studio Code](https://code.visualstudio.com/docs/copilot/copilot-customization#_use-instructionsmd-files)
- [GitHub Copilot の指示書が複数ファイル対応に！ルールを用途別に整理できる新機能 - Zenn](https://zenn.dev/m10maeda/articles/copilot-multi-instruction-files#github-copilot-%E3%81%AE%E6%8C%87%E7%A4%BA%E3%81%8C%E3%82%82%E3%81%A3%E3%81%A8%E6%9F%94%E8%BB%9F%E3%81%AB%EF%BC%81vscode-v1.100.0-%E3%81%AE%E6%96%B0%E6%A9%9F%E8%83%BD)
- [Visual Studio Code の git 連携機能と git コマンドについて - Qiita](https://qiita.com/satokaz/items/4660ce57ca8eb456a096)
