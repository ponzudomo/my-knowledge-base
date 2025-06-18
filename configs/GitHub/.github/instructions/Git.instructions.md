---
applyTo: "*.gitattributes,*.gitignore,*.gitmodules"
---

## Description

このファイルは Git に関する GitHub Copilot への指示と、一般的な利用規約やベストプラクティスをまとめたものです。
Copilot がより適切なサポートを提供し、開発者が一貫性のあるバージョン管理を行うためのガイドラインとして機能します。

## Purpose

- Copilot に対し、Git の操作や設定ファイル ( `.gitignore` など) の作成・編集における注意点を指示する。
- 開発者が参照するための、Git の基本的な利用規約やブランチ戦略、コミットメッセージの書き方などを提供する。
- リポジトリの履歴の可読性、保守性を高める。

## Usage

- Copilot はこの指示を読み込み、Git 関連の提案やファイル生成に活用する。
- 開発者はブランチ作成、コミット、マージなどの操作を行う際にこの規約を参照する。

## Key Files and Folders

- `.git/`: Git リポジトリの本体 (通常は直接編集しない)。
- `.gitignore`: Git の追跡対象外にするファイルやディレクトリを指定するファイル。
- `.gitattributes`: パスごとの属性 (行末コードの扱いなど) を指定するファイル。
- `.gitmodules`: サブモジュールを使用する場合の設定ファイル。

## For GitHub Copilot

### 全体の方針 (General Policy)

- このリポジトリの `general.instructions.md` に記載された全体方針に従うこと。
- Pro Git (特に日本語版) や Atlassian Git Tutorial などの信頼できる情報源を参考にすること。
- コミットメッセージの品質を重視すること。
- ブランチ戦略の基本 (例: Git Flow, GitHub Flow) を理解し、適切な提案を行うこと。

### コミットメッセージ (Commit Messages)

- **形式**: Conventional Commits の規約を推奨する。
  - 1 行目: `<type>(<scope>): <subject>` (例: `feat(api): add user authentication endpoint`)
    - `type`: `feat` (新機能), `fix` (バグ修正), `docs` (ドキュメント), `style` (コードスタイル), `refactor` (リファクタリング), `test` (テスト追加・修正), `chore` (ビルドプロセスや補助ツールの変更など)
    - `scope` (任意): 変更範囲を示す (例: `api`, `ui`, `parser`)
    - `subject`: 50 文字以内を目安に、簡潔に変更内容を記述する。動詞の原形から始める。
  - 2 行目: 空行
  - 3 行目以降: 詳細な説明 (変更の理由、影響範囲など)。必要に応じて記述する。1 行あたり 72 文字程度で折り返す。
- **言語**: 可能であれば英語で記述することを推奨するが、プロジェクトの規約に従う。
- **内容**: 「何を変更したか」だけでなく「なぜ変更したか」も記述するよう促す。

### ブランチ戦略 (Branching Strategy)

- **基本**: `main` (または `master`) ブランチは常にリリース可能な状態を保つ。
- **フィーチャーブランチ**: 新機能の開発やバグ修正は、`main` からブランチを作成して行う (例: `feature/user-login`, `fix/issue-123`)。
- **プルリクエスト (Pull Requests) / マージリクエスト (Merge Requests)**:
  - フィーチャーブランチの変更を `main` にマージする際は、プルリクエスト (またはマージリクエスト) を使用する。
  - コードレビューを経てからマージすることを推奨する。
  - マージ前にローカルでリベース (`git rebase -i main`) してコミット履歴を整理することを検討する。
- **タグ (Tags)**:
  - リリースポイントにはタグ (`git tag -a v1.0.0 -m "Version 1.0.0"`) を打つことを推奨する。

### `.gitignore` の作成・編集

- GitHub の [gitignore](https://github.com/github/gitignore) リポジトリにあるテンプレートを参考に、プロジェクトの言語やフレームワークに応じた適切な `.gitignore` ファイルを生成する。
- OS 固有のファイル (`.DS_Store`, `Thumbs.db` など)、IDE やエディタの設定ファイル (`.vscode/`, `.idea/` など)、コンパイル成果物、依存ライブラリ (`node_modules/`, `vendor/` など) を適切に無視するよう設定する。
- コメント (`#`) を活用して、なぜ特定のファイル/ディレクトリを無視するのか理由を記述することを推奨する。

### 一般的な操作 (General Operations)

- `git add .` のような包括的な追加よりも、`git add <file>` や `git add -p` で変更内容を確認しながらステージングすることを推奨する。
- `git pull` の代わりに `git fetch` と `git merge` (または `git rebase`) を分けて実行し、リモートの変更を確認してからマージすることを検討する。
- `git push --force` は、共有ブランチに対しては極力使用しない。使用する場合は、他の開発者と十分に調整した上で行う。

### 非推奨事項 (Discouraged Practices)

- 大きすぎるコミット。関連性の高い変更をまとめて、論理的な単位でコミットする。
- バイナリファイルや機密情報をリポジトリにコミットすること (Git LFS や `.gitignore` を適切に利用する)。
- コミットメッセージのない、あるいは意味不明なコミット。
