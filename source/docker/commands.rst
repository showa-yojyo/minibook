======================================================================
呪文集
======================================================================

.. include:: /_include/kbd.txt
.. include:: ./docker-inc.txt

プログラム :command:`docker` のコマンドラインを素早く組み立てるようになるのが目
標だ。

.. contents:: 本章見出し
   :depth: 2
   :local:

共通オプション
======================================================================

ここでいう共通オプションとは、次のコマンド呼び出しの形式における
``[common-options]`` の部分に来るコマンドラインオプションのこととする。

.. sourcecode:: console
   :caption: Synopsys

   $ docker [common-options] <command> [command-options] <args>

.. option:: -v, --version=true|false

   :command:`docker` 自身のバージョン情報を出力して終了する。既定値は ``false``.

.. option:: --help

   引数なしで実行すると Docker コマンド一覧と共通オプションを出力して終了する。
   :samp:`docker {command} --help` の形式で実行すると Docker コマンドの使用方法
   を出力して終了する。

.. option:: --config=<path>

   Docker クライアント構成ファイル（の格納されているディレクトリー）パスを指定す
   る。既定値は :file:`~/.docker`.

.. option:: -D, --debug=true|false

   デバッグモードを有効にする。既定値は ``false``,

.. option:: -l, --log-level="debug|info|warn|error|fatal"

   ログ水準を指定する。既定値は ``info`` だ。

常用コマンド
======================================================================

私が利用したいコマンドライン群、「呪文表」を示す。チートシートとして参照に耐え得
るものを用意したい。また、ヘルプ出力による用途別分類を利用させてもらう。まずは常
用に区分されているコマンド集の名称を示す：

.. csv-table:: Docker CLI Common Commands
   :delim: @
   :header-rows: 1
   :widths: auto

   Command @ Description
   ``run``     @ Create and run a new container from an image
   ``exec``    @ Alias for ``container exec``
   ``ps``      @ Alias for ``container ls``
   ``build``   @ Build an image from a Dockerfile
   ``pull``    @ Alias for ``image pull``
   ``push``    @ Alias for ``image push``
   ``images``  @ Alias for ``image ls``
   ``login``   @ Log in to a registry
   ``logout``  @ Log out from a registry
   ``search``  @ Search Docker Hub for images
   ``version`` @ Show the Docker version information
   ``info``    @ Alias for ``system info``

呪文表 ``run``
----------------------------------------------------------------------

コマンド ``run`` 実行時の基本動作は次のようなものだ：

#. Docker クライアントは指定のイメージをどうにかして見つけ、
#. そのコンテナー内部で指定コマンドを実行する。
#. その指定コマンドが終了するとコンテナーは終了する。

よく用いるオプションをまとめて記しておく。

.. option:: -d, --detach

   バックグラウンドプロセスとしてコンテナーを稼働する（端末ウィンドウをブロック
   しない）。コンテナーは自身の実行に使用したルートプロセスが終了したときに終了
   する。ただし、``--rm`` オプションとともに ``-d`` を使用すると、コンテナーは自
   身かデーモンのどちらかが早い方の終了時に削除される。

.. option:: -i, --interactive

   コンテナーの標準入力を開いておき、それを通してコンテナーに入力を送ることがで
   きるようにする。

   コンテナーの入出力ストリームを擬似端末に束縛して、コンテナーの対話型端末セッ
   ションを作成するために ``--tty`` とともに使用されがちだ。次のオプション説明と
   合わせて理解する。

.. option:: -t, --tty

   コンテナーに擬似 TTY を取り付け、端末をコンテナーの入出力ストリームに接続す
   る。この割り当ては TTY デバイスが搭載する入出力機能とやりとりできることを意味
   する。

   本文ではパスワード入力を要求するコンテナーで ``--tty`` の意義を示している。

.. option:: --rm

   コンテナー終了時にそのファイルシステムを削除させる。短期間のフォアグランドプ
   ロセス実行時に指定しがちなオプションだ。

.. option:: -name <container_name>, --name <container_name>

   コンテナー識別名を指定する。他のコマンド中にハッシュ値ではなくこの名前で参照
   することが可能になるという利点がある。

.. option:: -w <directory>, --workdir <directory>

   指定されたディレクトリー内でコマンドを実行する。パスが存在しない場合はコンテ
   ナー内に自動的に作成される。

.. option:: -p <port1>:<port2>, --publish <port1>:<port2>,

   コンテナーのポート ``<port2>`` をホストのポート ``<port1>`` に束縛する。

.. option:: -P, --publish-all

   すべての公開ポートをホストに公開する。Docker は各公開ポートをホスト上のランダ
   ムなポートに束縛する。

   |Dockerfile| の ``EXPOSE`` 指定や ``docker run`` の ``--expose`` オプションは
   公開フラグが明示的に付けられたポート番号しか公開しない。

.. option:: -v <dir1>:<dir2>, --volume <dir1>:<dir2>

   ホスト側ディレクトリー ``<dir1>`` をコンテナーの ``<dir2>`` にマウントする。

   バインドマウントされたボリュームのホストディレクトリーが存在しない場合、
   Docker が実行者に代わって ``<dir1>`` をホスト上に作成する。

.. option:: --mount <mount>

   ボリュームやホストディレクトリーをコンテナー内にマウントする。

   このオプションは ``--volume`` が対応しているオプションのほとんどを対応するも
   のの、構文は異なる。

   本文で言われているように、``--volume`` よりも ``--mount`` を優先して使え。

.. option:: --network <network_name>

   コンテナーをネットワークに接続する。ネットワークは後述する関連コマンドでなん
   とかする。

.. option:: -e <varname[=value]>, --env <varname[=value]>

   稼働するコンテナー内部に対して環境変数を設定したり、コンテナーのイメージの
   |Dockerfile| で定義された変数を上書きしたりする。

.. option:: --env-file <file>

   環境変数をファイルからロードする。ファイルの書式は変数名と値の代入文が並ぶと
   いうものだ。

----

ここから呪文例。

:samp:`docker run --name {<container_name>} {<image_name>}`
   イメージからコンテナーを生成、稼働する。コンテナーに独自の名前を与える。
:samp:`docker run -p {<host_port>}:{<container_port>} {<image_name>}`
   実行元マシンに公開するポートを指定してコンテナーを稼働する。
:samp:`docker run -d {<image_name>}`
   コンテナーをバックグランドで稼働する。

``docker run alpine ls -l``
   コマンド ``ls -l`` を指定したので、Docker はディレクトリー一覧出力をコンテ
   ナー内で実行する。出力が終了するとコンテナーはシャットダウンする。

.. ``docker run -it alpine /bin/sh``
.. ``docker run -it alpine /bin/ash``
.. ``docker run -ti ubuntu bash``
.. ``docker run hello:v0.1``
.. ``docker run -dt ubuntu sleep infinity``
..    This command will create a new container based on the ubuntu:latest image and
..    will run the sleep command to keep the container running in the background.
..
.. ``docker run --name web1 -d -p 8080:80 nginx``
..
.. ``docker container run --interactive --tty --rm ubuntu bash``
..
.. ``docker container run \
.. --detach \
.. --name mydb \
.. -e MYSQL_ROOT_PASSWORD=my-secret-pw \
.. mysql:latest``

.. ``docker container run \
.. --detach \
.. --publish 80:80 \
.. --name linux_tweet_app \
.. $DOCKERID/linux_tweet_app:1.0``
..
.. ``docker container run \
.. --detach \
.. --publish 80:80 \
.. --name linux_tweet_app \
.. --mount type=bind,source="$(pwd)",target=/usr/share/nginx/html \
.. $DOCKERID/linux_tweet_app:1.0``
..
.. ``docker container run \
.. --detach \
.. --publish 8080:80 \
.. --name old_linux_tweet_app \
.. $DOCKERID/linux_tweet_app:1.0``
.. docker container run -it --rm linkextractor:step1 http://example.com/
..
.. docker container run -it --rm linkextractor:step1 https://training.play-with-docker.com/
.. docker run -d -p 8080:8080 spring-helloworld
.. docker run -d -p 8080:80 nginx
.. docker run -p 80 nginx
.. docker run -d -p HOST_PORT:CONTAINER_PORT postgres

``docker run -d -e POSTGRES_PASSWORD=secret -p 5434:5432 --network mynetwork postgres``
   Postgres コンテナーがバックグラウンドで起動し、ホストポート 5434 に写され、
   ネットワーク ``mynetwork`` に接続する。

``docker run -P nginx``
   イメージによって設定されたすべてのポートを公開する。
``docker run -e foo=bar postgres env``
   オプション ``-e`` はコンテナー内側での環境変数を指定する。
``docker run --env-file .env postgres env``
   環境変数の集合をファイル :file:`.env` で指定する。
``docker run --memory="512m" --cpus="0.5" postgres``
   コンテナーのメモリー使用量と CPU 枠を制限する。
``docker run -d -p 80:80 -v log-data:/logs docker/welcome-to-docker``
   コンテナが実行されると、:file:`/logs` ディレクトリーに書き込まれるすべての
   ファイルが、コンテナー外のこのボリューム ``log-data`` に保存される。コンテ
   ナーを削除し、同じボリュームを使用して新しいコンテナーを稼働してもファイルは
   そのまま残る。

``docker run --name=db -e POSTGRES_PASSWORD=secret -d -v postgres_data:/var/lib/postgresql/data postgres``
   TODO: ボリューム用
``docker run --mount type=bind,source=/HOST/PATH,target=/CONTAINER/PATH,readonly nginx``
   TODO: マウント用
``docker run -v HOST-DIRECTORY:/CONTAINER-DIRECTORY:rw nginx``
   TODO: 権限用

``docker run -d --name redis --network sample-app --network-alias redis redis``
   Redis コンテナーを起動し、先に作成したネットワーク ``sample-app`` に取り付け
   てネットワーク別名を作成する。DNS lookup に便利だ。
``docker run -v $PWD:/test -w /test golangci/golangci-lint golangci-lint run``
   TODO: ``-w``
``docker build --target=server --platform=linux/arm/v7 .``
   TODO: ``--platform``

.. docker run -it --mount type=bind,src="$(pwd)",target=/src ubuntu bash

呪文表 ``exec``
----------------------------------------------------------------------

コマンド ``container exec`` の別名。:ref:`docker-container-exec` を参照しろ。

呪文表 ``ps``
----------------------------------------------------------------------

コマンド ``container ls`` の別名。:ref:`docker-container-ls` を参照しろ。

呪文表 ``build``
----------------------------------------------------------------------

``docker build .``
   イメージを構築する。Docker にファイル |Dockerfile| を :file:`.` から参照させ
   る。
:samp:`docker build -t {<image_name>}`
   |Dockerfile| からイメージを構築する。イメージ名は例えば ``hello:v0.1`` のよう
   な文字列で指定可。
:samp:`docker build -t {<image_name>} . -no-cache`
   キャッシュなしで |Dockerfile| からイメージを構築する。
``docker build -t spring-helloworld .``
   TBW
``docker build -t linkextractor:step1 .``
   TBW
``docker build --tag $DOCKERID/linux_tweet_app:1.0 .``
   TBW

``docker build -t node-docker-image-test --progress=plain --no-cache --target test .``
   ``test`` ステージを対象として新しいイメージをビルドし、テスト結果を表示する。

   * ビルド出力を表示するのは ``--progress=plain`` による。
   * テストがつねに実行されるのは ``--no-cache`` による。
   * ``test`` ステージが対象であるのは ``--target test`` による。
``docker build --provenance=true --sbom=true --tag ORG/scout-demo-service:v1 --push .``
   TODO: scout 用
``docker build --tag=buildme-client --target=client .``
   TBW
``docker build --target=client --progress=plain . 2> log1.txt``
   ``--progress=plain`` フラグを付け、出力をログファイルにリダイレクトする。
``docker build --build-arg="GO_VERSION=1.19" .``
   TBW
``docker build --output=. --target=server .``
   対象 ``server`` のファイルをホストファイルシステム上の現在の作業ディレクト
   リーにエクスポートする。

呪文表 ``pull``
----------------------------------------------------------------------

コマンド ``image pull`` の別名。:ref:`docker-image-pull` を参照しろ。

呪文表 ``push``
----------------------------------------------------------------------

コマンド ``image push`` の別名。:ref:`docker-image-push` を参照しろ。

呪文表 ``images``
----------------------------------------------------------------------

コマンド ``image ls`` の別名。:ref:`docker-image-ls` を参照しろ。

呪文表 ``login``
----------------------------------------------------------------------

レジストリー、普通は |DockerHub| にログインする。

:samp:`docker login -u {<username>}`
   使用者を指定して Docker にログインする。Password のプロンプトが表示される。こ
   れに適切な入力を与えればレジストリーとやり取り可能になる。
:samp:`docker login -u {<username>} -p {PASSWORD}`
   使用者とパスワードを両方指定してログインする。

.. todo::

   二因子認証の場合、ログアウトしてまたログインするときの対処法を記す。

呪文表 ``logout``
----------------------------------------------------------------------

レジストリーからログアウトする。

``docker logout``
   <https://registry-1.docker.io/> にある Docker の公開レジストリーからログアウ
   トする。
``docker logout localhost:8080``
   ローカルホストのレジストリーからログアウトする。

呪文表 ``search``
----------------------------------------------------------------------

:samp:`docker search {<image_name>}`
   イメージを |DockerHub| から検索する。
``docker search --filter=is-official=true Python``
   Python に関係するであろう、公式イメージを検索する。
:samp:`docker search --filter=stars=3 sql`
   SQL に関係するであろうイメージで、ランク 3 かそれ以上のものを検索する。

呪文表 ``version``
----------------------------------------------------------------------

``docker version``
   Docker バージョン情報を出力する。
``docker version --format '{{.Server.Version}}'``
   サーバーバージョンを出力する。

呪文表 ``info``
----------------------------------------------------------------------

コマンド ``system info`` の別名。:ref:`docker-system-info` を参照しろ。

運営コマンド
======================================================================

.. sourcecode:: text
   :caption: Docker CLI Management Commands

   builder     Manage builds
   buildx*     Docker Buildx
   compose*    Docker Compose
   container   Manage containers
   context     Manage contexts
   image       Manage images
   manifest    Manage Docker image manifests and manifest lists
   network     Manage networks
   plugin      Manage plugins
   scout*      Docker Scout
   system      Manage Docker
   trust       Manage trust on Docker images
   volume      Manage volumes

呪文表 ``builder``
----------------------------------------------------------------------

``docker builder prune -af``
   ビルドキャッシュを消去する。リビルドの直前に実行する。

呪文表 ``compose``
----------------------------------------------------------------------

マルチコンテナーアプリケーションの定義および実行に対するコマンドを構成する。

``docker compose down``
   コンテナーを完全に終了する。
``docker compose down --volumes``
   コンテナーを完全に終了する。ボリュームをも削除する。
``docker compose up``
   プロジェクトディレクトリーから実行することでアプリケーションを起動する。
``docker compose up -d``
   サービスをバックグラウンドで実行したい場合はオプション ``-d`` を加える。
``docker compose up -d --build``
   TBW
``docker compose watch``, ``docker compose up --watch``
   アプリケーションをビルドして稼働し、ファイル監視モードを開始する。
``docker compose ps``
   現在稼働中のコンテナー一覧を出力する。
``docker compose rm``
   停止サービスコンテナーを削除する。
``docker compose run server npm run test``
   コンテナー内のファイル :file:`package.json` からテストスクリプトを実行する。

.. docker-compose exec redis redis-cli monitor

呪文表 ``container``
----------------------------------------------------------------------

コンテナーを運営するためのコマンド。

.. sourcecode:: text
   :caption: Subcommands of ``docker container``

   attach      Attach local standard input, output, and error streams to a running container
   commit      Create a new image from a container's changes
   cp          Copy files/folders between a container and the local filesystem
   create      Create a new container
   diff        Inspect changes to files or directories on a container's filesystem
   exec        Execute a command in a running container
   export      Export a container's filesystem as a tar archive
   inspect     Display detailed information on one or more containers
   kill        Kill one or more running containers
   logs        Fetch the logs of a container
   ls          List containers
   pause       Pause all processes within one or more containers
   port        List port mappings or a specific mapping for the container
   prune       Remove all stopped containers
   rename      Rename a container
   restart     Restart one or more containers
   rm          Remove one or more containers
   run         Create and run a new container from an image
   start       Start one or more stopped containers
   stats       Display a live stream of container(s) resource usage statistics
   stop        Stop one or more running containers
   top         Display the running processes of a container
   unpause     Unpause all processes within one or more containers
   update      Update configuration of one or more containers
   wait        Block until one or more containers stop, then print their exit codes

呪文表 ``container commit``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``commit`` を使用可。

:samp:`docker commit {CONTAINER_ID}`
   差分をコミットする
``docker commit -m "Add node" base-container node-base``
   TBW
``docker commit -c "CMD node app.js" -m "Add app" app-container sample-app``
   このコマンドは ``sample-app`` という新しいイメージを作成するだけでなく、コン
   テナー起動時の既定コマンドを ``node app.js`` に設定する。

呪文表 ``container create``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``create`` を使用可。

TBW

呪文表 ``container diff``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``diff`` を使用可。

:samp:`docker diff {<container ID>}`
   docker run -it からのファイルすべて

.. _docker-container-exec:

呪文表 ``container exec``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``exec`` を使用可。

:samp:`docker exec -it {<container_name>} {command}`
   稼働中のコンテナーの内側でコマンドを実行する。
:samp:`docker exec {<container_id>} ls`
   TBD
``docker exec -it mydb sh``
   MySQL コンテナーである ``mydb`` 内に対話型シェル :program:`sh` が表示される。
``docker exec -it mydb mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version``
   TBW
``docker exec my-mysql mysql -u root -pmy-secret-pw -e "SELECT * FROM mydb.myothertable;"``
   TBW

呪文表 ``container kill``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``docker kill yourcontainerid1 yourcontainerid2``
   TBW

呪文表 ``container logs``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``logs`` を使用可。

:samp:`docker logs -f {<container_name>}`
   コンテナーのログを取得、追跡する。
``docker logs mydb``
   TBW
``docker logs linkextractor``
   TBW

.. _docker-container-ls:

呪文表 ``container ls``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``ps`` を使用可。

``docker ps``
   現在稼働中のコンテナーすべてを一覧する。稼働でないコンテナーは返されない。
``docker ps --all``
   稼働中でも停止中でも、コンテナーすべてを一覧する。

呪文表 ``container rm``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``rm`` を使用可。

:samp:`docker rm -f {<container>}``
   コンテナーを稼働中であっても削除する。
``docker rm --force linux_tweet_app``
   TBW
``docker rm -f linkextractor``
   TBW

呪文表 ``container run``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

コマンド ``run`` の別名。

呪文表 ``container start``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``start`` を使用可。

:samp:`docker start {<container>}`
   既存のコンテナーを開始する。

呪文表 ``container stats``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``stats`` を使用可。

``docker stats``
   資源使用統計を標準出力に出力する。|Ctrl+C| で終了。

呪文表 ``container stop``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``stop`` を使用可。

:samp:`docker stop {<container>}`
   既存のコンテナーを停止する。

呪文表 ``container top``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``docker container top mydb``
   TBW


呪文表 ``image``
----------------------------------------------------------------------

コマンド ``image`` はサブコマンドで構成されている：

.. sourcecode:: text
   :caption: Subcommands of ``docker image``

   build       Build an image from a Dockerfile
   history     Show the history of an image
   import      Import the contents from a tarball to create a filesystem image
   inspect     Display detailed information on one or more images
   load        Load an image from a tar archive or STDIN
   ls          List images
   prune       Remove unused images
   pull        Download an image from a registry
   push        Upload an image to a registry
   rm          Remove one or more images
   save        Save one or more images to a tar archive (streamed to STDOUT by default)
   tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

呪文表 ``image build``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

コマンド ``build`` の別名。そちらで述べる。

呪文表 ``image history``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker image history {<image_name>}`
   イメージのレイヤー一覧を出力する。
``docker image history --no-trunc getting-started``
   オプション ``--no-trunc`` で完全な出力を得る。
``docker image history mobywhale/concepts-build-image-demo``
   TBW

呪文表 ``image inspect``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker image inspect {<image_name>}`
   JSON
:samp:`docker image inspect --format "{{ json .RootFS.Layers }}" <{image}>`
   層の一覧を得る

.. _docker-image-ls:

呪文表 ``image ls``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``images`` を使用可。打鍵数が少ない方を選べ。

``docker images``
   システムにあるイメージすべての一覧を出力する。

呪文表 ``image network``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``docker network create mynetwork``
   カスタムネットワークを新規作成する。
``docker network inspect``
   コンテナーがネットワークに接続されているかどうかを確認できる。
``docker network ls``
   ネットワークすべてを一覧する。

呪文表 ``image prune``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``docker image prune``
   未使用イメージすべてを削除する。

.. _docker-image-pull:

呪文表 ``image pull``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker image pull {image_name}`
   |DockerHub| から指定イメージを取得し、システムに保存する。

.. _docker-image-push:

呪文表 ``image push``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker push {<username>}/{<image_name>}`
   イメージを |DockerHub| に押し付ける。
``docker push my-username/my-image``
   TBW

呪文表 ``image rm``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``rmi`` が打鍵量が最も少ない。

:samp:`docker rmi {<image_name>}`
   イメージを削除する。

呪文表 ``image tag``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``tag`` を使用可。

:samp:`docker tag {<image_id>} {<image_name>}`
   イメージにラベルを付けてバージョン管理することができる。
``docker tag my-username/my-image another-username/another-image:v1``
   イメージに別のタグを追加できる。

呪文表 ``network``
----------------------------------------------------------------------

``docker network ls``
   現在の Docker ホスト上の既存のコンテナーネットワークを表示する。
``docker network inspect bridge``
   ``bridge`` と呼ばれるネットワークの詳細を表示する。

呪文表 ``scout``
----------------------------------------------------------------------

これは高級なコマンドなので後回しとする。

``docker scout repo enable ORG/scout-demo-service``
   リポジトリー上で Docker Scout を有効にする。
``docker scout cves --only-cve-id CVE-2022-24999``
   イメージの脆弱性を表示する。CVE-2022-24999 という CVE を確認する。
``docker scout cves --only-cve-id CVE-2022-24999 --vex-location .``
   ``--vex-location`` フラグを使うと VEX 文書を含むディレクトリーを指定できる。

.. docker scout attestation add \
..   --file in-toto.vex.json \
..   --predicate-type https://openvex.dev/ns/v0.2.0 \
..   ORG/scout-demo-service:v1

.. docker scout cves \
..   --only-cve-id CVE-2022-24999 \
..   registry://ORG/scout-demo-service:v1

呪文表 ``system``
----------------------------------------------------------------------

.. sourcecode:: text
   :caption: Subcommands of ``docker system``

   df          Show docker disk usage
   events      Get real time events from the server
   info        Display system-wide information
   prune       Remove unused data

.. _docker-system-info:

呪文表 ``system info``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``info`` を使用可。

``docker info``
   システム全体の情報を表示する。
``docker info --format '{{json .}}'``
   それを JSON 書式で出力する。

呪文表 ``volume``
----------------------------------------------------------------------

``docker volume create log-data``
   ``log-data`` という名前のボリュームを作成する。
``docker volume inspect todo-db``
   ボリュームを使用しているとき、データをどこに保存しているのかを知る。
``docker volume ls``
   ボリュームすべてを一覧する。
:samp:`docker volume rm {<volume-name-or-id>}`
   ボリュームを削除する。ボリュームがどのコンテナーにも付属していない場合にのみ
   機能する。ボリュームを削除する前にそれをコンテナーから取り外す必要がある。
``docker volume prune``
   未使用の（どのコンテナーにも付属していない）ボリュームすべてを削除する。

Swarm コマンド
======================================================================

.. sourcecode:: text
   :caption: Docker CLI Management Commands

   config      Manage Swarm configs
   node        Manage Swarm nodes
   secret      Manage Swarm secrets
   service     Manage Swarm services
   stack       Manage Swarm stacks
   swarm       Manage Swarm

呪文表 ``node``
----------------------------------------------------------------------

``docker node ls``
   TBW

呪文表 ``service``
----------------------------------------------------------------------

``docker service create --name demo alpine:latest ping 8.8.8.8``
   ``alpine`` ベースのファイルシステムを使用する単純な Docker サービスを実行し、
   8.8.8.8 への :command:`ping` を分離する。
``docker service create --name myservice --network overnet --replicas 2 ubuntu sleep infinity``
   TBW
``docker service create --name sleep-app ubuntu sleep infinity``
   TBW
``docker service logs demo``
   期待されるログが得られることを確認する。
``docker service ls``
   TBW
``docker service ps myservice``
   サービスが実行中のコンテナーを作成したことを確認する。
``docker service ps voting_stack_vote``
   TBW
``docker service inspect myservice``
   TBW
``docker service rm myservice``
   サービスを解体する。
``docker service update --replicas 7 sleep-app``
   TBW

呪文表 ``stack``
----------------------------------------------------------------------

``docker stack deploy -c bb-stack.yaml demo``
   アプリケーションを Swarm に配備する。
``docker stack deploy --compose-file=docker-stack.yml voting_stack``
   同上。
``docker stack ls``
   TBW
``docker stack services voting_stack``
   TBW
``docker stack rm demo``
   TBW

呪文表 ``swarm``
----------------------------------------------------------------------

``docker swarm init``
   Docker Swarm モードを初期化する。
``docker swarm init --advertise-addr $(hostname -i)``
   TBW
``docker swarm leave --force``
   TBW

無印コマンド
======================================================================

ほとんどは別のコマンドの別名であり、おそらく打鍵効率の便宜上設けられているものと
考えられる。

.. csv-table:: Docker CLI Commands
   :delim: @
   :header-rows: 1
   :widths: auto

   Command @ Description
   ``attach``  @ Alias for ``container attach``
   ``commit``  @ Alias for ``container commit``
   ``cp``      @ Alias for ``container cp``
   ``create``  @ Alias for ``container create``
   ``diff``    @ Alias for ``container diff``
   ``events``  @ Alias for ``system events``
   ``exec``    @ Alias for ``container exec``
   ``export``  @ Alias for ``container export``
   ``history`` @ Alias for ``image history``
   ``import``  @ Alias for ``image import``
   ``inspect`` @ Return low-level information on Docker objects
   ``kill``    @ Alias for ``container kill``
   ``load``    @ Alias for ``image load``
   ``logs``    @ Alias for ``container logs``
   ``pause``   @ Alias for ``container pause``
   ``port``    @ Alias for ``container port``
   ``rename``  @ Alias for ``container rename``
   ``restart`` @ Alias for ``container restart``
   ``rm``      @ Alias for ``container rm``
   ``rmi``     @ Alias for ``image rm``
   ``save``    @ Alias for ``image save``
   ``start``   @ Alias for ``container start``
   ``stats``   @ Alias for ``container stats``
   ``stop``    @ Alias for ``container stop``
   ``tag``     @ Alias for ``image tag``
   ``top``     @ Alias for ``container top``
   ``unpause`` @ Alias for ``container unpause``
   ``update``  @ Alias for ``container update``
   ``wait``    @ Alias for ``container wait``

呪文表 ``inspect``
----------------------------------------------------------------------

:samp:`docker inspect {<container>}`
   稼働中のコンテナーを検査する。
