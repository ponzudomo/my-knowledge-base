---
applyTo: "*.sql"
---

## Description

このファイルは SQL に関する GitHub Copilot への指示と、一般的なコーディング規約をまとめたものです。<br>
Copilot がより適切なサポートを提供し、開発者が一貫性のあるクエリを記述するためのガイドラインとして機能します。

## Purpose

- Copilot に対し、SQL のプロジェクトにおけるコーディングスタイル、ベストプラクティス、注意点を指示する。
- 開発者が参照するための、SQL の基本的なコーディング規約を提供する。
- クエリの可読性、保守性、効率性を高める。

## Usage

- Copilot はこの指示を読み込み、SQL のコード生成や提案に活用する。
- 開発者は新しいクエリを記述する際や、既存のクエリをレビューする際にこの規約を参照する。

## Key Files and Folders

- `*.sql`: SQL スクリプトファイル。
- `schema.sql`: データベーススキーマを定義するファイル。
- `data.sql`: 初期データを挿入するファイル。
- `queries/`: クエリを格納するディレクトリ。

## For GitHub Copilot

### 全体の方針 (General Policy)

- このリポジトリの `general.instructions.md` に記載された全体方針に従うこと。
- SQL の標準仕様 (ANSI SQL) を優先的に参照すること。
- データベースの種類 (MySQL, PostgreSQL, SQLite, SQL Server, Oracle など) に応じたベストプラクティスを提案すること。
- 可読性と保守性を重視したクエリを生成すること。
- パフォーマンスを意識したクエリを推奨すること。

### 命名規則 (Naming Conventions)

- テーブル名: `snake_case` (例: `user_profiles`, `order_items`)
- カラム名: `snake_case` (例: `user_id`, `created_at`)
- インデックス名: `idx_<table_name>_<column_name>` (例: `idx_user_profiles_user_id`)
- 外部キー名: `fk_<table_name>_<referenced_table_name>` (例: `fk_order_items_orders`)
- ストアドプロシージャ名: `snake_case` (例: `get_user_orders`)
- ファイル名: `snake_case.sql` (例: `create_tables.sql`, `insert_data.sql`)

### コーディングスタイル (Coding Style)

- キーワードはすべて大文字で記述する (例: `SELECT`, `FROM`, `WHERE`, `JOIN`)。
- テーブル名、カラム名は小文字で記述する。
- インデント: サブクエリや複雑な条件式にはスペース 2 つまたは 4 つでインデントを付ける。
- 1 行の最大文字数: 80〜100 文字程度を目安とする。
- コメント:
  - シングルラインコメントは `--` を使用する。
  - マルチラインコメントは `/* ... */` を使用する。
- クエリの各句 (SELECT, FROM, WHERE, JOIN など) は改行して記述する。

### SQL 特有の規約 (Specific Conventions for SQL)

- **データ型の選択**:
  - 必要以上に大きなデータ型を使用しない (例: `VARCHAR(255)` の乱用を避ける)。
  - 数値型は用途に応じて適切に選択する (例: `INT`, `BIGINT`, `DECIMAL` など)。
- **NULL の扱い**:
  - 必要に応じて `NOT NULL` 制約を付与する。
  - NULL 値を比較する場合は `IS NULL` または `IS NOT NULL` を使用する。
- **インデックスの使用**:
  - クエリのパフォーマンスを向上させるために適切なインデックスを作成する。
  - インデックスの作成は慎重に行い、不要なインデックスを避ける。
- **ジョイン (JOIN)**:
  - 必要に応じて `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL JOIN` を使い分ける。
  - 暗黙的なジョイン (WHERE 句での結合) は避ける。
- **トランザクション**:
  - データの整合性を保つためにトランザクション (`BEGIN`, `COMMIT`, `ROLLBACK`) を使用する。
- **エラーハンドリング**:
  - ストアドプロシージャやトリガー内で適切なエラーハンドリングを行う。
- **セキュリティ**:
  - SQL インジェクションを防ぐためにプリペアドステートメントを使用する。
  - データベースユーザーの権限を最小限に抑える。

### 非推奨事項 (Discouraged Practices)

- `SELECT *` の使用。必要なカラムを明示的に指定する。
- 暗黙的な型変換。
- データベース固有の拡張機能に過度に依存する。
- トリガーの乱用 (必要な場合に限定する)。
- 大量のデータを処理する際の非効率なクエリ。
