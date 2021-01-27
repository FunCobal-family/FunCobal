# FunCobal 基本仕様原案

<!--
<style>
body {
    counter-reset: h2;
}
h2 {
    counter-reset: h3;
}
h3 {
    counter-reset: h4;
}
h4 {
    counter-reset: h5;
}
h5 {
    counter-reset: h6;
}
h2:before {
    counter-increment: h2;
    content: "第" counter(h2) "章 ";
}
h3:before {
    counter-increment: h3;
    content: "第" counter(h3) "部 ";
}
h4:before {
    counter-increment: h4;
    content: "第" counter(h4) "節 ";
}
h5:before {
    counter-increment: h5;
    content: counter(h5) ". ";
}
h6:before {
    counter-increment: h6;
    content: counter(h5) ". " counter(h6) ". ";
}
</style> -->
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
- [代数 - Algebraic Models](#%E4%BB%A3%E6%95%B0---algebraic-models)
  - [型体系 - The Type System](#%E5%9E%8B%E4%BD%93%E7%B3%BB---the-type-system)
  - [変数種名 - Kind of Variable Models](#%E5%A4%89%E6%95%B0%E7%A8%AE%E5%90%8D---kind-of-variable-models)
  - [代数宣言](#%E4%BB%A3%E6%95%B0%E5%AE%A3%E8%A8%80)
- [関数](#%E9%96%A2%E6%95%B0)
  - [関数合成](#%E9%96%A2%E6%95%B0%E5%90%88%E6%88%90)
- [代数的データ構造](#%E4%BB%A3%E6%95%B0%E7%9A%84%E3%83%87%E3%83%BC%E3%82%BF%E6%A7%8B%E9%80%A0)
  - [ミクスイン](#%E3%83%9F%E3%82%AF%E3%82%B9%E3%82%A4%E3%83%B3)
  - [連続体](#%E9%80%A3%E7%B6%9A%E4%BD%93)
  - [構造体と共用体](#%E6%A7%8B%E9%80%A0%E4%BD%93%E3%81%A8%E5%85%B1%E7%94%A8%E4%BD%93)
  - [クラスとプロトタイプ・トレイト](#%E3%82%AF%E3%83%A9%E3%82%B9%E3%81%A8%E3%83%97%E3%83%AD%E3%83%88%E3%82%BF%E3%82%A4%E3%83%97%E3%83%BB%E3%83%88%E3%83%AC%E3%82%A4%E3%83%88)
- [リテラル表現](#%E3%83%AA%E3%83%86%E3%83%A9%E3%83%AB%E8%A1%A8%E7%8F%BE)
- [基本構文](#%E5%9F%BA%E6%9C%AC%E6%A7%8B%E6%96%87)
  - [コーディングスタイル](#%E3%82%B3%E3%83%BC%E3%83%87%E3%82%A3%E3%83%B3%E3%82%B0%E3%82%B9%E3%82%BF%E3%82%A4%E3%83%AB)
  - [コードの利用条件](#%E3%82%B3%E3%83%BC%E3%83%89%E3%81%AE%E5%88%A9%E7%94%A8%E6%9D%A1%E4%BB%B6)
  - [ポーランド記法と逆ポーランド記法](#%E3%83%9D%E3%83%BC%E3%83%A9%E3%83%B3%E3%83%89%E8%A8%98%E6%B3%95%E3%81%A8%E9%80%86%E3%83%9D%E3%83%BC%E3%83%A9%E3%83%B3%E3%83%89%E8%A8%98%E6%B3%95)
  - [制御構文](#%E5%88%B6%E5%BE%A1%E6%A7%8B%E6%96%87)
    - [if 文](#if-%E6%96%87)
    - [else 文](#else-%E6%96%87)
    - [elif 文](#elif-%E6%96%87)
    - [for 文](#for-%E6%96%87)
    - [while 文](#while-%E6%96%87)
    - [switch 文](#switch-%E6%96%87)
    - [match 文](#match-%E6%96%87)
    - [do 文](#do-%E6%96%87)
    - [please 文](#please-%E6%96%87)
    - [massage 文](#massage-%E6%96%87)
    - [assert 文](#assert-%E6%96%87)
    - [require 文](#require-%E6%96%87)
  - [データ構造定義構文](#%E3%83%87%E3%83%BC%E3%82%BF%E6%A7%8B%E9%80%A0%E5%AE%9A%E7%BE%A9%E6%A7%8B%E6%96%87)
    - [enum 文](#enum-%E6%96%87)
    - [struct 文](#struct-%E6%96%87)
    - [union 文](#union-%E6%96%87)
    - [class 文](#class-%E6%96%87)
    - [fold 文](#fold-%E6%96%87)
  - [例外構文](#%E4%BE%8B%E5%A4%96%E6%A7%8B%E6%96%87)
    - [try 文](#try-%E6%96%87)
    - [rescue 文](#rescue-%E6%96%87)
    - [ensure 文](#ensure-%E6%96%87)
  - [同期・非同期構文](#%E5%90%8C%E6%9C%9F%E3%83%BB%E9%9D%9E%E5%90%8C%E6%9C%9F%E6%A7%8B%E6%96%87)
    - [sync 文](#sync-%E6%96%87)
    - [async 文](#async-%E6%96%87)
  - [遅延処理構文](#%E9%81%85%E5%BB%B6%E5%87%A6%E7%90%86%E6%A7%8B%E6%96%87)
    - [lazy 文](#lazy-%E6%96%87)
  - [コメント構文](#%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88%E6%A7%8B%E6%96%87)
    - [単一行コメント](#%E5%8D%98%E4%B8%80%E8%A1%8C%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88)
      - [a 通常(doc 非対象)](#a-%E9%80%9A%E5%B8%B8doc-%E9%9D%9E%E5%AF%BE%E8%B1%A1)
      - [a 通常(doc 対象)](#a-%E9%80%9A%E5%B8%B8doc-%E5%AF%BE%E8%B1%A1)
      - [a ヘッダ専用(doc 非対象)](#a-%E3%83%98%E3%83%83%E3%83%80%E5%B0%82%E7%94%A8doc-%E9%9D%9E%E5%AF%BE%E8%B1%A1)
      - [a ヘッダ専用(doc 対象)](#a-%E3%83%98%E3%83%83%E3%83%80%E5%B0%82%E7%94%A8doc-%E5%AF%BE%E8%B1%A1)
    - [ブロックコメント](#%E3%83%96%E3%83%AD%E3%83%83%E3%82%AF%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88)
      - [b 通常(doc 非対象)](#b-%E9%80%9A%E5%B8%B8doc-%E9%9D%9E%E5%AF%BE%E8%B1%A1)
      - [b 通常(doc 対象)](#b-%E9%80%9A%E5%B8%B8doc-%E5%AF%BE%E8%B1%A1)
      - [b ヘッダ専用(doc 非対象)](#b-%E3%83%98%E3%83%83%E3%83%80%E5%B0%82%E7%94%A8doc-%E9%9D%9E%E5%AF%BE%E8%B1%A1)
      - [b ヘッダ専用(doc 対象)](#b-%E3%83%98%E3%83%83%E3%83%80%E5%B0%82%E7%94%A8doc-%E5%AF%BE%E8%B1%A1)
  - [キャスト](#%E3%82%AD%E3%83%A3%E3%82%B9%E3%83%88)
    - [昇格(明示的キャスト)](#%E6%98%87%E6%A0%BC%E6%98%8E%E7%A4%BA%E7%9A%84%E3%82%AD%E3%83%A3%E3%82%B9%E3%83%88)
    - [暗黙キャスト](#%E6%9A%97%E9%BB%99%E3%82%AD%E3%83%A3%E3%82%B9%E3%83%88)
    - [スマートキャスト](#%E3%82%B9%E3%83%9E%E3%83%BC%E3%83%88%E3%82%AD%E3%83%A3%E3%82%B9%E3%83%88)
- [関数型](#%E9%96%A2%E6%95%B0%E5%9E%8B)
  - [関数型の性質 - 遅延評価](#%E9%96%A2%E6%95%B0%E5%9E%8B%E3%81%AE%E6%80%A7%E8%B3%AA---%E9%81%85%E5%BB%B6%E8%A9%95%E4%BE%A1)
  - [関数型の性質 - ラムダ式・ラムダ計算](#%E9%96%A2%E6%95%B0%E5%9E%8B%E3%81%AE%E6%80%A7%E8%B3%AA---%E3%83%A9%E3%83%A0%E3%83%80%E5%BC%8F%E3%83%BB%E3%83%A9%E3%83%A0%E3%83%80%E8%A8%88%E7%AE%97)
- [文字列処理](#%E6%96%87%E5%AD%97%E5%88%97%E5%87%A6%E7%90%86)
  - [正規表現](#%E6%AD%A3%E8%A6%8F%E8%A1%A8%E7%8F%BE)
- [数理計算](#%E6%95%B0%E7%90%86%E8%A8%88%E7%AE%97)
  - [数式処理](#%E6%95%B0%E5%BC%8F%E5%87%A6%E7%90%86)
  - [数値計算](#%E6%95%B0%E5%80%A4%E8%A8%88%E7%AE%97)
  - [グラフ描画](#%E3%82%B0%E3%83%A9%E3%83%95%E6%8F%8F%E7%94%BB)
  - [統計解析](#%E7%B5%B1%E8%A8%88%E8%A7%A3%E6%9E%90)
- [グラフィック・空間モデル処理](#%E3%82%B0%E3%83%A9%E3%83%95%E3%82%A3%E3%83%83%E3%82%AF%E3%83%BB%E7%A9%BA%E9%96%93%E3%83%A2%E3%83%87%E3%83%AB%E5%87%A6%E7%90%86)
  - [多様体](#%E5%A4%9A%E6%A7%98%E4%BD%93)
  - [GUI 処理](#gui-%E5%87%A6%E7%90%86)
    - [コンポーネント](#%E3%82%B3%E3%83%B3%E3%83%9D%E3%83%BC%E3%83%8D%E3%83%B3%E3%83%88)
    - [Web サイト/Web アプリ](#web-%E3%82%B5%E3%82%A4%E3%83%88web-%E3%82%A2%E3%83%97%E3%83%AA)
      - [DomKit](#domkit)
    - [デスクトップアプリ/スマホアプリ](#%E3%83%87%E3%82%B9%E3%82%AF%E3%83%88%E3%83%83%E3%83%97%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B9%E3%83%9E%E3%83%9B%E3%82%A2%E3%83%97%E3%83%AA)
      - [GUI アプリケーションエンジン](#gui-%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%B3)
    - [三次元アプリケーション](#%E4%B8%89%E6%AC%A1%E5%85%83%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)
      - [三次元グラフィックエンジン](#%E4%B8%89%E6%AC%A1%E5%85%83%E3%82%B0%E3%83%A9%E3%83%95%E3%82%A3%E3%83%83%E3%82%AF%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%B3)
- [附属子類](#%E9%99%84%E5%B1%9E%E5%AD%90%E9%A1%9E)
  - [識別子 - Identifier](#%E8%AD%98%E5%88%A5%E5%AD%90---identifier)
  - [演算子](#%E6%BC%94%E7%AE%97%E5%AD%90)
    - [算術演算子](#%E7%AE%97%E8%A1%93%E6%BC%94%E7%AE%97%E5%AD%90)
    - [関係演算子](#%E9%96%A2%E4%BF%82%E6%BC%94%E7%AE%97%E5%AD%90)
    - [論理演算子](#%E8%AB%96%E7%90%86%E6%BC%94%E7%AE%97%E5%AD%90)
    - [その他の演算子](#%E3%81%9D%E3%81%AE%E4%BB%96%E3%81%AE%E6%BC%94%E7%AE%97%E5%AD%90)
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
    - [多様体アノテーション](#%E5%A4%9A%E6%A7%98%E4%BD%93%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)
    - [tsaaspec アノテーション](#tsaaspec-%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)
    - [fpub アノテーション](#fpub-%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)
    - [Hardinfile アノテーション](#hardinfile-%E3%82%A2%E3%83%8E%E3%83%86%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)
- [並行処理・並列処理・分散処理](#%E4%B8%A6%E8%A1%8C%E5%87%A6%E7%90%86%E3%83%BB%E4%B8%A6%E5%88%97%E5%87%A6%E7%90%86%E3%83%BB%E5%88%86%E6%95%A3%E5%87%A6%E7%90%86)
  - [非同期処理](#%E9%9D%9E%E5%90%8C%E6%9C%9F%E5%87%A6%E7%90%86)
  - [高階関数](#%E9%AB%98%E9%9A%8E%E9%96%A2%E6%95%B0)
  - [並行処理](#%E4%B8%A6%E8%A1%8C%E5%87%A6%E7%90%86)
    - [アクター](#%E3%82%A2%E3%82%AF%E3%82%BF%E3%83%BC)
  - [チャンネル](#%E3%83%81%E3%83%A3%E3%83%B3%E3%83%8D%E3%83%AB)
    - [メッセージング](#%E3%83%A1%E3%83%83%E3%82%BB%E3%83%BC%E3%82%B8%E3%83%B3%E3%82%B0)
  - [並列処理](#%E4%B8%A6%E5%88%97%E5%87%A6%E7%90%86)
  - [分散処理](#%E5%88%86%E6%95%A3%E5%87%A6%E7%90%86)
- [例外処理](#%E4%BE%8B%E5%A4%96%E5%87%A6%E7%90%86)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 前文 - Preamble

この言語は、外観はシンプルであり、かつそれでいて内側は複雑である。

Ruby を超える楽しさ、C 言語の速度、MATRAB や Mathematica のような数式になじんだ記述、Julia や Haskell、Octave のような強力な数式処理、Ruby のような関数型プログラミングと命令型プログラミングが絶妙に調和されたデザイン、Dart のようなクロスプラットフォーム、Ruby や Dart のような実用性、LISP(Scheme)から受け継いだ強力な記号操作と推論能力、Ruby のような強力な正規表現とそれに裏付けられた文字列処理、Ruby や Lua のようなグルー性、Dart のようなクラウドコンピューティング、Dart のような簡潔な UI 記述、Scala のような継続、HSP のような専用開発環境を併せ持つ言語を求めてこの言語を設計した。

我々は美的であり、貪欲である。果てしない可能性を追い求めて。

## 概要- Abstract

この言語は、Julia ,Dart ,及び Ruby に触発されて製作されたものであり、Julia, Dart, Ruby, Ada, LISP(Scheme), Haskell, Oz, D, Chestnut,Lury, Scala, Nemerle, HSP 及び OCaml の影響を強く受けている。また、これらの言語及びその他の数多の諸言語を参考にしている。

汎用機能と特化型機能を兼ね備えている超高級言語である。分散処理・並列処理や数理数式処理・科学技術計算・知的推論・統計解析に特化しているほか、グラフィック・空間モデル処理、ハードウェア(インターフェース等)制御、組込システム(センサ/アクチュエータ)制御、文字列処理、データ(構造データ/データベース)処理、サーバ処理等にも幅広くフォーカスされている。手続き型と関数型の性質を兼ね合わせた真のクロスプラットフォーム言語である。

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
- コーディング効率よりも可読性を重視すること
- プリプロセッサマクロを持たないこと
- マルチパラダイム言語
- 強い型検査（コンパイル時および(オプションとして)実行時）
- 自動ビルド(処理系への要求項目)
- -O3/-O4 C lang に匹敵する高速性(処理系への最上級要求事項)

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
契約プログラミング  
Programming by Contract  
文芸的プログラミング  
Literate Programming  
目的プログラミング  
Intentional Programming

## オブジェクト - The Object

総てのリテラルはオブジェクトである。

## 識別名 - Modified Name

ソースコードは総て Unicode で記述され処理される。 代数や関数などの総ての識別子は Unicode で記述し、UTF-8 で保存する。対して ASCII や ANSI、S-JIS はゴミであり、使用できず、また使用してはならない。

識別子は内部的には Symbol 型で評価・処理される。識別子のシンボルは symbol アノテーションで得られる。シンボルから識別子の取得は Symbol.getString ()メソッドで得られる。

同一オブジェクト種別間のみならず、異なるオブジェクト種別の間でも識別名の衝突は許さない。多重定義(異なる引数構成について異なる振舞いをさせること)は、オプショナル引数及び共用体、Type アノテーション、null チェックによって実現する。

## 系列言語形式名前空間

本言語はグルー性をもっており、(後述する)`@using`アノテーションで他の言語を組み込むことができる。FunCobal のコンパイラ・インタプリタ・REPL はこのアノテーションに当たったらその配下のコードをそれぞれの言語処理系の API に投げ、意味論解読した構文木をうけとる。

主な系列言語形式名前空間は次の通りである。

- Bantra : FC/Ches LL Langs : ex. Yezi-diki, Chestnut Bytecode
- Hardin: FC HL Langs : ex. FunCobal, Hjerbata, FC-Shell
- Tolte : Ches HL Langs : ex. Chestnut
- Google: Google Langs : ex. Dart, Go lang

また、記述されているファイルの主たる言語との関係性により、以下の特別指定句にて名前空間を指定することができる。

- This : 自らの属する名前空間を示す
- Sub : 配下の名前空間(DSL など)を示す
- Super : Sub の逆を示す

## 代数 - Algebraic Models

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

### 代数宣言

代数は、変数種名と型名を`::`で結合し、宣言するべき代数の識別名と半角空白を開けて前置する。識別名(同時に初期化たる代入を行う場合にはその終端)の後には同じく半角空白を開けて`\def`を記述することが望ましい。

```FunCobal
Let::Int a \def;
FixedExpr::Int b=30 \def;
```

## 関数

計算や処理の定義。クラス等に所属する関数をメソッドという。`@function`アノテーション影響下では参照透過性をもち、副作用をもたない。

### 関数合成

この言語においては、いかなる関数も任意に合成することができ、関数を引数に渡すこと、及び関数チェーンにより実装できる。数学(代数学)の関数合成と同じである。関数チェーンは、代数学における合成演算子(∘)がドット(`.`)になっただけである。

関数チェーンを行った場合、返り値が次の第一引数となる。この返り値と第一引数の型が違う場合(キャストが指定されている場合を除く)には、普通の代入と同様にエラーが吐かれる。関数の引数渡しと関数チェーンは次のように対応する。

- 引数渡し: 　`f (g (x))`
- 関数チェーン: 　`x.g ().f ()`

## 代数的データ構造

- 連続体：コンストラクタのみの列挙型オブジェクト。エイリアスとして enum をもち、enum 文によって定義される。コンストラクタ必須である。
- 構造体：フィールドのみでメソッドのない直積型オブジェクト。エイリアスとして struct をもち、struct 文によって定義される。コンストラクタは任意である。コンストラクタのない場合は、フィールド宣言時のデータがインスタンス作成時にインスタンスにコピーされる。
- 共用体：フィールドのみでメソッドのない直和型オブジェクト。F#の判別共用体に相当。エイリアスとして union をもち、union 文によって定義される。
- クラス：フィールド・コンストラクタの他にメソッドをもつオブジェクト。エイリアスとして class をもち、class 文によって定義される。コンストラクタ必須である。コンストラクタを省略して暗黙的に単純代入コンストラクタを自動構築することできる。
- 多様体：少なくとも局所的には座標系が定義できるオブジェクト。エイリアスとして fold をもち、fold 文によって定義される。シェイプ、コンポーネントやウィジェット、CG モデルや地理空間データなどがある。[多様体](#%E5%A4%9A%E6%A7%98%E4%BD%93)を参照。

### ミクスイン

クラス等はモジュールをミクスイン(Mixin)し、トレイトやプロトタイプのすべてのメソッドを自由に受け取ることができます。

- プロトタイプ: 　抽象メソッド宣言であり、実装をもたない。Java 言語などのインターフェースに相当する。この場合のプロトタイプは プロトタイプベースのプロトタイプとは異なるので注意のこと。
- トレイト: 　拡張メソッド基盤であり、実装をもつ。識別子が衝突する場合、ミクスイン先におけるエイリアス定義によって解決されるが、欠缺のある場合は、トレイト側の衝突するメソッドが無視(除外)される。

### 連続体

### 構造体と共用体

### クラスとプロトタイプ・トレイト

クラスの定義。基本表記と簡略表記がある

```FunCobal
--- 基本表記
class クラス名 extends 継承元クラス impl プロトタイプ with トレイト {
}
--- 簡略表記
class クラス名 < 継承元クラス : プロトタイプ :: トレイト {
}
```

プロトタイプはクラスに紐づけられたオブジェクトの一種であるが、プロトタイプ単独では定義できない。クラス定義時に deriv キーワードを宣言することにより同名のプロトタイプが暗黙的に定義される。

```FunCobal
--- クラスの定義とプロトタイプの暗黙定義
class クラス名 extends 継承元クラス impl プロトタイプ with トレイト deriv {
}
```

トレイトはクラスに紐づけられたオブジェクトの一種であり、以下の 3 つの制限をクリアしたクラスであれば、トレイトとして提供できる。クラスが具象か抽象かは問わない。クラス定義時に mod キーワードを宣言することにより同名のトレイトが暗黙的に定義される。 1.コンストラクタを定義していない 2.スーパークラスが Any（Any 以外のクラスを継承していない）
3.super キーワードでスーパークラスを参照していない

```FunCobal
--- クラスの定義とトレイトの暗黙定義
class クラス名 extends 継承元クラス impl プロトタイプ with トレイト mod {
}

```

## リテラル表現

## 基本構文

### コーディングスタイル

中括弧(アノテーションの小括弧も同じ)では、始まりのものに直前に半角空白のみを、終わりのものには直後に改行を伴う。制御構文の小括弧については、始まりのものに関し同様。空ブロックはその始まりと終わりに括弧の間に半角空白ただ一つのみを伴う。カンマは行末にある場合は改行、そうでない場合は半角空白ただ一つのみを伴う。

if 文の中括弧の省略は邪悪なのでできない。

### コードの利用条件

### ポーランド記法と逆ポーランド記法

デフォルトでは中置記法であるが、ポーランド記法と逆ポーランド記法もサポートする。

ポーランド記法は`:(operator operand, operand)`、逆ポーランド記法は`:~(operand, operand operator)`と記述する。

### 制御構文

goto 文,comefrom 文,break 文,continue 文,三項条件演算子は有害なので存在しない。

#### if 文

伴う条件式が真だった場合の処理を記述する：

```FanCobal


```

#### else 文

if 文の条件が偽だった場合の処理を記述する：

```FanCobal


```

#### elif 文

else 文とそれに内包された if 文の縮約形である：

```FanCobal


```

は次と等価である：

#### for 文

標準の for ループを使って繰り返しができる。例えば：

```FanCobal


```

#### while 文

while ループはループの前に条件を計算する：

```FanCobal


```

直前に do 文を伴う場合はそのループの後に条件を計算する：

```FanCobal


```

#### switch 文

整数や文字列などの比較によって条件分岐する：

```FanCobal


```

#### match 文

パターンマッチであり、条件の範囲や集合によって条件分岐する：

```FanCobal


```

#### do 文

while 文に伴う：

```FanCobal


```

そのほか、単独で出現してひと纏まりの処理をつくる：

```FanCobal


```

あるいは、引数タプルを伴って nullable 引数を non-null 化する：

```FanCobal


```

あるいは、

#### please 文

do 文ととそれに内包された try 文の縮約形：

```FanCobal
please {
  Future<String> file = File("some-path.ext").readString()
}
```

は次と等価である：

```FanCobal
do {
  try {
    Future<String> file = File("some-path.ext").readString()
  }
}
```

#### massage 文

関数に内包されて、もしくは assert 文や require 文に伴ってメッセージを生成する：

```FanCobal


```

#### assert 文

伴う条件式が偽だった場合に通常の実行を中断させる：

```FanCobal


```

#### require 文

その内包する処理のいづれかが失敗すると通常の実行を中断させる：

```FanCobal


```

### データ構造定義構文

#### enum 文

#### struct 文

#### union 文

#### class 文

#### fold 文

### 例外構文

#### try 文

例外が発生する可能性のある処理を記述し、試行する：

```FanCobal
try {
  Auto::List<Int> ls = List()
  Auto::String str = ls[-1]
}

```

#### rescue 文

例外が発生した場合の処理を記述し、補足した例外を救出する：

```FanCobal
rescue {
  print ("No Index Available, And Illegal Type")
}

```

特定又は限定された例外を救出することもできる：

```FanCobal
rescue (NoValidIndexErr){
  fix ($${1} = ls[$${2}], $${1} = ls[0])
}
rescue (NoMatchTypesErr){
  fix ($${1} = ls[$${2}], $${1} = ls[$${2}] as String)
}

```

※ここで唐突に出てくる`fix (wrong,correct)`は誤った構文パターン検索と修正の機能を提供する。`$${数字}`は構文パターンの任意部分を示すワイルドカード。

また、例外型列挙定義にて、その型の例外を救出する処理を記述する。

```FunCobal
enum NoMatchTypesErr {
  impl = rescue {
    fix ($${1} = ls[$${2}, $${1} = ls[$${1}] as ${2}.type)
  },
  impl = massage (Display disp) {
    disp = "An NoMatchTypesErr occurred: $${0}"
  },
  impl = do {
    -- error object
  },
}
```

#### ensure 文

例外が発生するか否かに関わらず実行する処理を記述する：

```FanCobal
ensure {
  print ("End Proc")
}

```

### 同期・非同期構文

#### sync 文

#### async 文

### 遅延処理構文

#### lazy 文

### コメント構文

#### 単一行コメント

次の 4 種に対応している。

##### a 通常(doc 非対象)

`--- comments`

##### a 通常(doc 対象)

`[] ( comments )`

##### a ヘッダ専用(doc 非対象)

`#! comments`

##### a ヘッダ専用(doc 対象)

`/// comments`

#### ブロックコメント

次の 4 種に対応している。doc 対象でないものは全てネストに対応している(doc 対象のものも最も内側になる場合に限りネストされることができる)。

##### b 通常(doc 非対象)

```FunCobal
{-
  comments
  for
  multi-lines
-}
```

##### b 通常(doc 対象)

```FunCobal
(*
  comments
  for
  multi-lines
*)
```

##### b ヘッダ専用(doc 非対象)

```FunCobal
//*
  comments
  for
  multi-lines
///
```

##### b ヘッダ専用(doc 対象)

```FunCobal
///
|  comments
|  for
|  multi-lines
///
```

### キャスト

#### 昇格(明示的キャスト)

Int 型から Num 型、Real 型から Complex 型、String 型から Chd 型、Char 型から String 型などのように、情報及び精度を失わせない場合は、次のように明示的キャストを行うことができる。この明示的キャストを昇格という。

情報及び精度を失わせる場合においても、warning が出るものの明示的キャストを行うことができる。

明示的キャスト小括弧で囲った型名を前置するか、或いは as 構文で昇格する。

```FunCobal
Auto::Int bit_64 <- 64
Auto::Double dou_bit <- (Double) bit_64
```

或いは

```FunCobal
Auto::Char ch <- "c"
Auto::String str <- ch as String
```

#### 暗黙キャスト

暗黙キャストによるメモリ侵犯の虞を考慮し、暗黙キャストを提供しない。

#### スマートキャスト

代数から type パラメータで型名を出し eq メソッドで照合し if 文で条件分岐することで、if 文内の処理で明示キャストを必要としない。

```FunCobal
Void sampleFunc (Literal var) {
  if (var.type.eq(String)) {
    print(var.length);
  }
  else {
    print(var.toString.length);
  }
}

```

## 関数型

@function アノテーションで囲われたエリア内では、関数型プログラミングにて記述することができる。

```FunCobal
@function (
  Let::Int factor <- (Int n){
    if (n>0) {
      n * factor(n - 1)
    }
    else {
      1
    }
  }
)
```

### 関数型の性質 - 遅延評価

@function アノテーション配下或いは laziness 指定子のついたブロック内、lazy 指定子のついた式において遅延評価が適用される。

```FunCobal
--- 遅延評価　この例の場合変数dが呼び出されるまで9+5はされない
lazy.Let::Int d = 9+5;

--- 遅延評価　lpブロック内の処理はlpブロックを呼び出す処理が評価されるまで評価されない
Block lp <- laziness {
    print (9.toString ())
}
```

### 関数型の性質 - ラムダ式・ラムダ計算

ラムダ記号`>\`を用いてラムダ式を表現し、ラムダ計算をすることができる(@function アノテーション外でも利用できる)。

記法は`(>\ (引数) -> 処理)`である。

## 文字列処理

### 正規表現

本言語、もとい FunCobal family プロジェクトは専用の正規表現ライブラリ(とはいえ当然他の言語にも導入可能だが。)である「[鬼瀬](https://github.com/FunCobal-family/Onigase)」("[Onigase](https://github.com/FunCobal-family/Onigase)")を擁しており、研究開発が進行している。

詳しくは上記リンク先を参照の事。

## 数理計算

### 数式処理

### 数値計算

### グラフ描画

### 統計解析

## グラフィック・空間モデル処理

### 多様体

### GUI 処理

GUI 処理は`@sdata`アノテーション(後述)等を用いてコードを直書きすることも可能ではあるが、コンパイル/実行速度の向上にはほとんど資さないし、そのうえ可読性や生産性を大きく損なうので特に特殊な処理を行うのでなければ直書きはすべきでない。

GUI 処理の為には多様体のシステム及びグラフィカルパーツであるコンポーネントを用いる事が良い。

#### コンポーネント

#### Web サイト/Web アプリ

##### DomKit

組込ライブラリである DomKit の各パッケージを用いて`@sdata`アノテーションによる構造データが操作される。コンポーネントに基づいて DomKit により画面が描画される。

#### デスクトップアプリ/スマホアプリ

##### GUI アプリケーションエンジン

#### 三次元アプリケーション

##### 三次元グラフィックエンジン

## 附属子類

### 識別子 - Identifier

### 演算子

#### 算術演算子

|  演算子   | 意味                     | 同値        | 対応メソッド    |
| :-------: | ------------------------ | ----------- | --------------- |
|   a + b   | 和                       |             | add (a, b)      |
|   a - b   | 差                       |             | sub (a, b)      |
|  a \* b   | 積                       |             | mul (a, b)      |
|   a / b   | 商                       |             | div (a, b)      |
|   a % b   | 剰余                     |             | mod (s, b)      |
|   a @ b   | 剰余差                   | a - (a % b) | sub/mod (a, b)  |
|  a \| b   | 整除                     | (a @ b) / b |                 |
|  a ^ ind  | 冪                       |             | power (a, ind)  |
| ind \_/ a | 冪根                     |             | sqrt (a, ind)   |
|   !/ a    | 平方根                   |             | sqrt (a, 2)     |
|   !!/ a   | 立法根                   |             | sqrt (a, 3)     |
|           | 対数                     |             | log (a , ind)   |
|           | 自然対数                 |             | log (a , E)     |
|           | 常用対数                 |             | log (a , 10)    |
|           | 論理対数                 |             | log (a , 2)     |
|           | 対数根                   |             | power (ind, a)  |
|    a !    | 階乗                     |             | factor (a)      |
|   !! a    | 階乗(前置)               |             | factor (a)      |
|           | 絶対値                   |             | abs (a)         |
|   「 a    | 天井関数                 |             | ceil (a)        |
|   a 」    | 床関数                   |             | floor (a)       |
|           | クヌース・テトレーション |             | knuth3(a, b)    |
|           | クヌース・ペンテーション |             | knuth4(a, b)    |
|           | コンウェイ・チェーン     |             | conway(a, b, c) |

#### 関係演算子

| 演算子 | 意味       | 同値                                          | 対応メソッド |
| :----: | ---------- | --------------------------------------------- | ------------ |
|   =    | 等しい     |                                               | eq(a, b)     |
| !=,<>  | 等しくない |                                               | neq(a, b)    |
|   >    | 超過       |                                               |              |
|   <    | 未満       |                                               |              |
| =>,>=  | 以上       |                                               |              |
| =<,<=  | 以下       |                                               |              |
|        | 包含       | この場合 a,b はコレクション又はクラス、構造体 |              |
|        | 被包含     | この場合 a,b はコレクション又はクラス、構造体 |              |
|        | 要素       | この場合 b はコレクション又はクラス、構造体   |              |
|        |            |                                               |              |
|        |            |                                               |              |
|        |            |                                               |              |
|        |            |                                               |              |
|        |            |                                               |              |

#### 論理演算子

- 第一基本一項論理演算子

| 演算子 | 意味 | 同値            |           |
| :----: | ---- | --------------- | --------- |
|  ! a   | 否定 | a !& a, a !\| a | not(a, b) |

- 第一基本二項論理演算子

|        演算子         | 意味   | 同値       | 対応メソッド |
| :-------------------: | ------ | ---------- | ------------ |
| a \| \| b 又は a or b | 論理和 | !(a !\| b) | or (a, b)    |
|  a && b 又は a and b  | 論理積 | !(a !& b)  | and (a, b)   |

- 第二基本二項論理演算子

|        演算子        | 意味       | 同値        | 対応メソッド |
| :------------------: | ---------- | ----------- | ------------ |
| a !\| b 又は a nor b | 否定論理和 | !(a \|\| b) | nor (a, b)   |
| a !& b 又は a nand b | 否定論理積 | !(a && b)   | nand (a, b)  |

- 組立二項論理演算子

|       演算子        | 意味         | 同値                      | 対応メソッド |
| :-----------------: | ------------ | ------------------------- | ------------ |
| a `^ b 又は a xor b | 排他的論理和 | (a && !b) \|\| (!a && b ) | xor (a, b)   |
| a `/ b 又は a sub b | 論理差       | a && !( a && b )          | sub (a, b)   |
|                     | 含意         | !a \|\| b                 |              |
|                     | 補論理積     | !(a \|\| b) && (a && b)   |              |

#### その他の演算子

- 一項演算子

| 演算子 | 意味                 | 同値 | 対応メソッド |
| :----: | -------------------- | ---- | ------------ |
|   ++   | (和差)インクリメント |      |              |
|   --   | (和差)デクリメント   |      |              |
|  \*\*  | 乗除インクリメント   |      |              |
|   //   | 乗除デクリメント     |      |              |
|   +=   | 加算                 |      |              |
|   -=   | 減算                 |      |              |
|  \*=   | 乗算                 |      |              |
|   /=   | 除算                 |      |              |

- 二項演算子

|   演算子    | 意味       | 同値 | 対応メソッド |
| :---------: | ---------- | ---- | ------------ |
|     <-      | 代入(定義) |      |              |
| x.f ().g () | 結合(合成) |      | f (g (x))    |
|             |            |      |              |
|             |            |      |              |
|             |            |      |              |
|             |            |      |              |
|             |            |      |              |
|             |            |      |              |

- 三項演算子

| 演算子 | 意味 | 同値 | 対応メソッド |
| :----: | ---- | ---- | ------------ |
|        |      |      |              |
|        |      |      |              |
|        |      |      |              |
|        |      |      |              |
|        |      |      |              |
|        |      |      |              |
|        |      |      |              |
|        |      |      |              |

### 指定子

指定子は対象リテラルの直前にドット`.`で結合する。例えば、`public.Class sample{}`のようにである。

#### アクセス権指定子

リテラルへのアクセス権をコントローリする。

- public 　すべての場所からアクセス可能(pub と省略することも可)
- default 　ファイル内からのみアクセス可能(デフォルト、省略可能)
- protected 　ブロック内、同一オブジェクト内及び子孫オブジェクトからのみアクセス可能(prot と省略することも可)
- private 　ブロック内及び同一オブジェクト内からのみアクセス可能(オブジェクト識別子をダブルアンダーバーで始めることでも表現できる)

#### 静動指定子

静的性/動的性を指定する。省略可能なデフォルトはリテラルの種類によって異なる。

- dynamic 　動的性を与える(dyn と省略することも可)
- static 　静的性を与える(stat と省略することも可)

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

- `@function`：　関数型プログラミングによる記述

#### 言語間アノテーション - Inter-language Annotation

- `@using`: 　プログラム中に他の言語を組み込む。系列言語形式名前空間で修飾された言語名に続けて小括弧に囲んだ組込みプログラムを記述する。

```FunCobal
@using Sub:tex (
    //code written in Texicon(DSL of FunCobal,lang bind of Hardin Namespace)

)


@using This:hjr (
    //code written in Hjerbata(lang bind of Hardin Namespace)

)


@using Tolte:Chestnut (
    //code written in Chestnut(lang bind of Tolte Namespace)

)

@using Google:Dart (
    //code written in Dart(lang bind of Google Namespace)

)

@using Google:Go (
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
- `:implements`: 　`:net` アノテーションによる設定にたいしライブラリ パッケージを関連づける。

#### 多様体アノテーション

fold 文にの前行に付けて多様体の種類を示す。

- `@Shape`: 点や線、円や多角形、弧などの図形
- `@Component`: Web プログラミング等に用いるコンポーネント
- `@Widget`: アプリケーション等に用いるウィジェット
- `@Model`: obj ファイルや std ファイル、MMD モデルその他の CG モデル
- `@Geographic`: 地理空間情報

#### tsaaspec アノテーション

パッケージ構成ファイル「tsaaspec」で用いるもの

#### fpub アノテーション

ライブラリ構成ファイル「fpub」で用いるもの

#### Hardinfile アノテーション

ビルドファイル「Hardinfile」で用いるもの

## 並行処理・並列処理・分散処理

### 非同期処理

非同期処理の第一の方法は、async 文と await 指定子を用いる：

```FunCobal
//非同期処理
async {
    await.doing();
}
```

resolve 文、reject 文を用いてメッセージを返すこともできる：

```FunCobal
//(非同期処理の一種)
async {
    //await.doing();
}
resolve {
    //処理成功時に流すメッセージデータの生成処理
}
reject {
    //処理失敗時に流すメッセージデータの生成処理
}
```

### 高階関数

この言語では、各種の高階関数を備えている。

### 並行処理

この言語では、並行処理に対するアプローチとして、スレッド間で可変ステートを共有できないようにするという重要な概念を中心に据えており、アクターモデルとメッセージングにより並行処理が制御される。これは堅牢性を高めるのにも役立つ。

#### アクター

この言語では、すべてのものがアクターである。

アクターは並行的に受信するメッセージに対応した以下のような振る舞いを備えた計算実体である

- （他の）アクターに有限個のメッセージを送信する。
- 有限個の新たなアクターを生成する。
- 次に受信するメッセージに対する動作を指定する。

アクターは他のアクターに依存せず、独立並行的に動作する。

### チャンネル

アクター同士は相互のやり取りのためにチャンネルを開くことができる。チャンネルは一方通行のホースのようなもので、入口である tx と出口である rx のタプルで構成される。チャンネルはアクターモデルにおけるアドレスをラッパーする。

```FunCobal
--- チャンネルを用いたアクターである関数を定義
Let::Fn<Void> threadTest1 <- (Chan tx) async {
  Let::Int val = 9
  tx.send()
}
Let::Fn<Void> threadTest2 <- (Chan rx) async {
  print (rx.recv ().toString ())
}
--- アクターシステムとチャンネルを宣言
Let::Fun ftr <- actor ()
Let::Tuple<chan> ch <- channel ()
--- アクターをアクターシステムに登録
ftr.set () <- threadTest1 (ch.tx)
ftr.set () <- threadTest2 (ch.rx)
--- 登録したアクターを起動する
ftr.go ()
```

#### メッセージング

アクター同士はメッセージのやり取りによって相互に通信することができる。
メッセージのやり取りには、massage 文及び暗黙プロパティにて行う。

### 並列処理

### 分散処理

アクターモデルによる並行処理の技法は、ネットワークを介した分散処理にもそのまま適用できる。

ネットワークインターフェースはアクターモデルにおけるアドレスのもう一つのラッパーである。

ネットワークインターフェースは、インターネットプロトコルとチャンネルを接続する。

## 例外処理

```FunCobal
//The Exceptions.
do {
    /* Something code that may occur exceptions */
    throw Exception;//throw Exception
    raise Exception;//or for this what alias of it
    throw SomeException;//throw Exception in type "SomeException"
}
catch {
    /* Something code to do when occurred some exceptions */
}
catch (SomeException e) {
    /* Something code to do when occurred exceptions in type "SomeException" */
}
ensure {
    /* Something code to do in regardless of raise exceptions */
}
else {
    /* Something code to do when not occurred any exceptions what written rescue code */
}
```
