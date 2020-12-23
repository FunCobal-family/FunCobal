<img src="./FunCobal_Language_Logo.svg" width="150em" style="float:left" />

# FanCobal；FanCoBal 第一世代

![GitHub](https://img.shields.io/github/license/FunCobal-family/FunCobal?style=plastic&label=%E4%BD%BF%E7%94%A8%E8%A8%B1%E8%AB%BE%E6%9B%B8)
![GitHub repo size](https://img.shields.io/github/repo-size/FunCobal-family/FunCobal?label=%E3%83%AC%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%82%B5%E3%82%A4%E3%82%BA)
![GitHub language count](https://img.shields.io/github/languages/count/FunCobal-family/FunCobal?label=%E4%BD%BF%E7%94%A8%E8%A8%80%E8%AA%9E%E6%95%B0)
![GitHub top language](https://img.shields.io/github/languages/top/FunCobal-family/FunCobal?label=%E6%9C%80%E5%A4%9A%E4%BD%BF%E7%94%A8%E8%A8%80%E8%AA%9E)
![GitHub last commit](https://img.shields.io/github/last-commit/Funcobal-family/FunCobal?label=%E6%9C%80%E7%B5%82%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E6%97%A5)
![GitHub Release Date](https://img.shields.io/github/release-date/FunCobal-family/FunCobal?label=%E6%9C%80%E7%B5%82%E3%83%AA%E3%83%AA%E3%83%BC%E3%82%B9%E6%97%A5)

![GitHub release (latest by date)](https://img.shields.io/github/v/release/FunCobal-family/FunCobal?style=plastic&label=%E6%9C%80%E7%B5%82%E3%83%AA%E3%83%AA%E3%83%BC%E3%82%B9)
![GitHub commits since tagged version](https://img.shields.io/github/commits-since/FunCobal-family/FunCobal/Test-v0.0.0.2dev0-d181120?label=%E6%9C%80%E7%B5%82%E3%83%AA%E3%83%AA%E3%83%BC%E3%82%B9%E3%81%8B%E3%82%89%E3%81%AE%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E6%95%B0)
![GitHub Hacktoberfest combined status](https://img.shields.io/github/hacktoberfest/2020/FunCobal-family/Funcobal?label=Hacktoberfest%E6%A2%B1%E6%9D%9F%E6%B8%88%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9)
![GitHub closed issues](https://img.shields.io/github/issues-closed/FunCobal-family/FunCobal?label=closed+issue)

![GitHub contributors](https://img.shields.io/github/contributors/FunCobal-family/FunCobal?label=%E9%96%8B%E7%99%BA%E5%8F%82%E5%8A%A0%E8%80%85%E6%95%B0)
![GitHub contributors](https://img.shields.io/github/contributors-anon/FunCobal-family/FunCobal?label=%E9%96%8B%E7%99%BA%E5%8F%82%E5%8A%A0%E8%80%85%E6%95%B0%2F%E5%8C%BF%E5%90%8D%E5%90%AB%E3%82%80)
![Discord](https://img.shields.io/discord/787660506957611018?style=plastic&label=%E9%96%8B%E7%99%BA%E8%80%85Chat%28Discord%2F%E3%80%8C%E9%9B%BB%E8%84%B3Lang%3A%3AClib%E3%80%8D%E5%86%85%E3%80%8C%23FunCobal+family%E3%80%8D%29)

<p style="clear:both"></p>

## 前文 - Preamble

この言語は、外観はシンプルであり、かつそれでいて内側は複雑である。

Ruby を超える楽しさ、C 言語の速度、MATRAB や Mathematica のような数式になじんだ記述、Julia や Haskell、Octave のような強力な数式処理、Ruby のような関数型プログラミングと命令型プログラミングが絶妙に調和されたデザイン、Dart のようなクロスプラットフォーム、Ruby や Dart のような実用性、Ruby のような強力な正規表現とそれに裏付けられた文字列処理、Ruby や Lua のようなグルー性、Dart のようなクラウドコンピューティング、Dart のような簡潔な UI 記述を併せ持つ言語を求めてこの言語を設計した。

我々は美的であり、貪欲である。果てしない可能性を追い求めて。

([FunCobal 基本仕様案](./doc/FunCobal基本仕様案.md)より引用)

## 概要- Abstract

この言語は、Julia ,Dart ,及び Ruby に触発されて製作されたものであり、Julia, Dart, Ruby, Ada, Haskell, 及び OCaml の影響を強く受けている。また、これらの言語及びその他の数多の諸言語を参考にしている。

汎用機能と特化型機能を兼ね備えている超高級言語である。分散処理・並列処理や数理数式処理・科学技術計算・統計解析に特化しているほか、グラフィック・空間モデル処理、ハードウェア(インターフェース等)制御、組込システム(センサ/アクチュエータ)制御、文字列処理、データ(構造データ/データベース)処理、サーバ処理等にも幅広くフォーカスされている。手続き型と関数型の性質を兼ね合わせた真のクロスプラットフォーム言語である。

簡潔かつ分かりやすい記法で扱いやすく、また数式処理等はそれぞれになじんだ記法が採用されており、複雑な数式やアルゴリズムをストレスなく自然、シンプルかつリーダブルに記述できる。加えて-O3/-O4 C lang に匹敵する高速性(処理系への最上級要求事項)がある。

([FunCobal 基本仕様案](./doc/FunCobal基本仕様案.md)より引用)

## 仕様書(作業中)

FunCobal 言語の仕様は、[FunCobal 基本仕様案](./doc/FunCobal基本仕様案.md)に記載されている。

## 開発者用

### テスト

Test-v0.0.0.2dev0:d181120(バージョン附番様式：：左はリリーステスト用のもので実在しないバージョン)

### regular update

一日一回以上コミットする。変更部分のない場合は必要ない。次に示す定時に行い、この各定時毎のうちの最初のコミットを regular update とする。

各定時 y は各基準時を x として、x-2h<= y <= x+4h の区間である。

昼アップデート基準時：正午(JST)
夜アップデート基準時：正子(JST)

コミットメッセージの書式は"
$day $month \$time-area regular update"である。このうち、月日は英語・英国式・省略形、定時名は noon 又は midnight である。本書式における月日は、各定時の開始時点(JST)のものとするが、昼アップデート時は前日、夜アップデート時は翌日の月日とする。
