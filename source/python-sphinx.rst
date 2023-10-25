======================================================================
Sphinx 利用ノート
======================================================================

本稿は当読書ノートの基盤となる Python パッケージである Sphinx_ の利用に関するノー
トだ。

   Sphinx is a *documentation generator* or a tool that translates a set of
   plain text source files into various output formats, automatically producing
   cross-references, indices, etc. That is, if you have a directory containing a
   bunch of reStructuredText or Markdown documents, Sphinx can generate a series
   of HTML files, a PDF file (via LaTeX), man pages and much more.

.. contents::
   :depth: 3

インストール
======================================================================

グローバルにインストールする場合と、プロジェクトの仮想環境にインストールする場合
がある。両方説明する。更新手段は採用するパッケージマネジャーに従う。

グローバルの Python 環境はまともにあるものとする。

グローバルにインストールする
----------------------------------------------------------------------

Miniconda も使えるが、以下 :program:`pip` を利用する方法を記す。

.. code:: console

   bash$ pip install sphinx

プロジェクト個別にインストールする
----------------------------------------------------------------------

グローバルにインストールしてから実施することを勧める。プロジェクトディレクトリー
に移動して仮想環境を作成したら直ちにインストールするという想定で：

.. code:: console

   bash$ cd $PROJECT_DIR
   bash$ python -m env .venv
   bash$ pip install --upgrade pip
   bash$ pip install sphinx

インストール成功を確認する
----------------------------------------------------------------------

Sphinx のバージョンを確認する：

.. code:: console

   bash$ sphinx-build --version
   sphinx-build 7.2.6

原稿ディレクトリーを初期化する
======================================================================

将来的に生成した HTML ファイル群を GitHub に配備するので、プロジェクトディレクト
リーのルートにサブディレクトリー :file:`docs` を作成し、そこを Sphinx 用作業場と
する：

.. code:: console

   bash$ cd $PROJECT_DIR
   bash$ mkdir docs
   bash$ sphinx-quickstart
   ...

:program:`sphinx-quickstart` 成功後、生成されたファイルを確認すること。

.. admonition:: 読者ノート

   :program:`sphinx-quickstart` は引数なしで実行すると対話的操作によりファイルを
   生成する。ヘルプにあるオプションを十分に指定すれば、ファイルを一気に生成する。

次にやる作業が何になるかは場合による：

* ビルド構成を変える
* 原稿を執筆する
* テーマをいじる
* 拡張を導入する

初期設定
======================================================================

以下の説明では :program:`sphinx-quickstart` の入力は次を仮定する：

.. code:: console

   $ sphinx-quickstart --sep \
       --project 読者ノート \
       --author プレハブ小屋 \
       --release '1.0' \
       --language en \
       --ext-todo \
       --ext-mathjax \
       --ext-githubpages \
       --makefile \
       --no-batchfile

これらの内容は :file:`source/conf.py` に反映される。以降、この構成ファイルを次の
目的で手動で編集する：

* Sphinx 構成項目を調整する
* Sphinx 拡張を増減する
* Sphinx 拡張の構成項目を調整する

ビルド
======================================================================

:file:`Makefile` のあるディレクトリーに移動して：

.. code:: console

   $ make html

成果物はサブディレクトリー :file:`build/html` 以下の内容すべてだ。

GitHub Pages
======================================================================

GitHub のリポジトリーに Sphinx 用原稿を格納する場合、GitHub Actions の力で push
イベントで次のことを実現したいと考えるのが自然だ：

* 最新の原稿をビルドして HTML ファイルを生成し、
* それを GitHub Pages に公開する。

そのためのワークフロー YAML の記述方法は `Appendix: Deploying a Sphinx project
online <https://www.sphinx-doc.org/en/master/tutorial/deploying.html>`__ にあ
る。まとめておくと：

* リポジトリーの :menuselection:`Settings --> Pages` ページで各種項目を設定する：

  * Publish を有効にする
  * :guilabel:`Source` を :guilabel:`Deploy from a branch` に設定にする
  * :guilabel:`Branch` を設定する：

    * 左ドロップダウンリストを :guilabel:`gh-pages` に設定
    * 右ドロップダウンリストを :file:`Makefile` のあるほうのディレクトリーに設定

* :file:`Makefile` のあるディレクトリーに :program:`pip` 用のファイル
  :file:`requirements.txt` を置く。当読書ノートの場合は：

  .. parsed-literal::

     Sphinx >= 7.0
     ipython >= 8.0
     sphinxcontrib-mermaid

* リポジトリーにワークフローファイルを置く。例えば
  :file:`.github/workflows/sphinx.yml` とし、本文の内容にする。

  .. admonition:: 読者ノート

     ステップ Upload artifacts では大容量サイズのファイルを生成することになる。
     開発ブランチのビルドアクションでは行わず、リリースブランチだけで行うように
     書き換えるのが望ましい。

GitHub Actions がわからない場合や、ビルド時間が上限を超えるまでに文書が肥大化し
た場合は、ローカルで Sphinx ビルドをし、得られる生成ファイルを ``gh-pages`` ブラ
ンチに対して ``git push`` することになるだろう。

執筆慣行
======================================================================

.. todo::

   * [reStructuredText — Sphinx documentation](https://www.sphinx-doc.org/en/master/usage/restructuredtext/) に栞

     * Table はこの書式では使わない。
     * Images (`image` or `figure`)
     * Directives

       * 使っていないものを試す。
     * Additional body elements も試す。

       * `rubric` は使える。
     * Tables

       * `csv-table` 推奨
       * `list-table` は使いどころがあるかもしれない
   * Roles

     * `:doc:`, `:ref:` は使う。
     * `:code:` は使わない。``xxxx`` を使う。
     * `:abbr:` は使いどころが多すぎて忘れる。
     * `:command:` は多用しがち。
     * `:dfn:` も忘れる。
     * `:file:` はパス名にも使う。
     * `:guilabel:` よく使う。アンドマークに注意。
     * `:kbd:` よく使う
     * `:menuselection:` よく使う
     * `:program:` と `:command:` を間違いたくない。
     * `:regexp` は使いたい
   * Directives

     * `seealso` 使う
     * `code-block`, etc.
     * `math`
   * reST で記述するが、この文法についてはここではやらない。
   * 頻出 directives

     * `doc`
     * `ref`
     * `toctree`
   * `sphinx-build`, `make html`

ビルド構成
======================================================================

構成ファイル :file:`conf.py` で指定したい項目と目的を述べる。

.. todo::

   * `conf.py` の他に `docutils.conf` も使える。
   * `rst_epilog`, `rst_prolog` は何かいい用途がありそうだ

プロジェクト情報
----------------------------------------------------------------------

基本的には :program:`sphinx-quickstart` が生成した値を採用する。ただ一箇所、コ
ピーライト表示にビルド時の日付を反映させたいので改造する：

.. code:: python

   from datetime import date

   copyright = f'1999-{date.today().year}, {author}'

項目 ``version`` および ``release`` は手動で編集するのがいいだろう。

全般
----------------------------------------------------------------------

まず、Sphinx 拡張に手動追加するものがあるのでサブディレクトリーにパスを通す：

.. code:: python

   import sys
   import os

   # If extensions (or modules to document with autodoc) are in another directory,
   # add these directories to sys.path here. If the directory is relative to the
   # documentation root, use os.path.abspath to make it absolute, like shown here.
   sys.path.append(os.path.abspath('./_extension'))

当読者ノートにおける本稿執筆時点での拡張の編成は次のようなものだ：

.. code:: python

   extensions = [
       'disablesearchindex',
       'IPython.sphinxext.ipython_console_highlighting',
       'IPython.sphinxext.ipython_directive',
       'japanesesupport',
       'sphinx.ext.githubpages',
       'sphinx.ext.mathjax',
       'sphinx.ext.todo',
       'sphinxcontrib.mermaid',]

拡張それぞれについての構成方法は後述する。

HTML 出力
----------------------------------------------------------------------

もっとも神経を使うのはこの構成区分の設定だ。以下、当ノートの用途を意識した値を述
べる。生成コード量を少なくしたいことと、ライブラリー文書を指向していないことによ
り、ここに挙げる設定が妥当だとみなしている。

``html_theme``
   HTML5 に対応しているテーマを指定するべきだ。既定値の ``alabaster`` はそれを満
   足する。
``html_theme_options``
   この辞書の値を Alabaster の文書を見ながら決めろ。
``html_js_files``
   自作 JavaScript ファイルをリストに列挙する。
``html_sidebars``
   テーマが Alabaster なので明示的に指定する必要がある。
   ``html_theme_options['nosidebar']`` を ``True`` にした場合にはテキトーでい
   い。
``html_use_index``
   ``False`` とする。
``html_copy_source``
   ``False`` とする。reST 原稿を配備したくない。
``html_show_sourcelink``
   配備しないものに Sphinx はリンクしないようだが、明示的に ``False`` とする。
``html_show_search_summary``
   ``False`` とする。ライブラリー文書でないので。
``html_show_sphinx``
   ``False`` とする。HTML コードを減らしたいので。

拡張別構成
----------------------------------------------------------------------

``sphinx.ext.mathjax``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``mathjax_path``
   ラッパースクリプトのファイル名を設定する。例えばそれが
   :file:`source/_static/mathjax-v3.js` であるとすると：

   .. code:: python

      mathjax_path = "mathjax-v3.js"

.. seealso::

   MathJax 利用ノート

``sphinx.ext.todo``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

この拡張は重要ではないのだが、取り除く機会がないのでそのままにしてある。

``todo_include_todos``
   ``True`` に設定すると HTML に Todo 囲み記事が現れる。

.. todo::

   ノートじゅうに散乱している TODO 項目を一掃する。

``sphinxcontrib.mermaid``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``mermaid_version``, ``mermaid_init_js``
   どちらにも空文字列を代入する。その代わり構成項目 ``html_js_files`` にラッパー
   スクリプトのファイル名を追加する。例えばそれが
   :file:`source/_static_mermaid.js` であるとすると：

   .. code:: python

      html_js_files = ['mermaid.js']

.. seealso::

   :doc:`javascript-mermaid/index`

拡張
======================================================================

当ノートで利用している拡張について記す。

``sphinx.ext`` から始まる名前の拡張は Sphinx 組み込みの拡張だ。:file:`conf.py`
内のリスト ``extensions`` に含まれるだけで利用可能だ。

:program:`pip` でインストールされない拡張については、前述の構成上、サブディレク
トリー :file:`source/_extensions` に拡張用 Python ファイルを手動で追加する必要が
ある。

``sphinx.ext.githubpages``
----------------------------------------------------------------------

この拡張は GitHub の文書配置ルート位置にダミーファイルを配置する。HTML ファイル
を置く場所で Jekyll が働かないようにする意味がある。

   This extension creates :file:`.nojekyll` file on generated HTML directory to
   publish the document on GitHub Pages.

``sphinx.ext.mathjax``
----------------------------------------------------------------------

   This extension puts math as-is into the HTML files. The JavaScript package
   MathJax is then loaded and transforms the LaTeX markup to readable math live
   in the browser.

Sphinx 原稿内の ``math`` directives/roles を変換後 HTML ファイルで数式を描画させ
るためにこの拡張を導入している。

``sphinx.ext.todo``
----------------------------------------------------------------------

Sphinx 原稿内に ``todo`` および ``todolist`` 囲み記事を書けるようにする拡張だ。
これがなくても問題ない。

``IPython.sphinxext.ipython_*``
----------------------------------------------------------------------

原稿に ``ipython`` directive を記述すると、HTML 変換時によく描画してくれる。

.. ipython::

   In [136]: x = 2

   In [137]: x**3
   Out[137]: 8

拡張モジュールはビルド時の Python 環境にインストールされている必要がある。先述の
:file:`requirements.txt` に関する記述を参照。

.. seealso::

   `IPython Sphinx Directive
   <https://ipython.readthedocs.io/en/stable/sphinxext.html>`__

``sphinxcontrib.mermaid``
----------------------------------------------------------------------

原稿に ``mermaid`` directive を記述すると HTML 変換時に Mermaid が図式を描画す
る。

.. mermaid::
   :caption: Mermaid 動作確認

   stateDiagram-v2
     [*] --> Still
     Still --> [*]
     Still --> Moving
     Moving --> Still
     Moving --> Crash
     Crash --> [*]

拡張モジュールはビルド時の Python 環境にインストールされている必要がある。先述の
:file:`requirements.txt` に関する記述を参照。

.. seealso::

   `sphinxcontrib-mermaid · PyPI
   <https://pypi.org/project/sphinxcontrib-mermaid/>`__

``japanesesupport``
----------------------------------------------------------------------

現象を正確に記述するのは難しいのだが、本稿 reST ファイルには通常日本語の文をタイ
プする。私の場合は 70 文字打って改行する。日本語の文字と日本語の文字の間に改行文
字が入ることが普通にある。これが最終的に HTML ファイルになり、ブラウザーで読む。
そこでは改行文字だったものが空白文字に置き換わったかのように描画される。

それの回避策として、<http://sphinx-users.jp/reverse-dict/html/japanese.html> で
入手した :file:`japanesesupport.py` を :file:`source/_extensions` に追加
し、Sphinx 拡張としてロードしている。

.. todo::

   この拡張は：

   `sphinxcontrib-trimblank · PyPI <https://pypi.org/project/sphinxcontrib-trimblank/>`__

``disablesearchindex``
----------------------------------------------------------------------

当ノートでは Sphinx の枠組で搭載されている検索機能を完全に排除する。そのための自
作拡張だ。

.. seealso::

   `disable search index generation
   <https://groups.google.com/g/sphinx-users/c/vzSAi8SM3aY>`__

テーマ
======================================================================

* [Alabaster](https://alabaster.readthedocs.io/en/latest/) を採用
* テーマによってカスタマイズ方法をよく確認する

その他のカスタマイズ
======================================================================

* 自作箇所がわずかにあったはず

関連ノート
======================================================================

.. todo::

   本番用では書く。

   * Jinja2 利用ノート
   * Pygments 利用ノート
   * pip 利用ノート

.. _Sphinx: https://www.sphinx-doc.org/en/master/
