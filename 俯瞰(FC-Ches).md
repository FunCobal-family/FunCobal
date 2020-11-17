
# FunCobal family

\<H Processing System>　Language Processing System  
\<H SDK Tool Chain>　SDK Extensions for H Processing System  
    \<H Compiler Collection>　FunCobal family Language Compilers  
    \<H Bins Codes>　Binary Codes Tool with FunCobal family  
    \<H AutoHardin>　FunCobal family Language Auto Builder  
    \<H Test Manager>　Tester & Debugger  
    \<H Driven CronBase>　CI & CD Host  
    \<H OriGen>　Parser Generator  
    \<H Expressions>　Lint, Syntax Highlight  
\<HardingTsaa>　 Package Manager&Installer  
    [./Hardinfile]　　Package Build Script  
    [./* .hjrspec]or[./* .tsaaspec]　Library package Specification  
※IDE/Editor ... VisualStudio, VSCode, CLion, , , etc.  
※Version Manager ... Git, GitHub, , , etc.  

# 系列言語形式名前空間

- Bantra : FC/Ches LL Langs : ex. Yezi-diki, Chestnut Bytecode
- Hardin: FC HL Langs : ex. FunCobal, Hjerbata, FC-Shell
- Tolte : Ches HL Langs : ex. Chestnut

.  
.  

.　　　　　　　   ↙ Hardin: .*  
execute ← Bantra: .*  
.　　　　　　　   ↖ Tolte: .*

# バイトコード/ワードコード

- LLCIL))Chestnut Bytecode  (:BC,Tolte::Bantra:)
- LLCIL))"細葉子" a.k.a. "Yezi-diki" (:WC,Hardin::Bantra:)

# FIDOLS

Description :Package Identifying System File for HardingTsaa  
Acronym of : FunCobal Installing Dandified Original Leaves Specifier  
Configuration :  
[./* .fidols]  
　[./Hardinfile]  
　[./* .hjrspec] or [./* .tsaaspec]  
Management Method : like Package Managers of Gentoo Linux, and add specifications and implementations focused on to solve Satisfiability Problem.

# Specification of H Compiler Collection

Name : H Compiler Collection  
Description : Compilers for languages of FunCobal family, and Chestnut  
Outline : put Intermediate Language between Source and executive
Source  to CIL : Source → CIL→ execute with Interpreter (with embedding Assembly in C++ code)  
Source  to NASM: Source → NASM→ Object file  
CIL to Word Code : CIL → Word Code  
CIL :  **** , Intermediate Language for Chestnut as a low-level programming language  
Implementation : Each  of C++/Java/Dart/Julia/FunCobal  
Lead Developers : Garnet (for C++), Halka (for Java/Dart/Julia/FunCobal imp.)  
