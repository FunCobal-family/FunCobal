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

## 修飾子 - Modifier

## 識別子 - Identifier

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

### 特殊操作アノテーション - Special-operation Annotation

- @dare
- @sdata
