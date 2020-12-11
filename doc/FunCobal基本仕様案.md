# FunCobal 基本仕様原案

## 前文 - Preamble

この言語は、外観はシンプルであり、かつそれでいて内側は複雑である。

Ruby を超える楽しさ、C 言語の速度、MATRAB や Mathematica のような数式になじんだ記述、Julia や Haskell、Octave のような強力な数式処理、Ruby のような関数型プログラミングと命令型プログラミングが絶妙に調和されたデザイン、Dart のようなクロスプラットフォーム、Ruby や Dart のような実用性、Ruby のような強力な正規表現とそれに裏付けられた文字列処理、Ruby や Lua のようなグルー性、Dart のようなクラウドコンピューティング、Dart のような簡潔な UI 記述を併せ持つ言語を求めてこの言語を設計した。

我々は美的であり、貪欲である。果てしない可能性を追い求めて。

## 概要- Abstract

この言語は、Julia ,Dart ,及び Ruby に触発されて製作されたものであり、Julia, Dart, Ruby, Ada, Haskell, 及び OCaml の影響を強く受けている。また、これらの言語及びその他の数多の諸言語を参考にしている。

汎用機能と特化型機能を兼ね備えている超高級言語である。分散処理・並列処理や数理数式処理・科学技術計算・統計解析に特化しているほか、グラフィック・空間モデル処理、ハードウェア(インターフェース等)制御、組込システム(センサ/アクチュエータ)制御、文字列処理、データ(構造データ/データベース)処理、サーバ処理等にも幅広くフォーカスされている。手続き型と関数型の性質を兼ね合わせた真のクロスプラットフォーム言語である。

簡潔かつ分かりやすい記法で扱いやすく、また数式処理等はそれぞれになじんだ記法が採用されており、複雑な数式やアルゴリズムをストレスなく自然、シンプルかつリーダブルに記述できる。加えて-O3/-O4 C lang に匹敵する高速性(処理系への最上級要求事項)がある。

本文書ではこの言語の全てを体系的に説明する。

## 名称 - Name

「FunCobal」という名前はすわわ氏により命名された。氏によると、「Fun」は「関数型的なスタイルによる言語」に由来し、またこの言語が楽しい言語になるようにとの希望も含まれている。「Cobal」は、筆頭製作者である Haruka Sato(Takuya Matsunaga)のニックネームの一つである「Cobaltia」に由来する。

「Functional UNiversal Common Object-Based Algorithmic Language」の頭字でもある。

The name "FunCobal" is named by Mr. Suwawa. According to his saying, the origin is "Fun" from "with Some Functional Style" and hope that the language will be fantastic, and "Cobal" from "Cobaltia" , the alias name of Haruka Sato(Takuya Matsunaga), chief developer of the language.

## 主要方針 - Main Policy

- 小規模開発から大規模開発まで
- フロントエンドからバックエンドまで
- 汎用から科学技術計算,計算科学,数値解析まで

## 主要要件 - Main Requirement

- リスク耐性

## マルチパラダイム言語 - Multi-Paradigm Language

命令型プログラミング  
Imperative Programming  
├ オブジェクト指向プログラミング  
│Object-Oriented Programming  
│ ├ アスペクト指向プログラミング  
│ │ Aspect Oriented Programming  
│ ├ アクターモデル  
│ │ Actor Model  
│ └ プロトタイプベース  
│ 　　 Prototype-Based  
└ 手続き型プログラミング  
　 Procedural Programming  
　 └ モジュラープログラミング  
　　 Modular Programming  
宣言型プログラミング  
Declarative Programming  
└ 関数型プログラミング  
　 Functional Programming  
文芸的プログラミング  
Literate Programming  
インテンショナルプログラミング  
Intentional Programming

## オブジェクト - The Object

総てのリテラルはオブジェクトである。

- 構造体：フィールドのみでメソッドのないオブジェクト。エイリアスとして Struct をもつ。コンストラクタは任意である。コンストラクタのない場合は、フィールド宣言時のデータがインスタンス作成時にインスタンスにコピーされる。
- クラス：フィールド・コンストラクタの他にメソッドをもつオブジェクト。エイリアスとして Class をもつ。コンストラクタ必須である。
- 連続体：
- 多様体:少なくとも局所的には座標系が定義できるオブジェクト。エイリアスとして Fold をもつ。シェイプやコンポーネント、CG モデルや地理空間データなどがある。

## 識別名 - Modified Name

ソースコードは総て Unicode で記述され処理される。 変数群や関数群などの総ての識別子は Unicode で記述し、UTF-8 で保存する。対して ASCII や ANSI、S-JIS はゴミであり、使用できず、また使用してはならない。

同一オブジェクト種別間のみならず、異なるオブジェクト種別の間でも識別名の衝突は許さない。但し、関数群について、異なる引数構成について異なる振舞いをさせる場合に関しては、識別名を共通させるものとして。

## 系列言語形式名前空間

本言語はグルー性をもっており、(後述する)`@using`アノテーションで他の言語を組み込むことができる。FunCobal のコンパイラ・インタプリタ・REPL はこのアノテーションに当たったらその配下のコードをそれぞれの言語処理系の API に投げ、意味論解読した構文木をうけとる。

主な系列言語形式名前空間は次の通りである。

- Bantra : FC/Ches LL Langs : ex. Yezi-diki, Chestnut Bytecode
- Hardin: FC HL Langs : ex. FunCobal, Hjerbata, FC-Shell
- Tolte : Ches HL Langs : ex. Chestnut
- Google: Google Langs : ex Dart, Go lang

また、記述されているファイルの主たる言語との関係性により、以下の特別指定句にて名前空間を指定することができる。

- This : 自らの属する名前空間を示す
- Sub : 配下の名前空間(DSL など)を示す
- Super : Sub の逆を示す

## 変数群 - Variable Models

### 型体系 - The Type System

型(データ型)はオブジェクトであり、包含的派生型による型ツリーを構築する。

詳細は[FunCobal 型システム.md](./FunCobal型システム.md)(あるいは[FunCobal 型システム.pptx](./FunCobal型システム.pptx))を参照のこと。型システム .md の方が最新である。

### 変数種名 - Kind of Variable Models

|           スコープ |    常数    |       定数       |   変数   |
| -----------------: | :--------: | :--------------: | :------: |
|   ブロックスコープ |  Readonly  |      Final       |   Let    |
|   ファイルスコープ | ConstExpr  |    FixedExpr     |   Auto   |
| グローバルスコープ |   Const    |      Fixed       |   Var    |
|                    |  常に等値  |    再代入不可    | 制約なし |
|                    | 実行時定数 | コンパイル時定数 | 通常変数 |

### 変数群宣言

変数群は、変数種名と型名を`::`で結合し、宣言するべき変数群の識別名と半角空白を開けて前置する。識別名(同時に初期化たる代入を行う場合にはその終端)の後には同じく半角空白を開けて`\def`を記述することが望ましい。

```FunCobal
Let::Int a \def;
FixedExpr::Int b=30 \def;
```

## 関数群

### ルーチン

ひとまとまりの手続き。手続き型・オブジェクト指向・アスペクト指向等の部分で関数という場合はこちらを指す。インターフェースとプロシージャに分けられ、前者は返り値をもち、後者はもたない。クラス等に所属するルーチンをメソッドという。この場合のインターフェースは Java 言語などのインターフェースとは異なるので注意のこと。

#### ミクスイン

- プロトタイプ: 　抽象メソッド宣言であり、実装をもたない。Java 言語などのインターフェースに相当する。
- トレイト: 　拡張メソッド基盤であり、実装をもつ。識別子が衝突する場合、ミクスイン先におけるエイリアス定義によって解決されるが、欠缺のある場合は、トレイト側の衝突するメソッドが無視される。

### 純関数

参照透過性をもち、副作用をもたない、計算や処理の定義。関数型の部分で関数という場合はこちらを指す。

## リテラル表現

## 基本構文

## 附属子類

### 識別子 - Identifier

### 指定子

指定子は対象リテラルの直前にドット`.`で結合する。例えば、`public.Class sample{}`のようにである。

#### アクセス権指定子

リテラルへのアクセス権をコントローリする。

- public 　すべての場所からアクセス可能
- default 　ファイル内からのみアクセス可能(デフォルト、省略可能)
- protected 　ブロック内、同一オブジェクト内及び子孫オブジェクトからのみアクセス可能
- private 　ブロック内及び同一オブジェクト内からのみアクセス可能

#### 静動指定子

静的性/動的性を指定する。省略可能なデフォルトはリテラルの種類によって異なる。

- dynamic 　動的性を与える
- static 　静的性を与える

#### 型代入指定子

代入時に型体系における形式(精度など)をコントローリする。

- big 　最高精度多倍長型形式

#### 特殊処理指定子

遅延評価や非同期処理を規定する。

- lazy 　遅延評価
- await 　非同期

対ブロック

- laziness 　遅延評価
- async 　非同期
- para 並列処理指定

#### 指定子付き型のエイリアス

型に対する指定子のうち一部は、エイリアスたる型が定義されている。例えば、動的性を与える静動指定子`dynamic`は`Either`型と結合し`Dynamic`型を形成する。

### 修飾子 - Modifier

### 注釈子 - Annotation

#### ヘッダアノテーション - Header Annotation

`@package`, `@env`, `@depend` アノテーションは単独ファイルでコンパイル/実行する場合には必要。ライブラリパッケージを構成している場合は tsaaspec ファイルへの記述で十分。

- `@package`: 　その属するパッケージ名を指定する。
- `@env`: 　動作環境を指定する。
- `@depend`: 　依存パッケージを指定する。
- `@import`: 　パッケージ又はローカルのプログラムファイルをインポートする。
- `#include`: 　`@depend` アノテーションの追加項目を指定する。`@depend` アノテーションで指定した依存パッケージのうち特定のモジュールのみの依存の場合に、その情報を指定して追加モジュールを限定する。

#### パラダイムアノテーション - Paradigm Annotation

- `@function`
- `@component`

#### 言語間アノテーション - Inter-language Annotation

- `@using`: 　プログラム中に他の言語を組み込む。系列言語形式名前空間で修飾された言語名に続けて小括弧に囲んだ組込みプログラムを記述する。

```FunCobal
@using Sub:tex (
    //code written in Texicon(DSL of FunCobal,lang bind of Hardin Namespace)

)


@using This:hjr(
    //code written in Hjerbata(lang bind of Hardin Namespace)

)


@using Tolte:Chestnut(
    //code written in Chestnut(lang bind of Tolte Namespace)

)

@using Google:Dart(
    //code written in Dart(lang bind of Google Namespace)

)

@using Google:Go(
    //code written in Go lang(lang bind of Google Namespace)

)
```

#### 数理アノテーション - Mathematical-scientific Annotation

- `@index`:　リストのインデックスの開始値を示す。リストのインデックスの開始値はデフォルトではは 0 であるが、計算上の理由で変更したい場合は`@index` アノテーションを指定する。ブロックスコープである。

ex:

```FunCobal
{
    @index 1;
    //リストのインデックスの開始値を1と指定。このブロック内で有効。
}
```

#### 特殊操作アノテーション - Special-operation Annotation

- `@dare`: 　外部デバイス(標準入出力除く)(IC カード読み取り/書き込み器など)の操作を行う。
- `@sdata`: 　構造データを構築する。
- `:net`: 　外部デバイス(標準入出力除く)(IC カード読み取り/書き込み器など)の(プログラムファイルへの)設定(明示/宣言)を行う。
- `:implements`: 　`:net` アノテーションによる設定にたいしライブラリ。・パッケージを関連づける。

## 関数型

### 純関数の性質

### 遅延評価

```FunCobal
laziness{
    //遅延評価　この例の場合変数dが呼び出されるまで9+5はされない
    lazy.Let::Int d=9+5;
}
```

## 文字列処理

### 正規表現

本言語、もとい FunCobal family プロジェクトは専用の正規表現ライブラリ(とはいえ当然他の言語にも導入可能だが。)である「[鬼瀬](https://github.com/FunCobal-family/Onigase)」を擁しており、研究開発が進行している。

## 並行処理・並列処理・分散処理

### 非同期処理

```FunCobal
//非同期処理
async{
    await.doing();
}
```

```FunCobal
//(非同期処理の一種)
promise{
    //時間がかかる処理
}resolve{
    //処理成功時に流すメッセージデータの生成処理
}reject{
    //処理失敗時に流すメッセージデータの生成処理
}
```

### 高階関数

### 並行処理

### 並列処理

### 分散処理

## 例外処理

```FunCobal
//The Exceptions.
do{
    /* Something code that may occur exceptions */
    throw Exception;//throw Exception
    raise Exception;//or for this what alias of it
    throw SomeException;//throw Exception in type "SomeException"
}
catch{
    /* Something code to do when occurred some exceptions */
}
catch(SomeException e){
    /* Something code to do when occurred exceptions in type "SomeException" */
}
ensure{
    /* Something code to do in regardless of raise exceptions */
}
else{
    /* Something code to do when not occurred any exceptions what written rescue code */
}
```
