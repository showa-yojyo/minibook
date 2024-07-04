======================================================================
MariaDB 利用ノート
======================================================================

:Since: 2013
:Official site: <https://mariadb.org/>
:CLI: :program:`mariadb`, :program:`mysql`
:Server Version: 11.4.2-MariaDB-ubu2404 mariadb.org binary distribution

MariaDB をとりあえず利用するまでの手順を記す。ただし、Docker を利用してよいもの
とする。

`Installing and Using MariaDB via Docker - MariaDB Knowledge Base
<https://mariadb.com/kb/en/installing-and-using-mariadb-via-docker/>`__ の記述に
従えばデータベースシェル起動まではすんなり実現するはずだ。以下に要点をまとめてお
く。

最初に Docker Hub から公式イメージを検索して、それをローカルに持ってくる：

.. sourcecode:: console
   :caption: MariaDB イメージ取得例

   $ docker search mariadb --filter=stars=5000
   $ docker pull mariadb
   $ docker images --filter reference=mariadb

コンテナーに例えば ``mariadbtest`` などの名前を付けて稼働する。このときに
MariaDB に対して必要な情報、環境変数を指定する：

.. sourcecode:: console
   :caption: MariaDB コンテナー稼働コマンド例

   $ docker run --name mariadbtest -e MYSQL_ROOT_PASSWORD=mypass -p 3306:3306 -d mariadb

コンテナー内で稼働している MariaDB サーバーに CLI でアクセスしたい。このコンテ
ナー内でアクセスする方法と、ホスト側で CLI を使ってアクセスする方法があり得る。
前者は：

.. sourcecode:: console
   :caption: 稼働中の MariaDB コンテナーでCLI を対話的に起動する例

   $ docker exec -it mariadbtest mariadb -p
   Enter password:
   Welcome to the MariaDB monitor.  Commands end with ; or \g.
   Your MariaDB connection id is 4
   Server version: 11.4.2-MariaDB-ubu2404 mariadb.org binary distribution

   Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

   Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

   MariaDB [(none)]>

後者を行うにはコンテナーの IP アドレスが必要だ。次の例ではホスト側にある
:program:`mysql` を使って接続するが、ホストにおいても :program:`mariadb` が実行
可能であればもちろんそれが使える：

.. sourcecode:: console
   :caption: ホスト側 CLI からコンテナーの MariaDB サーバーに接続する例

   $ docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mariadbtest
   172.17.0.2
   $ mysql -h 172.17.0.2 -u root -p
   Enter password:
   Welcome to the MySQL monitor.  Commands end with ; or \g.
   Your MySQL connection id is 5
   Server version: 11.4.2-MariaDB-ubu2404 mariadb.org binary distribution

   Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

   Oracle is a registered trademark of Oracle Corporation and/or its
   affiliates. Other names may be trademarks of their respective
   owners.

   Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

   mysql>

.. admonition:: 利用者ノート

   IP アドレスを適当な変数を定義してそれに代入しておくのが行儀が良いかもしれな
   い。

コンテナの一時停止は、システムのリソースを一時的に解放する必要がある場合に非常に
便利である。コンテナが現時点で重要でない場合（たとえば、バッチ処理を実行している
場合など）、コンテナを解放して他のプログラムを高速に実行できるようにすることがで
きる。

.. todo::

   * 一時停止で資源を解放
   * アンインストールはしなくていいのだが
