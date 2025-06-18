---
applyTo: "*.js,*.jsx,*.ts,*.tsx"
---

## Description

このファイルは JavaScript (TypeScript を含む) に関する GitHub Copilot への指示と、一般的なコーディング規約をまとめたものです。
Copilot がより適切なサポートを提供し、開発者が一貫性のあるコードを記述するためのガイドラインとして機能します。

## Purpose

- Copilot に対し、JavaScript/TypeScript のプロジェクトにおけるコーディングスタイル、ベストプラクティス、注意点を指示する。
- 開発者が参照するための、JavaScript/TypeScript の基本的なコーディング規約を提供する。
- コードの可読性、保守性、一貫性を高める。

## Usage

- Copilot はこの指示を読み込み、JavaScript/TypeScript のコード生成や提案に活用する。
- 開発者は新しいコードを記述する際や、既存のコードをレビューする際にこの規約を参照する。

## Key Files and Folders

- `*.js`, `*.jsx`: JavaScript および JSX ファイル。
- `*.ts`, `*.tsx`: TypeScript および TSX ファイル。
- `package.json`: プロジェクトの依存関係やスクリプトを定義するファイル。
- `tsconfig.json`: TypeScript のコンパイラオプションを設定するファイル。
- `node_modules/`: 依存パッケージがインストールされるディレクトリ (通常 `.gitignore` 対象)。
- `src/`, `lib/`, `dist/`: ソースコードやビルド済みファイルを格納する一般的なディレクトリ名。

## For GitHub Copilot

### 全体の方針 (General Policy)

- このリポジトリの `general.instructions.md` に記載された全体方針に従うこと。
- MDN Web Docs (JavaScript, TypeScript), Airbnb JavaScript Style Guide, Google JavaScript Style Guide, TypeScript Deep Dive などを参考にすること。
- 可読性と保守性を重視したコードを生成すること。
- ES6 (ECMAScript 2015) 以降のモダンな構文を積極的に使用する (プロジェクトのターゲット環境に合わせる)。
- TypeScript を使用する場合は、その型システムの利点を最大限に活用する。
- モジュールシステム (ES Modules: `import`/`export`) を使用する。

### 命名規則 (Naming Conventions)

- 変数、関数: `camelCase` (例: `myVariable`, `calculateValue`)
- クラス、コンストラクタ、enum (TypeScript): `PascalCase` (例: `UserProfile`, `ColorOption`)
- 定数 (変更されないグローバルな値): `UPPER_SNAKE_CASE` (例: `MAX_USERS`, `API_KEY`)
- ファイル名: `camelCase.js` または `PascalCase.js` (コンポーネントの場合は `PascalCase` が多い)。TypeScript の場合は `.ts` / `.tsx`。
- プライベートなメンバ (クラス内): `_camelCase` (慣習的なもので、強制力はない。TypeScript では `private` キーワードを使用)。

### コーディングスタイル (Coding Style)

- インデント: スペース 2 つまたは 4 つ (プロジェクトで一貫性を保つこと。一般的にはスペース 2 つが多い)。
- 1 行の最大文字数: 80〜100 文字程度を目安とする。
- セミコロン: 行末にはセミコロンを付けることを推奨 (ASI による意図しない挙動を避けるため)。
- 文字列リテラル: シングルクォート (`'`) またはダブルクォート (`"`) で一貫性を保つ (テンプレートリテラル `` ` `` は複数行や式埋め込みに活用)。
- コメント:
  - JSDoc (`/** ... */`) 形式を推奨 (特に関数やクラスのドキュメンテーション)。
  - 通常のコメントは `//` を使用する。
- `var` の代わりに `let` (再代入可能) と `const` (再代入不可) を使用する。

### JavaScript/TypeScript 特有の規約 (Specific Conventions)

- **厳格モード (Strict Mode)**:
  - `'use strict';` をスクリプトまたは関数の先頭に記述することを推奨 (ES Modules ではデフォルトで有効)。
- **型 (TypeScript)**:
  - 可能な限り具体的な型を指定する (`any` の使用は避ける)。
  - インターフェース (`interface`) や型エイリアス (`type`) を適切に使い分ける。
  - `null` と `undefined` の違いを理解し、適切に扱う。
- **非同期処理 (Asynchronous Operations)**:
  - `Promise` や `async/await` を積極的に使用する。
  - コールバック地獄を避ける。
- **エラーハンドリング (Error Handling)**:
  - `try...catch` ブロックでエラーを適切に処理する。
  - `Promise` の場合は `.catch()` や `async/await` での `try...catch` を使用する。
- **等価比較 (Equality)**:
  - `==` や `!=` の代わりに、厳密等価演算子 `===` や `!==` を使用する。
- **アロー関数 (Arrow Functions)**:
  - `function` キーワードの代わりにアロー関数を適切に使用する (特にコールバック関数や `this` の挙動を意識する場合)。
- **オブジェクトと配列 (Objects and Arrays)**:
  - スプレッド構文 (`...`) や分割代入を適切に活用する。
  - 配列の操作には `map`, `filter`, `reduce` などの高階関数を積極的に使用する。
- **DOM 操作 (DOM Manipulation)** (ブラウザ環境の場合):
  - Vanilla JS で行う場合は、効率的なセレクタやメソッドを使用する。
  - 可能であれば、React, Vue, Angular などのフレームワーク/ライブラリの抽象化レイヤーを利用する。
- **モジュール化 (Modularization)**:
  - 機能ごとにファイルを分割し、`import`/`export` で依存関係を明確にする。

### 非推奨事項 (Discouraged Practices)

- グローバル変数の多用。
- `eval()` の使用。
- `document.write()` の使用。
- 同期的な XHR の使用。
- `with` 文の使用。
- TypeScript での `@ts-ignore` の乱用 (本当に必要な場合のみ、理由をコメントで記述する)。
