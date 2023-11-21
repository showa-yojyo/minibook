======================================================================
データベース利用ノート
======================================================================

各種データベースの稼動環境構築および撤去手順を記録したい。

.. contents::

.. note::

   .. code:: text

      DISTRIB_ID=Ubuntu
      DISTRIB_RELEASE=22.04
      DISTRIB_CODENAME=jammy
      DISTRIB_DESCRIPTION="Ubuntu 22.04.3 LTS"

Microsoft SQL Server
======================================================================

.. todo:: https://www.microsoft.com/ja-jp/sql-server

MySQL
======================================================================

.. todo:: https://www.mysql.com/

PostgreSQL
======================================================================

.. todo:: https://www.postgresql.org/

SQLite
======================================================================

:Since: 2000
:Official site: `SQLite Home Page <https://www.sqlite.org/index.html>`__
:CLI: :program:`sqlite3` 3.41.2

教材としては `SQLite Tutorial <https://www.sqlitetutorial.net/>`__ がいいと思わ
れる。SQL の基本を確認することも可能。

業務目的ではない場合、インストール手順は Python 環境に手を入れる手っ取り早い：

.. code:: console

   $ conda install sqlite

バージョン確認コマンドは ``sqlite3 -version``.

対話的セッションに入るにはコマンドラインから引数なしで ``sqlite3`` を実行する。
まず ``.help`` を実行してセッション終了方法を習得しろ。

CLI のドットファイルのパスは :file:`$XDG_HOME_CONFIG/sqlite3/sqliterc` にした
い。

SQLite をアンインストールする場合はこうするだろう：

* 本体をファイルシステムから削除する - ``conda uninstall sqlite``
* 構成ファイルを削除する
* データベースファイルを削除する

MongoDB
======================================================================

:Since: 2007
:Official site: `MongoDB <https://www.mongodb.com/>`__
:Service: :program:`mongod` 7.0.3
:CLI: :program:`mongosh` 2.0.2

何かのチュートリアルでインストールされた旧版 MongoDB をファイルシステムから撤去
するのに手間取る。旧版を完全に払拭しないと :program:`apt` によるバージョン 7.0
のインストールが歪む。その作業を含めたインストール手順は次の文書に記されている：
`Install MongoDB Community Edition on Ubuntu
<https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/>`__

インストール後、サービスを手動で稼動させる。Ubuntu の場合には :program:`service`
を用いる：

.. code:: console

   $ sudo service mongodb start
    * Starting database mongod                           [ OK ]
   $ sudo service mongodb status
    * Checking status of database mongod
   /etc/init.d/mongodb: 251: log_successs_msg: not found

サービスを停止するには：

.. code:: console

   $ sudo service mongodb stop
    * Stopping database mongod                           [ OK ]

サービス稼働中ならば :command:`mongosh` を実行して対話シェルを稼動可能。以下、
ローカルホストでの稼動を仮定する。

エディターなどの MongoDB Shell 設定をカスタマイズするといい。構成内容は JSON 形
式でファイル :file:`$HOME/.mongodb/mongosh/config` に保存される。現在のところ
XDG 未対応で、Git などによるバージョン管理が面倒だ。

入門として W3Schools の次のチュートリアルの前半をまず行う：
`MongoDB Tutorial <https://www.w3schools.com/mongodb/index.php>`__

中盤から出来合いのデータベースを用いる。そのため避けていた Atlas に触れざるを得
ない。アカウントを作成するときに氏名を求められるのが怖いので、ここで学習を中止す
る。

次のリポジトリーを ``git clone`` してスクリプトを実行すると、チュートリアルの続
きを少しは実施可能になる： `neelabalan/mongodb-sample-dataset: sample dataset
used in mongodb atlas cluster for local testing purpose
<https://github.com/neelabalan/mongodb-sample-dataset>`__

インデックス作成法辺りから迷子になる。

OrientDB
======================================================================

:Since: 2010:
:Official site: `Home | OrientDB Community Edition <https://www.orientdb.org/>`__
:CLI: OrientDB console 3.2.24

インストール手順は、ホームページのリンク先から圧縮ファイルをダウンロードして解凍
し、中にあるスクリプト :file:`bin/server.sh` を実行するというものだ。もう一つ、
Homebrew を用いる方法もあるようだ。

以下、ローカルホストで閉じた環境で実施する。

3.2. Create a DB の記述にしたがって URL をブラウザーで閲覧すると OrientDB Studio
画面が開く。

* ボタン :guilabel:`CREATE TABLE` を押す前に :guilabel:`Create Admin user` を ON
  にする必要がある。
* 他にも、インターネットからデータベースをインポート可能。

SQL 文 ``SELECT * FROM OUser`` を実行して成功すれば OK とする。画面上部の各種メ
ニュー項目も見ておく。

* 3.3. Create the Java Application 以降は私の Java 技術が欠落しているので実施しな
  い。
* 4.4. Run the Studio 以降をブラウザーで試す。コマンドの一部が微妙に失敗するが、
  その場合は当該クラスにレコードがあることを確認する。それでも失敗する場合はあ
  る。
* OrientDB Studio の :guilabel:`Schema Manager` の検索結果はカルーセルがあるのを
  見落とすな。
* 4.7.3 Queries をすべて試す。ブラウザーでは :guilabel:`BROWSE` と
  :guilabel:`GRAPH` タブを往復することになる。
* :guilabel:`Graph Editor` で問い合わせを実行してグラフを描画し終わったら、ゴミ
  箱ボタン :guilabel:`Clear Canvas` を押してクリアしておくこと。:guilabel:`MORE`
  も色々と試せ。
* ここでようやく 4.11. Tutorials を試す。ここまでを読み飛ばして最初に手を付けて
  はいけない。

  * 4.11.3. Setup a Distributed Database 辺りからやることが明らかでなくなる。
  * 4.11.9.1. Importing the Open Beer Database into OrientDB の元データのアドレ
    スが微妙に異なる。:file:`https://openbeerdb.com/files/openbeerdb_csv.zip` が
    良い。

    * 作成する JSON ファイル各種のパスを動作環境に合わせろ。

* 6.2. Basic Concepts をしっかりと読め。
* 8.1.3. Install as Service on Unix を読め。
* 9.1. Studio
* 10.1. Introduction

  * OrientDB の SQL には ``JOIN`` がない。

.. todo::

   Neo4j を済ませたら 4.11.9.2 に戻る。

MariaDB
======================================================================

.. todo:: https://mariadb.org/

Apache CouchDB
======================================================================

.. todo:: https://couchdb.apache.org/

Oracle Database
======================================================================

.. todo:: https://www.oracle.com/in/database/

Amazon DynamoDB
======================================================================

.. todo:: https://aws.amazon.com/dynamodb/

Neo4j
======================================================================

.. todo:: https://neo4j.com/

Firebird 5
======================================================================

`Firebird 5 Quick Start Guide <https://firebirdsql.org/file/documentation/html/en/firebirddocs/qsg5/firebird-5-quickstartguide.html>`__
