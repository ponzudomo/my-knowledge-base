# workflows ディレクトリについて

このディレクトリは GitHub Actions のワークフロー（CI/CD、自動化タスクなど）を管理するためのものです。

## ディレクトリ構成
- `main.yml`: プッシュ・プルリクエスト時のCI（Python/Node.js/C++/テスト自動化）
- `lint.yml`: 静的解析・Lintチェック
- `doc.yml`: ドキュメント生成・Markdownチェック
- `release.yml`: タグpush時のリリース自動化
- `study/`: 学習・実験用ワークフロー（サンプル・検証用YAML、README付き）

## 運用・記述方針
- すべてのワークフローファイルは YAML 形式（.yml）で記述する。
- ファイル名・内容は役割が明確になるように命名・記述する。
- 各ワークフローにはコメントで目的・トリガー・主要なジョブ内容を明記する。
- secrets や個人情報は絶対に含めない。
- 必要に応じてバッジや通知設定も活用する。
- 学習・実験用は `study/` フォルダにまとめ、運用ワークフローと分離する。

## 参考
- [GitHub Actions公式ドキュメント](https://docs.github.com/ja/actions)
- [ワークフローのベストプラクティス](https://docs.github.com/ja/actions/using-workflows/workflow-syntax-for-github-actions)
- [Awesome Actions](https://github.com/sdras/awesome-actions)
