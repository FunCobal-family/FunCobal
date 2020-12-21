# Chestnut 捆束仕様書

## 概要

Chestnut 言語の捆束は方言の実装による。この方言は公認である。

## 基本仕様書

基本仕様は本家 Chestnut 言語の仕様書による。詳しくは[こちら](https://github.com/Garnet3106/chestnut/blob/develop/docs/ja/releases/ches0/spec/index.md)を参照。

## 拡張仕様書

名称：Chestnut Pi  
目的:  
　本家 Chestnut から FunCobal へのステップアップのため  
　 FunCobal にクラスベースを埋め込むために  
　　　　(クラスベース指向者の取り込み目的)  
方式：FunCobal に公式バインディングする  
標準処理系：FunCobal の HPS の YACS サブシステム  
拡張項目：
　制御構文の終了標識の end の義務化  
　 swich の case の break を end に  
　制御構文に限りネスト可能  
　制御構文でないブロックとして go-end を追加  
　 FunC 風コメントの許可(doc 非対象コメントに限る)  
　言語間グルー機構の配備
