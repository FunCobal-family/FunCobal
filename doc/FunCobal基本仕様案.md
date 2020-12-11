# FunCobal 基本仕様原案

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [前文 - Preamble](#%E5%89%8D%E6%96%87---preamble)
- [概要- Abstract](#%E6%A6%82%E8%A6%81--abstract)
- [名称 - Name](#%E5%90%8D%E7%A7%B0---name)
- [主要方針 - Main Policy](#%E4%B8%BB%E8%A6%81%E6%96%B9%E9%87%9D---main-policy)
- [主要要件 - Main Requirement](#%E4%B8%BB%E8%A6%81%E8%A6%81%E4%BB%B6---main-requirement)
- [マルチパラダイム言語 - Multi-Paradigm Language](#%E3%83%9E%E3%83%AB%E3%83%81%E3%83%91%E3%83%A9%E3%83%80%E3%82%A4%E3%83%A0%E8%A8%80%E8%AA%9E---multi-paradigm-language)
- [オブジェクト - The Object](#%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88---the-object)
- [識別名 - Modified Name](#%E8%AD%98%E5%88%A5%E5%90%8D---modified-name)
- [系列言語形式名前空間](#%E7%B3%BB%E5%88%97%E8%A8%80%E8%AA%9E%E5%BD%A2%E5%BC%8F%E5%90%8D%E5%89%8D%E7%A9%BA%E9%96%93)
- [変数群 - Variable Models](#%E5%A4%89%E6%95%B0%E7%BE%A4---variable-models)
  - [型体系 - The Type System](#%E5%9E%8B%E4%BD%93%E7%B3%BB---the-type-system)
  - [変数種名 - Kind of Variable Models](#%E5%A4%89%E6%95%B0%E7%A8%AE%E5%90%8D---kind-of-variable-models)
  - [変数群宣言](#%E5%A4%89%E6%95%B0%E7%BE%A4%E5%AE%A3%E8%A8%80)
- [関数群](#%E9%96%A2%E6%95%B0%E7%BE%A4)
  - [ルーチン](#%E3%83%AB%E3%83%BC%E3%83%81%E3%83%B3)
    - [ミクスイン](#%E3%83%9F%E3%82%AF%E3%82%B9%E3%82%A4%E3%83%B3)
  - [純関数](#%E7%B4%94%E9%96%A2%E6%95%B0)
- [リテラル表現](#%E3%83%AA%E3%83%86%E3%83%A9%E3%83%AB%E8%A1%A8%E7%8F%BE)
- [基本構文](#%E5%9F%BA%E6%9C%AC%E6%A7%8B%E6%96%87)
- [附属子類](#%E9%99%84%E5%B1%9E%E5%AD%90%E9%A1%9E)
  - [識別子 - Identifier](#%E8%AD%98%E5%88%A5%E5%AD%90---identifier)
  - [指定子](#%E6%8C%87%E5%AE%9A%E5%AD%90)
    - [アクセス権指定子](#%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B9%E6%A8%A9%E6%8C%87%E5%AE%9A%E5%AD%90)
    - [静動指定子](#%E9%9D%99%E5%8B%95%E6%8C%87%E5%AE%9A%E5%AD%90)
    - [型代入指定子](#%E5%9E%8B%E4%BB%A3%E5%85%A5%E6%8C%87%E5%AE%9A%E5%AD%90)
    - [特殊処理指定子](#%E7%89%B9%E6%AE%8A%E5%87%A6%E7%90%86%E6%8C%87%E5%AE%9A%E5%AD%90)
    - [指定子付き型のエイリアス](#%E6%8C%87%E5%AE%9A%E5%AD%90%E4%BB%98%E3%81%8D%E5%9E%8B%E3%81%AE%E3%82%A8%E3%82%A4%E3%83%AA%E3%82%A2%E3%82%B9)
  - [修飾子 - Modifier](#%E4%BF%AE%E9%A3%BE%E5%AD%90---modifier)
  - [注釈子 - Annotation](#%E6%B3%A8%E9%87%88%E5%AD%90---annotation)
    - [ヘッダアノテーション - Header Annotation](#%E3%83%98%E3%83%83%E3%83%80%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3---header-annotation)
    - [パラダイムアノテーション - Paradigm Annotation](#%E3%83%91%E3%83%A9%E3%83%80%E3%82%A4%E3%83%A0%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3---paradigm-annotation)
    - [言語間アノテーション - Inter-language Annotation](#%E8%A8%80%E8%AA%9E%E9%96%93%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3---inter-language-annotation)
    - [数理アノテーション - Mathematical-scientific Annotation](#%E6%95%B0%E7%90%86%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3---mathematical-scientific-annotation)
    - [特殊操作アノテーション - Special-operation Annotation](#%E7%89%B9%E6%AE%8A%E6%93%8D%E4%BD%9C%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3---special-operation-annotation)
- [関数型](#%E9%96%A2%E6%95%B0%E5%9E%8B)
  - [純関数の性質](#%E7%B4%94%E9%96%A2%E6%95%B0%E3%81%AE%E6%80%A7%E8%B3%AA)
  - [遅延評価](#%E9%81%85%E5%BB%B6%E8%A9%95%E4%BE%A1)
- [文字列処理](#%E6%96%87%E5%AD%97%E5%88%97%E5%87%A6%E7%90%86)
  - [正規表現](#%E6%AD%A3%E8%A6%8F%E8%A1%A8%E7%8F%BE)
- [並行処理・並列処理・分散処理](#%E4%B8%A6%E8%A1%8C%E5%87%A6%E7%90%86%E3%83%BB%E4%B8%A6%E5%88%97%E5%87%A6%E7%90%86%E3%83%BB%E5%88%86%E6%95%A3%E5%87%A6%E7%90%86)
  - [非同期処理](#%E9%9D%9E%E5%90%8C%E6%9C%9F%E5%87%A6%E7%90%86)
  - [高階関数](#%E9%AB%98%E9%9A%8E%E9%96%A2%E6%95%B0)
  - [並行処理](#%E4%B8%A6%E8%A1%8C%E5%87%A6%E7%90%86)
  - [並列処理](#%E4%B8%A6%E5%88%97%E5%87%A6%E7%90%86)
  - [分散処理](#%E5%88%86%E6%95%A3%E5%87%A6%E7%90%86)
- [例外処理](#%E4%BE%8B%E5%A4%96%E5%87%A6%E7%90%86)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

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
