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
   :gem: 3.3.5
   :Bundler: 2.4.22
   :Jekyll: 4.3.2

.. contents::

文献
======================================================================

`Jekyll <https://jekyllrb.com/>`__
   Jekyll 公式サイト。

   `Using Jekyll with Bundler <https://jekyllrb.com/tutorials/using-jekyll-with-bundler/>`__
      Ruby プロジェクトの作法の初歩と思われる :program:`gem` および
      :program:`bundle` の使用方法について述べられている。Quickstart の次に読ん
      でいい。これは必読。
   `Step by Step Tutorial <https://jekyllrb.com/docs/step-by-step/01-setup/>`__
      :file:`Gemfile` の導入をなるべく後回しにしての Jekyll サイト構築チュートリ
      アルだ。Deploy の章を先頭近くに移した版を読んでみたい。
`kramdown <https://kramdown.gettalong.org/>`__
   Jekyll が使用している Markdown 解析器パッケージの公式サイト。

`Mastering Jekyll - Made Mistakes <https://mademistakes.com/mastering-jekyll/>`__
   特にリンク周りの説明が詳しい。時系列に整理する必要のない記事の配置のコツな
   ど、有用な知識が他にも述べられている。スタイリング理論はやや難しい。

ツール
======================================================================

`jekyll <https://github.com/jekyll>`__
   GitHub にある Jekyll 組織アカウント。プラグイン各種のリポジトリーを含む。

Jekyll サイト用意手順
======================================================================

公式サイトの Quickstart の記述を再現していく。最低限 :program:`ruby` は利用可能
であるとする。本ノートでは WSL の Ubuntu 環境を想定しているので、Jekyll on
Ubuntu の節に従う。

環境変数の値は XDG Base Directory Specification 愛好家としては次のようにしたい：

.. code:: bash

   export GEM_HOME="$XDG_DATA_HOME/gem"
   export GEM_SPEC_CACHE="$XDG_CACHE_HOME/gem"

   export BUNDLE_USER_CONFIG="$XDG_CONFIG_HOME/bundle"
   export BUNDLE_USER_PLUGIN="$XDG_DATA_HOME/bundle"
   export BUNDLE_USER_CACHE="$XDG_CACHE_HOME/bundle"

上記をファイル :file:`.bashrc` に書いておく。ここで、XDG 変数については適切に設
定済みであるとする。

----

``gem install bundler jekyll`` で :program:`bundler` と :program:`jekyll` をイン
ストールする。ここはチュートリアルの記述よりも精密な手順がある。例の記事を参照。
そして、:program:`gem` を使うのはこれで最後となる。作業ディレクトリーにファイル
:file:`Gemfile` があるときには必ず :program:`bundle` から Jekyll コマンドを実行
しろ。

----

その後に適当なディレクトリーに移動して Jekyll サイトを構築していく。既定のテーマ
と内容でまずブログを serve してみる：

.. code:: console

   $ bundle exec jekyll new myblog && cd $_
   $ bundle exec jekyll serve

コンソールにローカルホスト URL が出力されているので、ブラウザーでそれを開く。

生成ファイル名を微調整する：

.. code:: console

   $ find myblog -name '*.markdown' | xargs rename 's/.markdown$/.md/'

構成ファイル :file:`_config.yaml` を編集する
----------------------------------------------------------------------

.. seealso::

   :doc:`/yaml`

公式サイトの Configuration の章を確認しながら編集する。GitHub Pages に発行するこ
とを念頭に値を設定する：

.. code:: yaml

   # baseurl is only necessary when hosting your site in a sub-directory. Project
   # sites hosted on GitHub Pages are the common use-case of this variable.
   baseurl: /repository-name

   # Leave off trailing forward slashes when setting url
   url: https://showa-yojyo.github.io

   repository: https://github.com/showa-yojyo/repository-name

ビルド可能な状態にするために :file:`_config.yaml` を編集する。検証コマンドは
``jekyll doctor`` のようだ。

コマンド ``jekyll serve`` で Jekell サーバーが稼動開始する。

* コンソールに出力される URL をブラウザーで開けば Web サイトの表示を確認できる。
* コマンドラインオプション ``--livereload --baseurl=''`` を付与するのが良い。

保守手順
======================================================================

Ruby パッケージ関連
----------------------------------------------------------------------

Ruby 101 より中核概念の説明を引用しておく：

   Gems are code you can include in Ruby projects.

   A :file:`Gemfile` is a list of gems used by your site.

   Bundler is a gem that installs all gems in your :file:`Gemfile`.

:file:`Gemfile` を作成したら、Jekyll コマンドすべてを :program:`bundle` を介して
実行すること：

   If you followed our setup recommendations and installed Bundler, run ``bundle
   update jekyll`` or simply ``bundle update`` and all your gems will update to
   the latest versions.

定期的に、できれば自動でパッケージを更新したい。また、:file:`Gemfile` を手動で編
集したら ``bundle update`` を実行するのが普通。

----

* ``bundle init``: :file:`Gemfile` を生じる
* ``bundle config set --local path 'vendor/bundle'``
* ``bundle add jekyll [--skip-install]``
* ``bundle exec jekyll new --force --skip-bundle .``: :file:`.gitignore`
* ``bundle install``
* ``bundle exec jekyll serve [--livereload] [--baseurl '']``

メモ
======================================================================

Liquid 知識集のような

* objects
* tags
* filters

----

SCSS もわからない。

----

``jekyll build`` コマンドの実行手順は次が普通だ。これで :file:`_site` に生じる成
果物が配備可能なものになる：

.. code:: console

   $ JEKYLL_ENV=production bundle exec jekyll build
