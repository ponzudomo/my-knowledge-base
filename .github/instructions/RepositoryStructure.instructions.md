---
applyTo: "**"
---

# リポジトリの構造について

このファイルは、このリポジトリのディレクトリ構成や各フォルダ・ファイルの役割についてまとめたものです。

## 基本方針

- 各ディレクトリ・ファイルは役割ごとに整理し、可読性・保守性を高める。
- 新しい技術やカテゴリが増えた場合は、既存の構造を参考に一貫性を持って追加する。

## 主なディレクトリ・ファイル

- `README.md`: リポジトリ全体の概要、目的、構成を記載。
- `cheatsheets/`: よく使うコマンドやショートカットのチートシートを OS/用途ごとに分類。
- `configs/`: 各種ツールやエディタの設定ファイル、セットアップガイド。
- `experiments/`: 新しい技術やアイデアの検証用コード。
- `notes/`: 学習ノートやメモ、雑多な情報。
- `prompts/`: AI ツール用のプロンプト集。
- `reference/`: README テンプレートやドキュメントのベストプラクティス。
- `snippets/`: 言語ごとの再利用可能なコードスニペット。
- `.github/`: GitHub 用の設定やワークフロー、Copilot 向け instructions。

## 追加の指針

- 新規フォルダ・ファイルを追加する際は、README などで役割を明記する。
- 役割が重複しないように整理し、不要になったファイルはアーカイブまたは削除を検討する。

## 参考

- [GitHub Docs: About READMEs](https://docs.github.com/ja/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)
- [Google Engineering Practices: Project Structure](https://google.github.io/styleguide/)
