---
applyTo: "*.db,*.sqlite,*.sql"
---

## Description

このファイルは Database に関する GitHub Copilot への指示と、一般的なデータベース設計および運用規約をまとめたものです。
Copilot がより適切なサポートを提供し、開発者が一貫性のあるデータベース設計を行うためのガイドラインとして機能します。

## Purpose

- Copilot に対し、データベース設計および運用におけるベストプラクティス、注意点を指示する。
- 開発者が参照するための、データベース設計および運用の基本的な規約を提供する。
- データの整合性、保守性、効率性を高める。

## Usage

- Copilot はこの指示を読み込み、データベース関連のコード生成や提案に活用する。
- 開発者は新しいデータベースを設計する際や、既存のデータベースをレビューする際にこの規約を参照する。

## Key Files and Folders

- `*.db`, `*.sqlite`: データベースファイル。
- `schema.sql`: データベーススキーマを定義するファイル。
- `data.sql`: 初期データを挿入するファイル。
- `migrations/`: データベースのマイグレーションファイルを格納するディレクトリ。

## For GitHub Copilot

### 全体の方針 (General Policy)

- このリポジトリの `general.instructions.md` に記載された全体方針に従うこと。
- データベース設計の原則 (正規化、非正規化のバランス) を意識すること。
- データベースの種類 (MySQL, PostgreSQL, SQLite, SQL Server, Oracle など) に応じたベストプラクティスを提案すること。
- 可読性と保守性を重視した設計を推奨すること。
- パフォーマンスを意識した設計を推奨すること。

### 命名規則 (Naming Conventions)

- テーブル名: `snake_case` (例: `user_profiles`, `order_items`)
- カラム名: `snake_case` (例: `user_id`, `created_at`)
- インデックス名: `idx_<table_name>_<column_name>` (例: `idx_user_profiles_user_id`)
- 外部キー名: `fk_<table_name>_<referenced_table_name>` (例: `fk_order_items_orders`)
- ストアドプロシージャ名: `snake_case` (例: `get_user_orders`)
- ファイル名: `snake_case.sql` (例: `create_tables.sql`, `insert_data.sql`)

### データベース設計の原則 (Database Design Principles)

- **正規化 (Normalization)**:
  - 第 3 正規形 (3NF) を基本とし、必要に応じて非正規化を検討する。
  - 冗長性を最小限に抑える。
- **キーの設計**:
  - 主キー (Primary Key) は一意であることを保証する。
  - 外部キー (Foreign Key) を適切に使用してリレーションを定義する。
  - インデックスを適切に設計し、クエリのパフォーマンスを向上させる。
- **データ型の選択**:
  - 必要以上に大きなデータ型を使用しない (例: `VARCHAR(255)` の乱用を避ける)。
  - 数値型は用途に応じて適切に選択する (例: `INT`, `BIGINT`, `DECIMAL` など)。
- **NULL の扱い**:
  - 必要に応じて `NOT NULL` 制約を付与する。
  - NULL 値を比較する場合は `IS NULL` または `IS NOT NULL` を使用する。

### データベース運用のベストプラクティス (Database Operations Best Practices)

- **バックアップ**:
  - 定期的にデータベースのバックアップを取得する。
  - バックアップファイルは安全な場所に保存する。
- **モニタリング**:
  - データベースのパフォーマンスを定期的にモニタリングする。
  - クエリの実行計画を確認し、必要に応じて最適化する。
- **セキュリティ**:
  - データベースユーザーの権限を最小限に抑える。
  - SQL インジェクションを防ぐためにプリペアドステートメントを使用する。
  - データの暗号化を検討する。
- **マイグレーション**:
  - スキーマ変更はマイグレーションツール (例: Flyway, Liquibase) を使用して管理する。
  - マイグレーションファイルには変更内容を明確に記述する。

### 非推奨事項 (Discouraged Practices)

- SELECT \* の使用。必要なカラムを明示的に指定する。
- 暗黙的な型変換。
- データベース固有の拡張機能に過度に依存する。
- トリガーの乱用 (必要な場合に限定する)。
- 大量のデータを処理する際の非効率なクエリ。

---
