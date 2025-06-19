---
applyTo: "*.php"
---

## Description

このファイルは PHP に関する GitHub Copilot への指示と、一般的なコーディング規約をまとめたものです。<br>
Copilot がより適切なサポートを提供し、開発者が一貫性のあるコードを記述するためのガイドラインとして機能します。

## Purpose

- Copilot に対し、PHP のプロジェクトにおけるコーディングスタイル、ベストプラクティス (PSR など)、注意点を指示する。<br>
- 開発者が参照するための、PHP の基本的なコーディング規約を提供する。<br>
- コードの可読性、保守性、一貫性、セキュリティを高める。

## Usage

- Copilot はこの指示を読み込み、PHP のコード生成や提案に活用する。<br>
- 開発者は新しいコードを記述する際や、既存のコードをレビューする際にこの規約を参照する。

## Key Files and Folders

- `*.php`: PHP スクリプトファイル。<br>
- `composer.json`: プロジェクトの依存関係やオートロード設定を定義するファイル (Composer を使用する場合)。<br>
- `public/index.php`: Web アプリケーションのフロントコントローラー (一般的なパターン)。<br>
- `src/`: ソースコードディレクトリ (PSR-4 オートロード規約に準拠する場合)。<br>
- `vendor/`: Composer によってインストールされた依存パッケージが格納されるディレクトリ。<br>
- `tests/`: テストコードディレクトリ。

## For GitHub Copilot

### 全体の方針 (General Policy)

- このリポジトリの `general.instructions.md` に記載された全体方針に従うこと。<br>
- PHP-FIG の PSR (PHP Standards Recommendations) を強く意識し、特に PSR-1, PSR-12, PSR-4 を遵守するよう促すこと。<br>
- PHP 公式ドキュメント (php.net) を優先的に参照すること。<br>
- 可読性と保守性を重視したコードを生成すること。<br>
- オブジェクト指向プログラミングの原則を推奨する。<br>
- セキュリティのベストプラクティス (OWASP Top 10 など) を意識したコード生成を心がける。

### 命名規則 (Naming Conventions) - PSR-1, PSR-12 準拠

- クラス名: `PascalCase` (例: `UserProfile`, `DatabaseConnection`)<br>
- メソッド名: `camelCase` (例: `getUserById`, `calculateTotalPrice`)<br>
- 定数 (クラス定数含む): `UPPER_SNAKE_CASE` (例: `MAX_LOGIN_ATTEMPTS`, `DEFAULT_TIMEOUT`)<br>
- プロパティ名: `camelCase` (PSR-1 では特に規定なし、慣習として `camelCase`)<br>
- 変数名: `camelCase`<br>
- 関数名 (グローバルスコープ): `snake_case` (歴史的な経緯。新規プロジェクトではクラス化を推奨)<br>
- ファイル名: クラス名と一致させることを推奨 (PSR-4)。`PascalCase.php`。

### コーディングスタイル (Coding Style) - PSR-12 準拠

- PHP タグ: `<?php` と `<?= ?>` を使用。`<?` は使用しない。<br>
- 文字エンコーディング: UTF-8 (BOM なし)。<br>
- インデント: スペース 4 つ。タブは使用しない。<br>
- 1 行の最大文字数: ソフトリミット 80 文字、ハードリミット 120 文字。<br>
- 制御構造のキーワードの後にはスペースを 1 つ入れる (例: `if `, `foreach `)。<br>
- メソッドや関数の開き括弧 `{` は、宣言の次の行に書く。<br>
- 制御構造の開き括弧 `{` は、宣言と同じ行に書く。<br>
- 可視性: 全てのプロパティとメソッドに `public`, `protected`, `private` のいずれかを明示する。<br>
- コメント:<br>
  - PHPDoc (`/** ... */`) 形式をクラス、メソッド、関数に使用する。<br>
  - 通常のコメントは `//` または `#` を使用する。

### PHP 特有の規約 (Specific Conventions for PHP)

- **エラーハンドリング (Error Handling)**:<br>
  - 例外 (`Exception` クラスとそのサブクラス) を積極的に使用する。<br>
  - `@`演算子によるエラー抑制は極力避ける。<br>
  - `error_reporting(E_ALL)` と `display_errors` (開発環境) を適切に設定する。<br>
- **型宣言 (Type Declarations)** (PHP 7.0+):<br>
  - 引数の型、戻り値の型を可能な限り指定する。<br>
  - スカラー型宣言 (`int`, `float`, `string`, `bool`, `array`, `callable`) やクラス名を指定する。<br>
  - PHP 7.4+ ではプロパティの型宣言も活用する。<br>
- **厳密な型付け (Strict Types)** (PHP 7.0+):<br>
  - `declare(strict_types=1);` をファイルの先頭に記述することを推奨。<br>
- **オートロード (Autoloading)**:<br>
  - Composer と PSR-4 オートロード規約に従うことを強く推奨。<br>
- **依存性管理 (Dependency Management)**:<br>
  - Composer を使用してプロジェクトの依存関係を管理する。<br>
- **セキュリティ (Security)**:<br>
  - SQL インジェクション対策: プリペアドステートメント (PDO, MySQLi) を使用する。<br>
  - XSS (クロスサイトスクリプティング) 対策: 出力時のエスケープ (`htmlspecialchars` など) を徹底する。<br>
  - CSRF (クロスサイトリクエストフォージェリ) 対策: トークンを使用する。<br>
  - パスワードハッシュ: `password_hash()` と `password_verify()` を使用する。<br>
  - ファイルアップロード: 検証を厳格に行う。<br>
- **スーパーグローバル変数**: `$_GET`, `$_POST`, `$_SESSION` などは直接アクセスせず、ラッパー関数やクラスを通じてアクセスすることを検討する (特に大規模プロジェクト)。<br>
- **テンプレートエンジン**: 生の PHP を HTML に埋め込むよりも、Twig, Blade, Smarty などのテンプレートエンジンの利用を検討する。

### 非推奨事項 (Discouraged Practices)

- `mysql_*` 関数群 (廃止)。MySQLi または PDO を使用する。<br>
- `eval()` や `exec()` の安易な使用。<br>
- グローバル変数の多用。<br>
- 短縮オープンタグ `<?` ( `short_open_tag` ディレクティブに依存するため)。<br>
- エラー制御演算子 `@` の乱用。
