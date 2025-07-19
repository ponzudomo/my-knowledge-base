# 使いまわしそうなプロンプト一覧

---

## 着手
```
リポジトリ全体を読み込みなおせ。
.ponzu_domo/tasks/(案件番号)/copilot-instructions.md の内容を全て読み、key filesとして記載されたその他のファイルについても全て確認しろ。
その後、SRS.mdを再度読み込み、中身を全て読め。これに基づいて、blueprint.mdに変更すべきファイルと内容をまとめろ。その際、表形式でまとめろ。
これからこれらのドキュメントに沿って私の手助けをしてもらう。
まずは案件を進めるにあたっての方針を擦り合わせたい。blueprint.mdに実装方針をまとめろ。
```

```
次に、変更する必要のあるファイルについて解説をしてもらう。
file-descriptions/配下に解説ファイルを生成しろ。
```

## SRS手直し
```
リポジトリ全体を読み込みなおせ。中身に変更がある。
.ponzu_domo/tasks/(案件番号)/copilot-instructions.md の内容を全て読み、key filesとして記載されたその他のファイルについても全て確認しろ。
その後、SRS.mdを再度読み込み、中身を全て読め。最新のSRS.mdに基づいて、blueprint.mdに変更すべきファイルと内容をまとめろ。その際、表形式でまとめろ。
これからこれらのドキュメントに沿って私の手助けをしてもらう。
まずは案件を進めるにあたっての方針を擦り合わせたい。最新のSRS.mdに基づいて、blueprint.mdの内容を手直ししろ。
```

## コンテキストウィンドウがギチギチになってそうな時
```
そのまま作業を続けてほしい。
ただし、以下の5つの内容を読みこみなおし、中身をすべて確認すること。
以下の内容は、忘れそうになったタイミングで都度読み込みなおし、中身を全て確認すること。
常に頭に入れておくこと。
.github/instructions/general.instructions.md
.ponzu_domo/README.md
.ponzu_domo/tasks/(案件番号)/README.md
.ponzu_domo/tasks/(案件番号)/file-descriptions/*
.ponzu_domo/tasks/(案件番号)/blueprint.md
```

## 方針変更時
```
blueprintの中身を手直しした。もう一度ファイルを読み込みなおし、最後まで全て読んで。
変更内容に応じてfile-descriptionのoverview,mdも手直しして。
ただし、以下の内容を再度読み込みなおし、内容をすべて読み込み、常に頭に入れておくこと。
.github/instructions/general.instructions.md
.ponzu_domo/README.md
.ponzu_domo/tasks/153829/README.md
.ponzu_domo/tasks/153829/blueprint.md
```

## 行き詰まったとき
```
今までの作業内容をすべて忘れなさい。
リポジトリ全体を読み込みなおしなさい。
それから、以下の3つのファイルの内容を全て確認しなさい。
.github/instructions/general.instructions.md
.ponzu_domo/README.md
.ponzu_domo/tasks/(案件番号)/README.md
これからこれらのドキュメントに沿って私の手助けをしてもらう。
まずは案件を進めるにあたっての方針を擦り合わせたい。blueprint.mdに書かれた実装方針の手直しをしなさい。
この際、既に存在する修正案のファイルは無視して作業を進めなさい。
```

```
blueprint.mdの内容に基づき、既に存在する修正案を全て手直ししなさい。
根本的に構造を変えても構わない。
```

## 確認作業
```
もう一度.ponzu_domo/tasks/(案件番号)/README.mdの中身を読みなさい。
指示内容と今の変更内容(.ponzu_domo/tasks/(案件番号)/after/ 以下)が噛み合っているか確認しなさい。
.ponzu_domo/tasks/(案件番号)/blueprint.mdの内容を確認し、実装方針に沿って作業を進めているか確認しなさい。
今の進捗状況(.ponzu_domo/tasks/(案件番号)/after/ 以下)を.ponzu_domo/tasks/(案件番号)/change-summary/ 以下に改めてまとめなさい。
主目的はユーザーの学習の手助けである。初学者でも分かるように丁寧に中身を解説し、おすすめの学習ソースまでつけること。
```

## ひとしきり終わったら
```
現段階での変更内容を .ponzu_domo/tasks/(案件番号)/change-summary/ 以下にまとめなさい。
.ponzu_domo/tasks/(案件番号)/blueprint.md に書かれた実装方針に変更や補足があれば追記しなさい。
主目的はユーザーの学習の手助けである。初学者でも分かるように丁寧に中身を解説し、おすすめの学習ソースまでつけること。
```
