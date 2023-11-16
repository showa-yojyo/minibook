======================================================================
データベース利用ノート
======================================================================

各種データベースの稼動環境構築および撤去手順を記録したい。

.. contents::

TBW

Microsoft SQL Server
======================================================================

.. todo:: https://www.microsoft.com/ja-jp/sql-server

MySQL
======================================================================

.. todo:: https://www.mysql.com/

PostgreSQL
======================================================================

.. todo:: https://www.postgresql.org/

MongoDB
======================================================================

.. todo:: https://www.mongodb.com/

OrientDB
======================================================================

.. todo:: https://www.orientdb.org/

MariaDB
======================================================================

.. todo:: https://mariadb.org/

SQLite
======================================================================

:Official: `SQLite Home Page <https://www.sqlite.org/index.html>`__
:CLI: :program:`sqlite3`

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
