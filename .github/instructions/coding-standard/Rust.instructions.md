---
applyTo: "*.rs"
---

## Description

このファイルは Rust に関する GitHub Copilot への指示と、一般的なコーディング規約をまとめたものです。<br>
Copilot がより適切なサポートを提供し、開発者が一貫性のあるコードを記述するためのガイドラインとして機能します。

## Purpose

- Copilot に対し、Rust のプロジェクトにおけるコーディングスタイル、ベストプラクティス、注意点を指示する。<br>
- 開発者が参照するための、Rust の基本的なコーディング規約を提供する。<br>
- コードの可読性、保守性、一貫性を高める。

## Usage

- Copilot はこの指示を読み込み、Rust のコード生成や提案に活用する。<br>
- 開発者は新しいコードを記述する際や、既存のコードをレビューする際にこの規約を参照する。

## Key Files and Folders

- `*.rs`: Rust のソースファイル。<br>
- `Cargo.toml`: プロジェクトマニフェストファイル。<br>
- `src/`: ソースコードディレクトリ。<br>
- `tests/`: テストコードディレクトリ。

## For GitHub Copilot

### 全体の方針 (General Policy)

- このリポジトリの `general.instructions.md` に記載された全体方針に従うこと。<br>
- Rust 公式ドキュメント (The Book, Rust by Example, Standard Library Documentation) を優先的に参照すること。<br>
- 可読性と保守性を重視したコードを生成すること。<br>
- `rustfmt` によるフォーマットを前提とすること。<br>
- `clippy` の提案に留意し、可能な限り従うこと。

### 命名規則 (Naming Conventions)

- モジュール、クレート、型 (struct, enum, trait)、型エイリアス: `PascalCase`<br>
- 関数、メソッド、変数、ローカル変数、マクロ: `snake_case`<br>
- 定数 (const, static): `UPPER_SNAKE_CASE`

### コーディングスタイル (Coding Style)

- フォーマット: `rustfmt` のデフォルト設定に従う。<br>
- 1 行の最大文字数: 100 文字 ( `rustfmt` のデフォルトに近い)。<br>
- コメント:<br>
  - ドキュメンテーションコメントは `///` (アイテムの外側) または `//!` (アイテムの内側) を使用し、Markdown 形式で記述する (Rustdoc)。<br>
  - 通常のコメントは `//` を使用する。<br>
- モジュール: `mod.rs` または `{module_name}.rs` を適切に使い分ける。

### Rust 特有の規約 (Specific Conventions for Rust)

- **所有権と借用 (Ownership and Borrowing)**:<br>
  - 所有権システムを正しく理解し、ライフタイムを適切に管理する。<br>
  - 不要なクローン (`.clone()`) を避け、借用 (`&`, `&mut`) を最大限活用する。<br>
- **エラーハンドリング (Error Handling)**:<br>
  - `Result<T, E>` をエラーが発生しうる関数の戻り値として積極的に使用する。<br>
  - `Option<T>` を値が存在しない可能性がある場合に使用する。<br>
  - `unwrap()` や `expect()` の使用は、プログラムのロジック上絶対にエラーが発生しないと確信できる場合や、テストコード、サンプルコードに限定する。それ以外の場合は `match` や `if let`、`?` 演算子で適切に処理する。<br>
  - パニック (`panic!`) は回復不能なエラー、またはプログラムの不変条件が破壊された場合に限定する。ライブラリコードでは基本的に避ける。<br>
- **型システム (Type System)**:<br>
  - トレイト (Trait) を活用して抽象化とコードの再利用性を高める。<br>
  - ジェネリクスを適切に使用して、柔軟で型安全なコードを記述する。<br>
  - `newtype` パターンを活用して、型の安全性を高める。<br>
- **並行処理 (Concurrency)**:<br>
  - スレッドセーフティを意識し、`Send` トレイトと `Sync` トレイトを理解する。<br>
  - `Arc`, `Mutex`, `RwLock` などを適切に使用する。<br>
- **マクロ (Macros)**:<br>
  - 宣言的マクロ (`macro_rules!`) や手続きマクロを適切に使用して、コードの冗長性を減らす。ただし、過度な使用は可読性を損なう可能性があるため注意する。<br>
- **モジュールとクレート (Modules and Crates)**:<br>
  - クレートの API は明確に定義し、`pub` キーワードで公開範囲を適切に管理する。<br>
  - `pub(crate)`, `pub(super)` などを活用してカプセル化を強化する。

### 非推奨事項 (Discouraged Practices)

- `unsafe` コードの使用: 真に必要な場合を除き避ける。使用する場合は、その安全性の根拠をコメントで詳細に説明する。<br>
- 標準ライブラリで提供されている機能を安易に再実装すること。<br>
- 過度にネストしたコード。関数に切り出すなどして可読性を保つ。<br>
- 循環依存。
