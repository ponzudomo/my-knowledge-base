---
applyTo: "**"
---

# ファイル・フォルダの命名について

このファイルは、リポジトリ内でのファイル名・フォルダ名の命名規則やベストプラクティスをまとめたものです。

## 基本方針

- 英語（小文字、snake_case または kebab-case）を基本とする。
- 意味が明確で、内容や役割が一目で分かる名前を付ける。
- 略語や省略形は一般的なもの以外は避ける。
- ファイル名・フォルダ名にはスペースや全角文字を使わない。
- テストファイルや設定ファイルは、用途が分かるように suffix/prefix を付ける（例: `*.test.cpp`, `settings.json`）。

## 具体例

- `main.cpp`, `index.html`, `config.yaml`, `README.md`
- `cheatsheets/`, `snippets/`, `experiments/`, `notes/`
- `atcoder_utils.cpp`, `user_profile.sql`

## テストファイルの命名

- Google Test などのテストは `*.test.cpp` や `*_test.cpp` 形式を推奨。
- テスト対象のファイル名＋`_test` を基本とする。

## 参考

- [Google C++ Style Guide: File Names](https://google.github.io/styleguide/cppguide.html#File_Names)
- [Python Style Guide: Package and Module Names](https://peps.python.org/pep-0008/#package-and-module-names)
- [GitHub Docs: Working with files](https://docs.github.com/ja/repositories/working-with-files)
