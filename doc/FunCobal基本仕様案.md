# FunCobal 基本仕様原案

## 前文 - Preamble

## 概要- Abstract

この言語は、Julia言語、Dart言語、Ruby言語、及びAda言語に触発されて製作されたものであり、これらの言語及びその他の数多の諸言語を参考にしている。

## 名称 - Name

「FunCobal」という名前はすわわ氏により命名された。氏によると、「Fun」は「関数型的なスタイルによる言語」に由来し、またこの言語が楽しい言語になるようにとの希望も含まれている。「Cobal」は、筆頭製作者であるHaruka Sato(Takuya Matsunaga)のニックネームに由来する。

The name "FunCobal" is named by Mr. Suwawa. According to his saying, the origin is "Fun" from "with Some Functional Style" and hope that the language will be fantastic, and "Cobal" from "Cobaltia" , the alias name of Haruka Sato(Takuya Matsunaga), chif developer of the language.

## 主要方針

- 小規模開発から大規模開発まで
- フロントエンドからバックエンドまで
- 汎用から科学技術計算,計算科学,数値解析まで

## 主要要件

- リスク耐性

## マルチパラダイム言語

## Multi-Paradigm Language

オブジェクト指向プログラミング  
object-oriented programming  
└ 　プロトタイプベースプログラミング

## 型体系

型(データ型)はオブジェクトであり、包含的派生型による型ツリーを構築する。

## オブジェクト

クラスはオブジェクトの一種であり、

- 構造体：変数・定数のみでメソッドのないオブジェクト。エイリアスとしてstructをもつ。
- 連続体：
