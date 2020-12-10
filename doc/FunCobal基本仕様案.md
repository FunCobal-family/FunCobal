# FunCobal 基本仕様原案

## 前文 - Preamble

## 概要- Abstract

この言語は、Julia 言語、Dart 言語、Ruby 言語、及び Ada 言語に触発されて製作されたものであり、これらの言語及びその他の数多の諸言語を参考にしている。

## 名称 - Name

「FunCobal」という名前はすわわ氏により命名された。氏によると、「Fun」は「関数型的なスタイルによる言語」に由来し、またこの言語が楽しい言語になるようにとの希望も含まれている。「Cobal」は、筆頭製作者である Haruka Sato(Takuya Matsunaga)のニックネームに由来する。

The name "FunCobal" is named by Mr. Suwawa. According to his saying, the origin is "Fun" from "with Some Functional Style" and hope that the language will be fantastic, and "Cobal" from "Cobaltia" , the alias name of Haruka Sato(Takuya Matsunaga), chif developer of the language.

## 主要方針 - Main

- 小規模開発から大規模開発まで
- フロントエンドからバックエンドまで
- 汎用から科学技術計算,計算科学,数値解析まで

## 主要要件 - Main

- リスク耐性

## マルチパラダイム言語 - Multi-Paradigm Language

オブジェクト指向プログラミング  
object-oriented programming  
└ 　プロトタイプベースプログラミング

## オブジェクト - The Object

総てのリテラルはオブジェクトである。

- 構造体：フィールドのみでメソッドのないオブジェクト。エイリアスとして Struct をもつ。コンストラクタは任意である。コンストラクタのない場合は、フィールド宣言時のデータがインスタンス作成時にインスタンスにコピーされる。
- クラス：フィールド・コンストラクタの他にメソッドをもつオブジェクト。エイリアスとして Class をもつ。コンストラクタ必須である。
- 連続体：
- 多様体:少なくとも局所的には座標系が定義できるオブジェクト。エイリアスとして Fold をもつ。シェイプやコンポーネント、CG モデルや地理空間データなどがある。

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

## 関数群

### ルーチン

ひとまとまりの手続き。手続き型・オブジェクト指向・アスペクト指向等の部分で関数という場合はこちらを指す。インターフェースとプロシージャに分けられ、前者は返り値をもち、後者はもたない。クラス等に所属するルーチンをメソッドという。この場合のインターフェースは Java 言語などのインターフェースとは異なるので注意のこと。

#### ミクスイン

- プロトタイプ: 　抽象メソッド宣言であり、実装をもたない。Java 言語などのインターフェースに相当する。
- トレイト: 　拡張メソッド基盤であり、実装をもつ。識別子が衝突する場合、ミクスイン先におけるエイリアス定義によって解決されるが、欠缺のある場合は、トレイト側の衝突するメソッドが無視される。

### 純関数

参照透過性をもち、副作用をもたない、計算や処理の定義。関数型の部分で関数という場合はこちらを指す。

## 識別子 - Identifier

ソースコードは総て Unicode で記述され処理される。 変数群や関数群などの総ての識別子は Unicode で記述し、UTF-8 で保存

## 指定子

指定子は対象リテラルの直前にドット`.`で結合する。例えば、`public.Class sample{}`のようにである。

### アクセス権指定子

リテラルへのアクセス権をコントローリする。

- public 　すべての場所からアクセス可能
- default 　ファイル内からのみアクセス可能(デフォルト、省略可能)
- protected 　ブロック内、同一オブジェクト内及び子孫オブジェクトからのみアクセス可能
- private 　ブロック内及び同一オブジェクト内からのみアクセス可能

### 静動指定子

静的性/動的性を指定する。省略可能なデフォルトはリテラルの種類によって異なる。

- dynamic 　動的性を与える
- static 　静的性を与える

### 型代入指定子

代入時に型体系における形式(精度など)をコントローリする。

- big 　最高精度多倍長型形式

### 特殊処理指定子

遅延評価や非同期処理を規定する。

- lazy 　遅延評価
- await 　非同期

対ブロック

- laziness 　遅延評価
- async 　非同期

### 指定子付き型のエイリアス

"dynamic." + "::Either" == "::Dynamic"

### 非同期処理・遅延評価の例示コード

```FunCobal
//非同期処理
async{
    await.doing();
}
```

```FunCobal
laziness{
    //遅延評価　この例の場合変数dが呼び出されるまで9+5はされない
    lazy.Let::Int d=9+5;
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

## 修飾子 - Modifier

## 注釈子 - Annotation

### ヘッダアノテーション - Header Annotation

@package, @env, @depend アノテーションは単独ファイルでコンパイル/実行する場合には必要。ライブラリパッケージを構成している場合は tsaaspec ファイルへの記述で十分。

- @package: 　その属するパッケージ名を指定する。
- @env: 　動作環境を指定する。
- @depend: 　依存パッケージを指定する。
- @import: 　パッケージ又はローカルのプログラムファイルをインポートする。
- #include: 　@depend アノテーションの追加項目を指定する。@depend アノテーションで指定した依存パッケージのうち特定のモジュールのみの依存の場合に、その情報を指定して追加モジュールを限定する。

### パラダイムアノテーション - Paradigm Annotation

- @function
- @component

### 言語間アノテーション - Inter-language Annotation

- @using

### 数理アノテーション - Mathematical-scientific Annotation

- @index:　リストのインデックスの開始値を示す。リストのインデックスの開始値はデフォルトではは 0 であるが、計算上の理由で変更したい場合は@index アノテーションを指定する。ブロックスコープ

### 特殊操作アノテーション - Special-operation Annotation

- @dare
- @sdata
- :net
- :implements
