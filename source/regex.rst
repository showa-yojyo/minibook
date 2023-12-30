======================================================================
正規表現学習ノート
======================================================================

.. contents::

資料
======================================================================

`Regular expression - Wikipedia <https://en.wikipedia.org/wiki/Regular_expression>`__
   Wikipedia の正規表現に関する記述だ。公平性と専門性のバランスが良い。特に
   Syntax の節をよく読んでおきたい。

教材
----------------------------------------------------------------------

`Regular Expressions - Wikibooks <https://en.wikibooks.org/wiki/Regular_Expressions>`__
   教科書。こちらは読みやすさ重視か。用語集が便利。
`RegexOne - Learn Regular Expressions <https://regexone.com/>`__
   学習する正規表現の構成物をページ右柱を見ればわかるようになっている。言語別案
   内もうれしい。
`Regex Tutorial—From Regex 101 to Advanced Regex <https://www.rexegg.com/>`__
   文章が上手い。
`Regular-Expressions.info`_
   主要正規表現エンジン機能表が便利だ。エンジンごとに特定の機能が利用可能である
   かどうかを調べるのに最適。プログラマーはブラウザーのブックマークに追加してお
   くのが良い。

   チュートリアルの文章の量が多い。

ツール
----------------------------------------------------------------------

JavaScript の正規表現エンジンで事足りるならばブラウザーの開発ツールコンソールを
使えばよい。

`regex101: build, test, and debug regex <https://regex101.com/>`__
   正規表現と対象テキストを入力してマッチや置換を実行するオンラインツール。これ
   一本で事足りるかもしれない。普段は PCRE2 で検証すればよく、特定のエンジンを試
   したい時に限って :guilabel:`FLAVOR` を Python などに変更するという使い方でい
   い。
`RegExr: Learn, Build, & Test RegEx <https://regexr.com/>`__
   TBW
`PowerGREP <https://www.powergrep.com/>`__
   «Windows grep Software to Search (and Replace) through Files and Folders on
   Your PC and Network» とのことだ。

`Regular-Expressions.info`_ の Applications and Languages の章も参照。

言語別
----------------------------------------------------------------------

`Regular expressions - JavaScript
<https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions>`__

`Regular Expression Language - Quick Reference
<https://learn.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference>`__

`Regular Expression HOWTO <https://docs.python.org/3/howto/regex.html>`__

メモ
======================================================================

* NFA と DFA のどちらかを選べる場合、通常は NFA が最も速い。実際、現代の言語では
  これが最も一般的な実装だ。
* 式を評価するために括弧が必要だが、データを捕捉する必要がない場合は
  :regexp:`(?: ... )` 構文を使う。
* ドットを控えめに使う。
* ドットは最も誤用されるメタ文字だ。
* :regexp:`\h` が使えるならば :regexp:`\s` に優先して使うほうがいい。
* :regexp:`\v` が使えるならば :regexp:`[\r\n]` に優先して使うほうがいい。
* 正規表現をどこまで完璧にするかは、その正規表現で何をしたいかによって決まる。
  ユーザーの入力を検証するのであれば、完璧でなければならない。
* 入力を検証する前に、文字列前後の空白を除去しておく。
* Python に :regexp:`\z` はない。
* 正規表現エンジンに捕捉を back track させたくない場合は atomic group を使用する
  ことが可能だ。
* 正規表現によっては前方参照という概念があり得る。
* アクセント付きのアルファベットは一文字ではない場合がある。
* Unicode には平仮名および片仮名という区分が設けられている。それを利用した正規表
  現記号列がある。
* Lookaround が絡む正規表現を組み立てることが難し過ぎる。
* ソースコードで置換テキストを文字列定数として指定する場合、プログラミング言語に
  よって文字列定数内で特別な扱いを受ける文字をプログラマーが知っていなければなら
  ない。
* :program:`grep` で複数行モードはあり得ない。
* GNU :program:`grep` は Linux で最もよく使われている :program:`grep` の一種だ。
  テキスト指向エンジンと正規表現指向エンジンの両方を使う。後方参照を使用する場合
  は正規表現指向エンジンを使用する。それ以外の場合はより高速なテキスト指向エンジ
  ンを使用する。


.. _Regular-Expressions.info: https://www.regular-expressions.info/refflavors.html
