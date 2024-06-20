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

.. sourcecode:: text
   :caption: Docker CLI Common Commands

   run         Create and run a new container from an image
   exec        Execute a command in a running container
   ps          List containers
   build       Build an image from a Dockerfile
   pull        Download an image from a registry
   push        Upload an image to a registry
   images      List images
   login       Log in to a registry
   logout      Log out from a registry
   search      Search Docker Hub for images
   version     Show the Docker version information
   info        Display system-wide information

呪文表 ``run``
----------------------------------------------------------------------

:samp:`docker run --name {<container_name>} {<image_name>}`
   イメージからコンテナーを生成、稼働する。コンテナーに独自の名前を与える。
:samp:`docker run -p {<host_port>}:{<container_port>} {<image_name>}`
   実行元マシンに公開するポートを指定してコンテナーを稼働する。
:samp:`docker run -d {<image_name>}`
   コンテナーをバックグランドで稼働する。

呪文表 ``exec``
----------------------------------------------------------------------

:samp:`docker exec -it {<container_name>} {command}`
   稼働中のコンテナーの内側でコマンドを実行する。

呪文表 ``ps``
----------------------------------------------------------------------

``docker ps``
   現在稼働中のコンテナーを一覧する。
``docker ps --all``
   稼働中でも停止中でも、コンテナーすべてを一覧する。

呪文表 ``build``
----------------------------------------------------------------------

:samp:`docker build -t {<image_name>}`
   |Dockerfile| からイメージを構築する。
:samp:`docker build -t {<image_name>} . -no-cache`
   キャッシュなしで |Dockerfile| からイメージを構築する。

呪文表 ``pull``
----------------------------------------------------------------------

:samp:`docker pull {<image_name>}`
   |DockerHub| からイメージを引っぱる。

呪文表 ``push``
----------------------------------------------------------------------

:samp:`docker push {<username>}/{<image_name>}`
   イメージを |DockerHub| に押し付ける。

呪文表 ``images``
----------------------------------------------------------------------

``docker images``
   ローカルイメージ一覧を標準出力に出力する。

呪文表 ``login``
----------------------------------------------------------------------

:samp:`docker login -u {<username>}`
   使用者を指定して Docker にログインする。Password のプロンプトが表示される。こ
   れに適切な入力を与えればレジストリーとやり取り可能になる。

   .. todo::

      二因子認証の場合、ログアウトしてまたログインするときの対処法を記す。

呪文表 ``logout``
----------------------------------------------------------------------

TBD

呪文表 ``search``
----------------------------------------------------------------------

:samp:`docker search {<image_name>}`
   イメージを |DockerHub| から検索する。E.g. ``docker search toilet``.

呪文表 ``version``
----------------------------------------------------------------------

TBD

呪文表 ``info``
----------------------------------------------------------------------

``docker info``
   システム全体の情報を表示する。

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

..
.. docker container ls
..    現在実行中のすべてのコンテナを表示する
.. docker container ls -a
..    コンテナを表示する
..    実行中でないコンテナはlsコマンドで返されないので、-aオプションを忘れずに
..
.. docker container start <container ID>
..
.. docker container exec <container ID> ls
..
.. docker container diff <container ID>
..    docker run -it からのファイルすべて
.. docker container commit CONTAINER_ID
..    差分をコミットする
.. docker container run hello-world
.. docker container run alpine ls -l
.. docker container run alpine echo "hello from alpine"
.. docker container run alpine /bin/sh
.. docker container run -it alpine /bin/sh
.. docker container run -it alpine /bin/ash
.. docker container run -ti ubuntu bash
.. docker container run hello:v0.1

..   runを呼び出すと、Dockerクライアントはイメージ（この場合はalpine）を見つけ、コンテナを作成し、そのコンテナ内でコマンドを実行する。docker container run alpineを実行したとき、コマンド（ls -l）を指定したので、Dockerはディレクトリ一覧を表示したコンテナ内でこのコマンドを実行した。ls コマンドが終了すると、コンテナはシャットダウンした。


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

:samp:`docker image build -t {hello:v0.1} .`
   TBW

:samp:`docker image history {<image_name>}`
   TBW

:samp:`docker image inspect {<image_name>}`
   JSON
:samp:`docker image inspect --format "{{ json .RootFS.Layers }}" <{image}>`
   層の一覧を得る

``docker image ls``
   システムにあるイメージすべての一覧を出力する。
``docker image prune``
   未使用イメージすべてを削除する。
:samp:`docker image pull {image_name}`
   Docker レジストリーから指定イメージを取得し、システムに保存する。
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

.. sourcecode:: text
   :caption: Docker CLI Management Commands

   attach      Attach local standard input, output, and error streams to a running container
   commit      Create a new image from a container's changes
   cp          Copy files/folders between a container and the local filesystem
   create      Create a new container
   diff        Inspect changes to files or directories on a container's filesystem
   events      Get real time events from the server
   export      Export a container's filesystem as a tar archive
   history     Show the history of an image
   import      Import the contents from a tarball to create a filesystem image
   inspect     Return low-level information on Docker objects
   kill        Kill one or more running containers
   load        Load an image from a tar archive or STDIN
   logs        Fetch the logs of a container
   pause       Pause all processes within one or more containers
   port        List port mappings or a specific mapping for the container
   rename      Rename a container
   restart     Restart one or more containers
   rm          Remove one or more containers
   rmi         Remove one or more images
   save        Save one or more images to a tar archive (streamed to STDOUT by default)
   start       Start one or more stopped containers
   stats       Display a live stream of container(s) resource usage statistics
   stop        Stop one or more running containers
   tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
   top         Display the running processes of a container
   unpause     Unpause all processes within one or more containers
   update      Update configuration of one or more containers
   wait        Block until one or more containers stop, then print their exit codes

呪文表 ``inspect``
----------------------------------------------------------------------

:samp:`docker inspect {<container>}`
   稼働中のコンテナーを検査する。

呪文表 ``logs``
----------------------------------------------------------------------

:samp:`docker logs -f {<container_name>}`
   コンテナーのログを取得、追跡する。

呪文表 ``rmi``
----------------------------------------------------------------------

コマンド ``rmi``, ``image rm``, ``image remove`` は互いに同等。

:samp:`docker rmi {<image_name>}`
   イメージを削除する。

呪文表 ``start``
----------------------------------------------------------------------

:samp:`docker start {<container>}`
   既存のコンテナーを開始する。

呪文表 ``stats``
----------------------------------------------------------------------

コマンド ``stats`` と ``container stats`` は同等。

``docker container stats``
   資源使用統計を標準出力に出力する。|Ctrl+C| で終了。

呪文表 ``stop``
----------------------------------------------------------------------

:samp:`docker stop {<container>}`
   既存のコンテナーを停止する。
