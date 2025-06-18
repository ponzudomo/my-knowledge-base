---
applyTo: "**"
---

# DatabaseStructure.instructions.md

このファイルは、データベース設計・構造に関する指針やベストプラクティスをまとめたものです。

## 基本方針

- 正規化を意識し、冗長なデータを避ける。
- テーブル名・カラム名は英語（小文字、snake_case）で意味が明確なものを使う。
- 主キー・外部キー・インデックスを適切に設計する。
- ER 図やスキーマ図を活用し、構造を可視化する。
- マイグレーションやバージョン管理を徹底する。

## 推奨事項

- テーブルごとに README やコメントで役割・仕様を明記する。
- 複雑なリレーションや制約はドキュメント化する。
- セキュリティ（SQL インジェクション対策、権限管理）を考慮する。

## 参考

- [PostgreSQL 公式: Database Design](https://www.postgresql.org/docs/current/datatype.html)
- [MySQL 公式: Database Design](https://dev.mysql.com/doc/)
- [ER 図作成ツール: dbdiagram.io](https://dbdiagram.io/)
