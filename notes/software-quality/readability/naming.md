（Qiitaに載せる用の文章になっています）
（Qiitaに載せ終わったらもっとコンパクトにまとめます）

## 目次

スマホ版だと目次が表示されないようなので、置いておきますね

>
>

<br>

---

# 足りないセンスは知識で補おう

私がコーディングでもっとも嫌いな作業、それは **命名** です。

### 宣言でもたつくのをやめたい

コーディングとは、いわば創作活動です。
美しいコードへのこだわりが捨てきれない私は、いつも名前決めに無駄な時間をかけてしまいます。歯がゆいー

### よくわからない名前をやめたい

- ローマ字表記も英単語の誤用もプライドが許さない
- でも正しい英語表記は分からない
- ダサさを恐れて `tmp` や `ret` ばかり使っていては、何を書いているのか分からなくなるらしい

どうにかしてください。

## これってマニュアル化しておけば楽な気がする！

なぜこんなに命名に手間取っているのか？
それは**自由だから**です。正解がないから迷う余地が生まれるのです。

じゃあ、手順書を作って**流れ作業にしてしまえば楽になる**のでは？

<br>

---

# 可読性を上げるための命名規則

ということで、変数や関数を宣言するときのルールを細かく定めていきます。

> 1. [基本方針](1-基本方針)
> 1. [変数](2-変数)
> 1. [関数](3-関数)
> 1. [構造体](4-構造体)
> 1. [定数](5-定数)


## 1. 基本方針

:::note
**目的はあくまでも保守性・拡張性の向上**
- まずは規約に従う
- 情報(5W1H)が伝わる名前にする
- 長すぎず短すぎない
- 一貫性を保つ
:::

### 前提: まずはコーディング規約に従おう

変数や関数の名前には、大きく分けて以下の5つのフォーマットがあります。

|      命名規則      |      例      |                   由来                   |
| :----------------: | :----------: | :--------------------------------------: |
| **キャメルケース** | `camelCase`  |               ラクダのコブ               |
| **パスカルケース** | `PascalCase` |       Pascal (プログラミング言語)        |
| **スネークケース** | `snake_case` |             蛇が這っている姿             |
|  **ケバブケース**  | `kebab-case` |              串刺しのケバブ              |
|    ドットケース    |  `dot.case`  | 普通にドット (JSONとかXMLとかで使われる) |

お仕事でコーディングをする場合、コーディング規約としてあらかじめ指定してあることが多いです。規約に従いましょう。

なかった場合は、自分で規約を設けてしまうと後々楽だと思います。（詳しくは後述します）
各言語の公式ドキュメントに最低限のおすすめ命名規則は書いてあるので、基本的なところは参考にするのが安心です。

( [言語ごとに命名規則をまとめて下さった神記事](https://qiita.com/sakaki_developer/items/349fa8a41239ca361386) もあります！）


### 良い名前とは

> - いつ使えばいいのかが分かる (適用箇所)
> - 何に使うのかが分かる (適用先)
> - どうやって使うのかが分かる (適用方法)

名前からコンテキストが分かれば、コードの読解がしやすくなるでしょう。
名前から使い方が推測できれば、今後そのコードを扱いやすくなるでしょう。

名前は、簡易的なコメントとしての役割を持つのが望ましいです。

### 悪い名前とは

> - 短すぎる
> - 長すぎる

丁寧な命名は可読性を上げるというお話をしました。
しかし **丁寧さは冗長さと紙一重** であることに注意が必要です。

読解コストの節約量を記述コストが上回っていては本末転倒ですから、バランスを意識して命名するのが好ましいです。

### 使えるテクニック集

**否定形にしない**
- 問題文に ｢~でないものを選びなさい｣ って書いてあるとイラつく理論
- isNotEnabled より isDisabled

**スコープに応じた粒度**
- 一瞬しか使わない変数なら極論 tmp でもいい (どこでどう使われているのか視界に入るため)
- プログラムの軸となる関数やクラスはしっかり命名

**統一感を保つ**
- 表記揺れを防ぐ ( msg / message や cfg / config を混在させない )
- 語順を意識 ( userGet ではなく getUser にする )
- 対義語を揃える ( open ↔ close、enable ↔ disable )
- 頻出語を辞書登録しておく
- Notionなどで頻出英単語帳を作っておく

<br>

## 2. 変数

:::note
基本構造 : **`属性 - 内容`**
ポイント : **データ型, 単位, 時制**
:::

### 基本構造

**変数は、中身・数・状態を明示します。**

土台として ｢何にまつわる変数なのか｣ ｢具体的に何に使う変数なのか｣ の二つが入っていると嬉しいです。
これをベースとして、適宜接頭辞や接尾辞で味付けしていくとよいでしょう。

### 使えるテクニック集

**データ型を匂わせ**
- 真偽値(bool)なら `is_` や `has_` をつける
- 配列なら複数形にする

**単位を明記**
- 単位がある場合は、`pixels` や `seconds` といったように明記し誤用を防ぐ

**時制の区別をしっかり**
- これまでに行った内容なのか、これから行うべき内容なのかを区別
<br>

## 3. 関数

:::note
基本構造 : **`動詞 - 目的語`**
ポイント : **引数, 返り値, 動作の内容(副作用)**
:::

### 基本構造

何に対して何を行うものなのか、**`動詞 - 目的語`** で**動作を明確に**します。

### 使えるテクニック集

**引数と返り値を匂わせ**

- 関数は `a = calculate(b, c);` といったようにしれっと文中に登場してくるので、**特に返り値**は分かりやすくしておく必要がある
- たとえば read_input() よりも read_grid() の方が好き

**動作の内容(副作用)を明確に**

- `get` と `fetch` の使い分け然り、副作用の有無が読み取りやすいと嬉しい
<br>

## 4. 構造体/クラス

:::note
基本構造 : **`属性名`**
ポイント : **メンバ**
:::

### 基本構造

**ドメイン名詞で実態を表します。**

構造体は、基本的には単数系であるのが望ましいと聞きました。自分もそう思います。
｢よく使う属性について情報をまとめておく｣ みたいな認識です。

なので中に何を入れたのか、何がまとめられているのか思い出しやすい名前だと嬉しいです。
<br>

## 5. 定数

:::note
基本構造 : **`大分類 - 小分類`** or **`目的語のみ`**
ポイント : **`UPPER_CASE`**
:::

### 基本構造

定数を用いるメリットは、主にコードの安全性の向上やマジックナンバーへの別名付与かと思います。
定数は定数であることに意味があるので、大文字で記述するなどして **｢定数であること｣** をアピールするのが最優先です。

加えて、ピンポイントな使用用途のものは `大分類 - 小分類` といった構造で説明を加えてあげると親切かなと思います。
<br>

---

# よく使うワードリスト

## 名詞（オブジェクト・データ・役割）

| 日本語             | 英単語候補                                                  |
| ------------------ | ----------------------------------------------------------- |
| ユーザー           | `user`, `account`, `member`, `profile`                      |
| 商品・製品         | `item`, `product`, `goods`, `article`                       |
| 注文               | `order`, `purchase`, `transaction`                          |
| 住所               | `address`, `location`, `place`                              |
| メッセージ         | `message`, `note`, `comment`, `reply`                       |
| ファイル           | `file`, `document`, `record`, `attachment`                  |
| 画像               | `image`, `picture`, `photo`, `thumbnail`                    |
| 日時               | `date`, `time`, `timestamp`, `datetime`, `schedule`         |
| 認証               | `auth`, `credential`, `token`, `session`, `login`           |
| 設定               | `config`, `setting`, `option`, `preference`, `parameter`    |
| エラー             | `error`, `fail`, `exception`, `issue`, `bug`, `problem`     |
| ログ               | `log`, `history`, `trace`, `record`                         |
| 結果               | `result`, `response`, `output`, `data`, `payload`, `return` |
| ステータス         | `status`, `state`, `flag`, `condition`                      |
| カウント           | `count`, `total`, `amount`, `sum`, `number`, `quantity`     |
| ID関連             | `id`, `uuid`, `key`, `code`, `hash`                         |
| グループ・カテゴリ | `group`, `category`, `tag`, `label`, `type`, `class`        |
| ページ関連         | `page`, `view`, `screen`, `panel`, `window`                 |
| 通知               | `notification`, `alert`, `warning`, `reminder`              |

---

## 動詞（関数・メソッドによく使う）

| 日本語     | 英単語候補                                                                            |
| ---------- | ------------------------------------------------------------------------------------- |
| 取得       | `get`, `fetch`, `retrieve`, `load`, `read`, `collect`, `query`                        |
| 設定・変更 | `set`, `update`, `change`, `assign`, `modify`, `edit`, `adjust`                       |
| 作成       | `create`, `generate`, `build`, `make`, `construct`, `init`                            |
| 削除       | `delete`, `remove`, `clear`, `destroy`, `drop`, `unset`                               |
| 検証       | `validate`, `check`, `verify`, `ensure`, `confirm`, `assert`                          |
| 変換       | `convert`, `translate`, `format`, `parse`, `cast`, `map`, `serialize`                 |
| 実行       | `run`, `execute`, `perform`, `call`, `process`, `apply`, `trigger`, `start`, `launch` |
| 停止       | `stop`, `abort`, `cancel`, `end`, `terminate`, `pause`                                |
| 検索       | `find`, `search`, `lookup`, `scan`, `filter`, `match`                                 |
| 並べ替え   | `sort`, `arrange`, `order`, `shuffle`, `reorder`                                      |
| 保存       | `save`, `store`, `persist`, `cache`, `record`, `backup`                               |
| 読み込み   | `load`, `import`, `read`, `open`                                                      |
| 書き込み   | `write`, `export`, `output`, `log`                                                    |
| 通信       | `send`, `post`, `request`, `submit`, `receive`, `upload`, `download`                  |
| 結合       | `join`, `merge`, `combine`, `append`, `concat`                                        |
| 分割       | `split`, `divide`, `separate`, `slice`, `extract`                                     |

---

## 形容詞・副詞（状態の説明、フラグ名など）

| 日本語     | 英単語候補                                                 |
| ---------- | ---------------------------------------------------------- |
| 有効な     | `active`, `enabled`, `valid`, `available`, `visible`       |
| 無効な     | `inactive`, `disabled`, `invalid`, `unavailable`, `hidden` |
| 完了済み   | `completed`, `done`, `finished`, `processed`               |
| 一時的     | `temporary`, `temp`, `transient`, `ephemeral`              |
| 空・未設定 | `empty`, `null`, `undefined`, `blank`, `none`              |
| 新しい     | `new`, `fresh`, `recent`, `latest`                         |
| 古い       | `old`, `previous`, `outdated`, `legacy`                    |
| 成功       | `success`, `passed`, `ok`                                  |
| 失敗       | `fail`, `error`, `fault`, `broken`                         |
| 最大・最小 | `max`, `min`, `highest`, `lowest`, `top`, `bottom`         |
| 必須       | `required`, `mandatory`, `needed`                          |
| 任意       | `optional`, `selectable`, `nullable`                       |

---

## 状態・フラグ名に使いやすいワード特集

| 日本語           | 英単語候補                               |
| ---------------- | ---------------------------------------- |
| アクティブか     | `isActive`, `isEnabled`, `hasStarted`    |
| 読み取り専用か   | `isReadOnly`, `isLocked`                 |
| 初回か           | `isFirst`, `isInitial`, `isNewUser`      |
| 認証済みか       | `isAuthenticated`, `hasLogin`            |
| データありか     | `hasData`, `isEmpty`, `hasResults`       |
| 操作できるか     | `canEdit`, `canDelete`, `isEditable`     |
| ログイン状態     | `isLoggedIn`, `isGuest`, `isAdmin`       |
| ローディング中か | `isLoading`, `isProcessing`, `isPending` |

---

## 参考: 状況別命名例

| 意図                   | 命名例                                                  |
| ---------------------- | ------------------------------------------------------- |
| APIレスポンス格納用    | `response`, `res`, `apiResult`, `data`                  |
| ユーザー入力の一時保持 | `formData`, `inputValues`, `userInput`                  |
| ボタンのクリック処理   | `handleClick`, `onClick`, `submitForm`, `triggerAction` |
| フィルター条件         | `filter`, `criteria`, `query`, `searchParams`           |
| エラー処理             | `handleError`, `errorMsg`, `isFailed`, `hasError`       |
| ページ表示の状態       | `currentPage`, `activeTab`, `selectedIndex`             |

---

# ネーミングセンスを磨くには

命名で

## 良さげなコードから学ぼう

## モヤっとしたら辞書を引く

## AIに意見を聞いてもいい



# 参考文献
