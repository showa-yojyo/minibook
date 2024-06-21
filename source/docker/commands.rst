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

呪文表 ``exec``
----------------------------------------------------------------------

コマンド ``container exec`` の別名。

呪文表 ``ps``
----------------------------------------------------------------------

コマンド ``container ls`` の別名。そちらに記す。

呪文表 ``build``
----------------------------------------------------------------------

:samp:`docker build -t {<image_name>}`
   |Dockerfile| からイメージを構築する。イメージ名は例えば ``hello:v0.1`` のよう
   な文字列で指定可。
:samp:`docker build -t {<image_name>} . -no-cache`
   キャッシュなしで |Dockerfile| からイメージを構築する。

呪文表 ``pull``
----------------------------------------------------------------------

コマンド ``image pull`` の別名。そちらに記す。

呪文表 ``push``
----------------------------------------------------------------------

コマンド ``image push`` の別名。そちらに記す。

呪文表 ``images``
----------------------------------------------------------------------

コマンド ``image ls`` の別名。そちらに記す。

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
   イメージを |DockerHub| から検索する。E.g. ``docker search toilet``.

.. todo::

   絞り込み ``--filter`` を指定したコマンド例を追加する。

呪文表 ``version``
----------------------------------------------------------------------

``docker version``
   Docker バージョン情報を出力する。
``docker version --format '{{.Server.Version}}'``
   サーバーバージョンを出力する。

呪文表 ``info``
----------------------------------------------------------------------

コマンド ``system info`` の別名。そちらに記す。

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

呪文表 ``system``
----------------------------------------------------------------------

.. sourcecode:: text
   :caption: Subcommands of ``docker system``

   df          Show docker disk usage
   events      Get real time events from the server
   info        Display system-wide information
   prune       Remove unused data

呪文表 ``system info``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``info`` を使用可。

``docker info``
   システム全体の情報を表示する。
``docker info --format '{{json .}}'``
   それを JSON 書式で出力する。

呪文表 ``container``
----------------------------------------------------------------------

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

:samp:`docker container commit {CONTAINER_ID}`
   差分をコミットする

呪文表 ``container create``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``create`` を使用可。

TBW

呪文表 ``container diff``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``diff`` を使用可。

:samp:`docker diff {<container ID>}`
   docker run -it からのファイルすべて

呪文表 ``container exec``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``exec`` を使用可。

:samp:`docker exec -it {<container_name>} {command}`
   稼働中のコンテナーの内側でコマンドを実行する。
:samp:`docker exec {<container_id>} ls`
   TBD

呪文表 ``container logs``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``logs`` を使用可。

:samp:`docker logs -f {<container_name>}`
   コンテナーのログを取得、追跡する。

呪文表 ``container ls``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``ps`` を使用可。

``docker ps``
   現在稼働中のコンテナーすべてを一覧する。稼働でないコンテナーは返されない。
``docker ps --all``
   稼働中でも停止中でも、コンテナーすべてを一覧する。

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

呪文表 ``image``
----------------------------------------------------------------------

コマンド ``image`` にはサブコマンドで構成されている：

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
   TBW

呪文表 ``image inspect``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker image inspect {<image_name>}`
   JSON
:samp:`docker image inspect --format "{{ json .RootFS.Layers }}" <{image}>`
   層の一覧を得る

呪文表 ``image ls``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

別名 ``images`` を使用可。打鍵数が少ない方を選べ。

``docker image ls``
   システムにあるイメージすべての一覧を出力する。

呪文表 ``image prune``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``docker image prune``
   未使用イメージすべてを削除する。

呪文表 ``image pull``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker image pull {image_name}`
   |DockerHub| から指定イメージを取得し、システムに保存する。

呪文表 ``image push``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker push {<username>}/{<image_name>}`
   イメージを |DockerHub| に押し付ける。

呪文表 ``image tag``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:samp:`docker image tag {<image_id>} {<image_name>}`
   Git でコミットにタグを付けるようなもの？

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

呪文表 ``rmi``
----------------------------------------------------------------------

コマンド ``rmi``, ``image rm``, ``image remove`` は互いに同等。

:samp:`docker rmi {<image_name>}`
   イメージを削除する。

準備中
======================================================================

``docker network ls``
   現在のDockerホスト上の既存のコンテナ・ネットワークを表示する。
``docker network inspect bridge``
   The command below shows the details of the network called bridge.

``docker run -dt ubuntu sleep infinity``
   This command will create a new container based on the ubuntu:latest image and
   will run the sleep command to keep the container running in the background.

``docker run --name web1 -d -p 8080:80 nginx``

``docker swarm init --advertise-addr $(hostname -i)``

``docker swarm leave --force``

``docker node ls``


``docker service create --name myservice \
--network overnet \
--replicas 2 \
ubuntu sleep infinity``

``docker service create --name sleep-app ubuntu sleep infinity``

``docker service ls``

``docker service ps myservice``

``docker service inspect myservice``

``docker service rm myservice``

``docker service update --replicas 7 sleep-app``

``docker exec -it yourcontainerid /bin/bash``

``docker kill yourcontainerid1 yourcontainerid2``

``docker container run --interactive --tty --rm ubuntu bash``

``docker container run \
--detach \
--name mydb \
-e MYSQL_ROOT_PASSWORD=my-secret-pw \
mysql:latest``

``docker container logs mydb``

``docker container top mydb``

``docker exec -it mydb \
mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version``

``docker exec -it mydb sh``
   Executing the command below will give you an interactive shell (sh) inside your MySQL container.

``docker image build --tag $DOCKERID/linux_tweet_app:1.0 .``

``docker container run \
--detach \
--publish 80:80 \
--name linux_tweet_app \
$DOCKERID/linux_tweet_app:1.0``

``docker container rm --force linux_tweet_app``

``docker container run \
--detach \
--publish 80:80 \
--name linux_tweet_app \
--mount type=bind,source="$(pwd)",target=/usr/share/nginx/html \
$DOCKERID/linux_tweet_app:1.0``

``docker container run \
--detach \
--publish 8080:80 \
--name old_linux_tweet_app \
$DOCKERID/linux_tweet_app:1.0``
