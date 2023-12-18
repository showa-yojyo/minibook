======================================================================
Jekyll 利用ノート
======================================================================

.. note::

   .. code:: text

      DISTRIB_ID=Ubuntu
      DISTRIB_RELEASE=22.04
      DISTRIB_CODENAME=jammy
      DISTRIB_DESCRIPTION="Ubuntu 22.04.3 LTS"

   :Ruby: 3.0.2p107
   :RubyGems: 3.3.5
   :Bundler: 2.4.22
   :Jekyll: 4.3.2
   :Minima: 2.5.1

.. contents::

資料
======================================================================

公式文書
----------------------------------------------------------------------

`Jekyll <https://jekyllrb.com/>`__
   Jekyll 公式サイト。特に重要なのが次の章だろう：

   `Using Jekyll with Bundler <https://jekyllrb.com/tutorials/using-jekyll-with-bundler/>`__
      Ruby プロジェクトの作法の初歩と思われる :program:`gem` および
      :program:`bundle` の使用方法について述べられている。Quickstart の次に読ん
      でいい。これは必読。
   `Step by Step Tutorial <https://jekyllrb.com/docs/step-by-step/01-setup/>`__
      :file:`Gemfile` の導入をなるべく後回しにしての Jekyll サイト構築チュートリ
      アルだ。Deploy の章を先頭近くに移した版を読んでみたい。

`Daring Fireball: Markdown <https://daringfireball.net/projects/markdown/>`__
   Markdown 公式サイトと思われる。
`kramdown <https://kramdown.gettalong.org/>`__
   Jekyll が使用している Markdown 解析器パッケージの公式サイト。特に
   Documentation/Configuration Options は :file:`_config.yml` を書く時に参照す
   る。
`Liquid <https://jekyllrb.com/docs/liquid/>`__
   Jekyll が使用しているテンプレートエンジンパッケージ Liquid の公式サイト。
   Sphinx における Jinja2 に相当する機能を担当する。
`List of supported languages and lexers · rouge-ruby/rouge Wiki <https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers>`__
   コードテキストに対する構文強調機能を担当する Rouge の対応言語一覧を掲載してい
   る。
`GitHub - jekyll/minima <https://github.com/jekyll/minima>`__
   既定テーマ minima の GitHub リポジトリー。バージョン 3 開発中？

教材
----------------------------------------------------------------------

`Mastering Jekyll - Made Mistakes <https://mademistakes.com/mastering-jekyll/>`__
   特にリンク周りの説明が詳しい。時系列に整理する必要のない記事の配置のコツな
   ど、有用な知識が他にも述べられている。スタイリング理論はやや難しい。

Jekyll サイト用意手順
======================================================================

公式サイトの Quickstart の記述を再現していけば問題はない。本ノートでは WSL の
Ubuntu 環境を想定しているので Jekyll on Ubuntu の節に従う。

開発環境に対して一度きりの設定手順
----------------------------------------------------------------------

1. :program:`ruby` がなければインストールする
2. 環境変数を設定する
3. RubyGems つまり :program:`gem` がなければインストールする
4. Bundler つまり :program:`bundler` がなければインストールする
5. Jekyll つまり :program:`jekyll` がなければインストールする

システムにインストール済みの Ruby, RubyGems, Bundler, Jekyll があればそれを使用
してよい。ない場合に限り Quickstart の記述に従ってインストールする。

RubyGems と Bundler が参照する環境変数各種の値を XDG Base Directory
Specification 愛好家としては次のようにしたい：

.. code:: bash

   export GEM_HOME="$XDG_DATA_HOME/gem"
   export GEM_SPEC_CACHE="$XDG_CACHE_HOME/gem"

   export BUNDLE_USER_CONFIG="$XDG_CONFIG_HOME/bundle"
   export BUNDLE_USER_PLUGIN="$XDG_DATA_HOME/bundle"
   export BUNDLE_USER_CACHE="$XDG_CACHE_HOME/bundle"

上記をファイル :file:`.bashrc` に書いておく。ここで、XDG 変数各種については適切
に設定済みであるとする。

そして、:program:`gem` を使うのはこれで最後となる。作業ディレクトリーにファイル
:file:`Gemfile` があるときには必ず :program:`bundle` から Jekyll コマンドを実行
しろ。

Jekyll サイト仮設
----------------------------------------------------------------------

適当なディレクトリーに移動して Jekyll サイトを構築していく。ここでは
:file:`myblog` というディレクトリーに Jekyll サイトのルートを合わせるように作
る：

.. code:: console

   $ mkdir myblog && cd $_
   $ jekyll new .
   $ bundle exec jekyll serve

``jekyll new`` コマンドの実行によりいくつかのファイルが生じる。この段階で重要な
のは次の三つ：

* :file:`Gemfile`
* :file:`Gemfile.lock`
* :file:`_config.yml`

:file:`Gemfile` を編集する
----------------------------------------------------------------------

このファイルを変更する機会はそれほどない。手をいれる可能性のある箇所を列挙する：

1. ``gem "jekyll"`` から始まる行
2. ``gem "minima"`` から始まる行
3. ``group :jekyll_plugins do`` ... ``end`` ブロック

GitHub Pages での厳密な運用を想定している場合、1. の行を削って次のような行に置き
換える。主旨は GitHub でのビルドとローカル環境でのビルドにおける gem バージョン
を一致させたいということだそうだ。それが気にならないならば既定の Jekyll のままで
良い。

.. code:: ruby

   gem "github-pages", "~> 228", group: :jekyll_plugins

ここで ``228`` と示した数は、実際には次のページで適切な値を確認して決定しろ：
`Dependency versions | GitHub Pages <https://pages.github.com/versions/>`__

.. admonition:: 読者ノート

   ``github-pages`` を使うことにした場合、ローカル環境ではさらに ``webrick`` と
   いう gem が必要になる可能性が高い。手作業で :file:`Gemfile` を編集してもよい
   が、この場合はコマンド実行のほうが早い：

   .. code:: console

      $ bundle add webrick

Jekyll テーマを既定の ``minima`` から別のものに変更したい場合、2. を削ってテーマ
配布者の指示に従って新しい行を記入しろ。

Jekyll プラグインを追加または削除する場合、3. の ``do`` ... ``end`` に行を追加す
る。行の記述はプラグイン配布者の指示に従え。

以上の編集により gem 構成が変化した場合、サイト動作確認までに次のコマンドを実行
して当該 gem をローカル環境にインストールしろ：

.. code:: console

   $ bundle install

:file:`Gemfile.lock` を更新する
----------------------------------------------------------------------

このファイルを更新することは保守に相当する。Jekyll サイト準備中に行う必要のない
ものだが、ノート構成の便宜上ここに記す。

   If you followed our setup recommendations and installed Bundler, run ``bundle
   update jekyll`` or simply ``bundle update`` and all your gems will update to
   the latest versions.

定期的に、できれば自動で ``bundle update`` を実行して gem を更新したい。

.. admonition:: 読者ノート

   Ruby 101 より RubyGems の核となる概念の説明を引用しておく：

      Gems are code you can include in Ruby projects.

      A :file:`Gemfile` is a list of gems used by your site.

      Bundler is a gem that installs all gems in your :file:`Gemfile`.

   Bundler コマンド集をまとめておく：

   * ``bundle init``: :file:`Gemfile` を生じる
   * ``bundle config set --local path 'vendor/bundle'``
   * ``bundle add jekyll [--skip-install]``
   * ``bundle exec jekyll new --force --skip-bundle .``: :file:`.gitignore` も生
     じる
   * ``bundle install``
   * ``bundle exec jekyll serve [--livereload] [--baseurl '']``

構成ファイル :file:`_config.yaml` を編集する
----------------------------------------------------------------------

.. seealso::

   :doc:`/yaml`

公式サイトの Configuration の章を確認しながら編集する。GitHub Pages に発行するこ
とを念頭に値を設定する：

.. csv-table::
   :delim: |
   :header: Option, Description or value
   :widths: auto

   ``baseurl`` | :samp:`/{repository-name}`
   ``markdown_ext`` | ``md`` のみにする
   ``timezone`` | ``Asia/Tokyo``
   ``url`` | :samp:`https://{github-account-name}.github.io`

テーマ Minima (``thema: minima``) の参照する項目のうち、明示的に設定するべき項
目は次のとおり。

.. csv-table::
   :delim: |
   :header: Option, Description or value
   :widths: auto

   ``author`` | サイト著者名
   ``minima.date_format`` | 好みだが ``"%Y-%m-%d (%a)"``
   ``description`` | サイトの内容などを説明した文章
   ``email`` | サイト責任者のメールアドレス
   ``github_username`` | 関連 GitHub アカウントの screen name
   ``header_pages`` | ページ天井のリンク列に対応する原稿ファイルパスの配列
   ``lang`` | ``ja``
   ``repository`` | :samp:`https://github.com/{github-account-name}/{repository-name}`
   ``rss`` | 空でない任意の文字列で良いが ``RSS`` が無難
   ``show_excerpts`` | ``true``
   ``title`` | サイトの題名
   ``twitter_username`` | 関連 Twitter アカウントの screen name

配列 ``header_pages`` は Jekyll サイトの固定ページ構成を更新するときに変更する値
だ。

.. admonition:: 読者ノート

   * Minima のバージョンは 2.x であるとする。バージョン 3.x では項目が異なる。
   * SNS 関連の項目は他にもある。

Markdown 関係の設定項目を固定する。``markdown: kramdown`` であるとき、
``kramdown:`` 以下の設定項目で明示的に設定するべきもの：

.. csv-table::
   :delim: |
   :header: Option, Description or value
   :widths: auto

   ``line_width`` | テキストエディターの設定値に合わせる
   ``math_engine`` | 既定値だが ``mathjax`` を明示する
   ``remove_line_breaks_for_cjk`` | ``true``

MathJax については :doc:`/mathjax` を記した時にけっこう調べた。

オプション ``kramdown.remove_line_breaks_for_cjk`` については当ノートをまとめて
いる過程で知った。エディターで編集するときに一行あたりのカラム数を固定しているの
で有効にする。

サーバー稼動
----------------------------------------------------------------------

Jekyll サイトの内容が整ったら HTTP サーバーを稼動する。次のコマンドが良い：

.. code:: console

   $ bundle exec jekyll serve --incremental --livereload --baseurl ''

VS Code で作業する場合、何かの拡張のトーストが持つ URL そのままで Jekyll サイト
のトップページがブラウザーで開く。このコマンドを :file:`tasks.json` に入れておく
といい。

ページを追加する
======================================================================

まず ``jekyll new`` が生成したファイル名を微調整しておく：

.. code:: console

   $ find myblog -name '*.markdown' | xargs rename 's/.markdown$/.md/'

これ以降 Jekll サイト内に置く Markdown ファイルの拡張子は ``.md`` で統一する。

個人日記サイトの例
----------------------------------------------------------------------

:file:`_posts` ディレクトリーに日記エントリーを毎日一本追加していくシナリオを考
える。ここには日記以外のファイルを含めないとする。目標はこうなる：

* 日記ページの著者は同一人物で統一する
* 日記ページの区分は日記とわかるもので統一する
* 日記ページの HTML テンプレートは日記用のもので統一する
* 日記ページの front matter はせいぜい見出しだけ書けば済むようにする

やることはこうなる：

* 構成ファイル :file:`_config.yml` で著者名、区分、テンプレートの既定値を規定す
  る
* 日記用テンプレートを :file:`_layouts` ディレクトリーに置く

:file:`_config.yml` に追加する設定はこういうものだ：

.. code:: yaml

   defaults:
     - scope:
         path: _posts
         type: posts
       values:
         # YAML のノード参照を使って外側に定義した author を参照する手もある
         author: "AUTHOR-NAME"
         categories:
           - diary
         layout: diary

この記述により、次の効果が得られる。日記 Markdown ファイルを :file:`_posts` に追
加すると、それらの front matter で次が指定されたとみなされる（明示的に指定しない
限り）：

.. code:: yaml

   ---
   author: "AUTHOR-NAME"
   categories:
     - diary
   layout: diary
   ---

ディレクトリー :file:`_layouts` にテンプレートファイル :file:`diary.html` を適当
な内容で追加しておく。Liquid 技術の腕の発揮しどころだ。

変数と値の一覧を確認するためのページを用意する
----------------------------------------------------------------------

例えば次のような HTML をサイトに組み込んでおく。開発モードでだけ出現するように仕
掛ける：

.. code:: html

   <h2>Configuration</h2>
   <h3>Global Configuration</h3>
   <ul>
     <li>source = {{ site.source }}</li>
     <li>destination = {{ site.destination }}</li>
     <li>safe = {{ site.safe }}</li>
     <li>disable_disk_cache = {{ site.disable_disk_cache }}</li>
     <li>ignore_theme_config = {{ site.ignore_theme_config }}</li>
     <li>exclude = [{{ site.exclude | join: ", " }}]</li>
     <li>include = [{{ site.include | join: ", " }}]</li>
     <li>keep_files = [{{ site.keep_files | join: ", " }}]</li>
     <li>timezone = {{ site.timezone }}</li>
     <li>encoding = {{ site.encoding }}</li>
   </ul>

   <h3>Build Command Options</h3>
   ...

画像一覧ページを作成する
----------------------------------------------------------------------

.. todo::

   上述の教材のいずれかのギャラリー作成記事を簡略化してみる。

Markdown に関するノート
======================================================================

次の URL のテキストを見るといい：
<https://daringfireball.net/projects/markdown/syntax.text>

Markdown でどう実現するのかわからなくなっても、次の原理に立ち返れば安心だ：

   For any markup that is not covered by Markdown’s syntax, you simply use HTML
   itself. (Daring Fireball, Markdown: Syntax)

Liquid に関するノート
======================================================================

Liquid は Jekyll が採用しているテンプレート言語だ。Sphinx で言う Jinja2 に相当す
る。

   Liquid uses a combination of objects, tags, and filters inside template files
   to display dynamic content. (*Liquid*, Introduction)

この節では覚えておくべき Liquid 構成要素を記す。

.. admonition:: 読者ノート

   Liquid 標準要素と Jekyll 固有の要素を区別しておくといい？

オブジェクト
----------------------------------------------------------------------

   :dfn:`Objects` contain the content that Liquid displays on a page. Objects
   and variables are displayed when enclosed in double curly braces: ``{{`` and
   ``}}``. (*Liquid*, Introduction)

テンプレート内に ``{{ varname }}`` と書いておくと、Liquid はその箇所を変数
``varname`` の値で置き換える。Jekyll サイトの場合、次のようなものがよく用いられ
る：

* ``{{ page.tags }}``, ``{{ page.title }}``, ``{{ page.url }}``, etc.
* ``{{ post.author }}``, ``{{ post.date }}``, ``{{ post.excerpt }}``, ``{{
  post.title }}``, ``{{ post.url }}``, etc.
* ``{{ site.baseurl }}``, ``{{ site.posts }}``, ``{{ site.theme }}``, ``{{
  site.title }}``, etc.

フィルター
----------------------------------------------------------------------

フィルターは Liquid オブジェクトや変数の出力を変更するものだ。``{{`` ... ``}}``
と変数代入の中で使われ、縦棒文字 ``|`` で区切られた形を取る。UNIX のパイプのよう
に複数のフィルターを連結することがある。

.. csv-table::
   :delim: @
   :header: Filter, Description, Example
   :widths: auto

   ``date`` @ 日付の書式を ``strftime`` 様式で指定して変換 @ ``{{ page.date | date: "%Y-%m-%d" }}``
   ``date_to_xmlschema`` @ 日付を ISO 8601 様式に変換 @ ``{{ post.date | date_to_xmlschema }}``
   ``default`` @ 値が空や偽の変数ならば指定値を出力 @ ``{{ page.lang | default: site.lang | default: "en" }}``
   ``escape`` @ 文字列を URL などで使えるようにエスケープ処理 @ ``{{ page.title | escape }}``
   ``join`` @ 配列要素を指定区切りパターンで連結して文字列にする @ 上記参照
   ``prepend`` @ 文字列の先頭に指定文字列を追加 @ ``{{ post.url | prepend: site.baseurl }}``
   ``relative_url`` @ 文字列の先頭に ``site.baseurl`` を追加 @ ``{{ "/assets/images/screenshot.png" | relative_url }}``

高度なフィルターとしては次のようなものがある。ページまたはポストのコレクションを
捌くのに有用だろう：

* ``where``, ``where_exp``
* ``group_by``, ``group_by_exp``
* ``sort``

タグ
----------------------------------------------------------------------

Liquid の文脈におけるタグとは：

   :dfn:`Tags` create the logic and control flow for templates. The curly brace
   percentage delimiters ``{%`` and ``%}`` and the text that they surround do
   not produce any visible output when the template is rendered. This lets you
   assign variables and create conditions or loops without showing any of the
   Liquid logic on the page. (*Liquid*, Introduction)

タグを分類して理解する：

制御
   条件分岐構文は次のようにまとめられる。

   * :samp:`\\{% if {condition} %\\}` ... ``{% endif %}``

     * 裏バージョンの ``{% unless %}`` もある
     * ``{% else %}`` や :samp:`\\{% elsif {condition} %\\}` もある
   * ``{% case %}`` ... ``{% endcase %}`` は switch 文に相当する

     * 選択肢は :samp:`{\% when {value} %\}` らしい
     * ``{% else %}`` 節を default とする
ループ
   ループ中でしか使えない変数や引数も存在する。割愛。

   * :samp:`\\{% for {i} in {collection} %\\}` ... ``{% endfor %}`` ループの中では
     次のタグが有効だ。働きは Python のと同じだろう：

     * ``{{ break }}``
     * ``{{ continue }}``
     * ``{{ else }}``
   * :samp:`\\{% tablerow {i} in {collection} %\\}` ... ``{% endtablerow %}``
テンプレート
   Liquid コードとそれ以外を区別させるタグだ。

   * ``{% comment %}`` ... ``{% endcomment %}`` 部分はコメント
   * ``{% raw %}`` ... ``{% endraw %}`` 部分は Liquid 処理が無効
   * :samp:`\\{% include "{template-name}" %\\}`

   最近では ``include`` が公式に deprecated とされている。Jekyll の採用する
   Liquid のバージョンが上がるのを待って ``render`` を用いるようにする。
変数代入
   変数代入またはそれに関する操作を指定するタグだ。主に使うのは次の二つ：

   * :samp:`\\{% assign {variable} = {value} %\\}`
   * :samp:`\\{% capture {variable} = {value} %\\}` ... ``{% endcapture %}``

   両者の差異は指定変数の有効域にある。なるべく後者を使うのが実践的か。

SCSS に関するノート
======================================================================

SCSS もわからない。

Rouge に関するノート
======================================================================

TBW

Minima に関するノート
======================================================================

* Minima

   ``minima`` is the current default theme, and ``bundle info minima`` will show
   you where minima theme's files are stored on your computer.


その他ノート整理中
======================================================================

``jekyll build`` コマンドの実行手順は次が普通だ。これで :file:`_site` に生じる成
果物が配備可能なものになる：

.. code:: console

   $ JEKYLL_ENV=production bundle exec jekyll build

----

* Permalink 調整（日記用）

  .. code:: yaml

     permalink: /:categories/:year/:month/:day/:title:output_ext

----

   Note that you should avoid using too many includes, as this will slow down
   the build time of your site.
