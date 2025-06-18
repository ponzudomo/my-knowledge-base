---
applyTo: "**/*.cpp,**/*.cxx,**/*.cc,**/*.hpp,**/*.hxx,**/*.hh"
---

# テスト（Google Test）に関する instructions

## 基本方針

- テストは Google Test（gtest）を主に利用する。
- テストコードは本体コードと同じ命名規則・コーディング規約に従う。
- テストファイルは `*_test.cpp` 形式で命名し、テスト対象のファイル名に合わせる。
- テストケース名・テスト関数名は、テスト内容が分かるように具体的に記述する。
- テストは小さく独立させ、1 つのテストで複数の事象を検証しない。
- テストデータは必要に応じて fixture を活用し、重複を避ける。

## Google Test のベストプラクティス

- `TEST`/`TEST_F` マクロを使い、テストクラスや fixture を適切に設計する。
- 失敗時の出力が分かりやすいように assertion メッセージを工夫する。
- テストコードにもコメントを付け、何を検証しているか明記する。
- テストの可読性・保守性を重視し、冗長なテストは避ける。

## 参考

- [Google Test 公式ドキュメント](https://google.github.io/googletest/)
- [Google C++ Style Guide: Unit Tests](https://google.github.io/styleguide/cppguide.html#Unit_Tests)
