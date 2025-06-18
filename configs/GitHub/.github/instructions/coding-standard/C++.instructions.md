---
applyTo: "*.cpp,*.cxx,*.cc,*.hpp,*.hxx,*.hh"
---

## Description

このファイルは C++ に関する GitHub Copilot への指示と、一般的なコーディング規約をまとめたものです。
Copilot がより適切なサポートを提供し、開発者が一貫性のあるコードを記述するためのガイドラインとして機能します。

## Purpose

- Copilot に対し、C++ のプロジェクトにおけるコーディングスタイル、ベストプラクティス、注意点を指示する。
- 開発者が参照するための、C++ の基本的なコーディング規約を提供する。
- コードの可読性、保守性、一貫性を高める。

## Usage

- Copilot はこの指示を読み込み、C++ のコード生成や提案に活用する。
- 開発者は新しいコードを記述する際や、既存のコードをレビューする際にこの規約を参照する。

## Key Files and Folders

- `*.cpp`, `*.cxx`, `*.cc`: C++ のソースファイル。
- `*.hpp`, `*.hxx`, `*.hh`: C++ のヘッダーファイル。
- `CMakeLists.txt`, `Makefile`: ビルドシステムファイル。

## For GitHub Copilot

### 全体の方針 (General Policy)

- このリポジトリの `general.instructions.md` に記載された全体方針に従うこと。
- C++ Core Guidelines や Google C++ Style Guide などを参考に、モダン C++のベストプラクティスを推奨すること。
- 可読性と保守性を重視したコードを生成すること。
- オブジェクト指向設計の原則 (SOLID など) を意識すること。
- モジュール化を促進し、コンポーネント間の結合度を低く保つこと。

### 命名規則 (Naming Conventions)

- クラス名、構造体名、列挙型名: `PascalCase` (例: `MyClass`, `PlayerData`)
- 関数名、メソッド名: `camelCase` または `snake_case` (プロジェクトで一貫性を保つこと。ここでは `camelCase` を推奨: `calculateValue`, `getUserName`)
- 変数名 (ローカル、メンバ): `camelCase` (例: `itemCount`, `isEnabled`)
- 定数 (const, constexpr), enum メンバー: `kPascalCase` または `UPPER_SNAKE_CASE` (例: `kMaxUsers`, `MAX_BUFFER_SIZE`)
- マクロ名: `UPPER_SNAKE_CASE` (例: `ENABLE_FEATURE_X`)
- ファイル名: `snake_case.cpp` / `snake_case.hpp` または `PascalCase.cpp` / `PascalCase.hpp` (プロジェクトで一貫性を保つこと)

### コーディングスタイル (Coding Style)

- インデント: スペース 4 つ。
- 1 行の最大文字数: 80〜100 文字程度を目安とする。
- 中括弧 `{}`: K&R スタイルまたは Allman スタイル (プロジェクトで一貫性を保つこと)。
- コメント:
  - Doxygen 形式 (`/** ... */` や `///`) を用いたドキュメンテーションコメントを推奨。
  - 通常のコメントは `//` を使用する。
- `using namespace std;` はヘッダーファイルでは使用せず、ソースファイル内でもスコープを限定して使用する。

### C++ 特有の規約 (Specific Conventions for C++)

- **RAII (Resource Acquisition Is Initialization)**:
  - リソース管理には RAII を徹底し、スマートポインタ (`std::unique_ptr`, `std::shared_ptr`) を積極的に活用する。
  - 生ポインタの直接的な `new` / `delete` は極力避ける。
- **エラーハンドリング (Error Handling)**:
  - 例外を適切に使用する。エラーが発生しうる箇所では `try-catch` ブロックで処理する。
  - 関数の成功・失敗を示すためにエラーコードを返す場合は、その意味を明確にする。
- **const 正しさ (Const Correctness)**:
  - 変更しない変数やメンバ関数には `const` を付与する。
- **型推論 (Type Deduction)**:
  - `auto` キーワードは可読性を損なわない範囲で適切に使用する。
- **モダン C++機能の活用**:
  - C++11 以降の機能 (ラムダ式, ムーブセマンティクス, レンジベース for ループなど) を積極的に活用する。
  - 標準ライブラリ (STL) を最大限に活用する。
- **ヘッダーファイル**:
  - インクルードガード (`#pragma once` または `#ifndef MY_HEADER_HPP ... #endif`) を必ず使用する。
  - ヘッダーファイルには、そのヘッダーが単独でコンパイル可能になるように、必要なヘッダーをすべてインクルードする (Self-contained headers)。
  - 前方宣言を適切に使用してコンパイル時間を削減する。
- **オブジェクト指向**:
  - 継承よりもコンポジションを優先することを検討する。
  - 仮想関数は必要な場合にのみ使用し、`override` キーワードを明示する。
  - デストラクタは、基底クラスで仮想にするか、`protected` にしてポリモーフィックな削除を禁止する。

### 非推奨事項 (Discouraged Practices)

- C スタイルのキャスト (`(type)value`) の代わりに C++スタイルのキャスト (`static_cast`, `dynamic_cast`, `reinterpret_cast`, `const_cast`) を使用する。
- グローバル変数の多用。
- マクロによる複雑な制御フローの実現 (関数やテンプレートで代替できないか検討する)。
- 生の配列よりも `std::vector` や `std::array` を使用する。
