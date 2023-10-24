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
   :depth: 2

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

* `sphinx-quickstart`
* `conf.py`: 既定コードと比較して検討

reST/

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

* Configuration
  * `conf.py` の他に `docutils.conf` も使える。
  * `conf.py` で見るべきところ：
    * `extensions` 採用しているものを列挙
    * `master_doc` は `root_doc` に改名した
    * `rst_epilog`, `rst_prolog` は何かいい用途がありそうだ
    * `html_` で始まる項目を念入りに確認しろ
      * `html_theme` は HTML5 対応しているものを選べ。
      * `html_copy_source = False`
* 読者ノート専用構成
  * テーマ
  * 拡張
  * 既定機能無効化

拡張
======================================================================

  * 標準から：`sphinx.ext.githubpages`, `sphinx.ext.mathjax`, `sphinx.ext.todo`
  * `IPython.sphinext`
  * `sphinxcontrib.mermaid`
  * 入手経路を忘れた `japanesesupport`
  * これも原典不明の `disablesearchindex`

テーマ
======================================================================

* Theming
  * [Alabaster](https://alabaster.readthedocs.io/en/latest/) を採用
  * テーマによってカスタマイズ方法をよく確認する

カスタマイズ
======================================================================

* 自作箇所がわずかにあったはず

関連ノート
======================================================================

.. todo::

   本番用では書く。

   * Jinja2 利用ノート
   * Pygments 利用ノート
   * pip 利用ノート

.. _Sphinx: https://www.sphinx-doc.org/en/master/index.html

