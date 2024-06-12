======================================================================
Docker 利用ノート
======================================================================

.. |Dockerfile| replace:: :file:`Dockerfile`

遅ればせながら Docker を習う。

.. contents:: 本章見出し
   :depth: 3
   :local:

手順
======================================================================

WSL2 Ubuntu 22.04.4 LTS に Docker Engine をインストールして学習を進める。Docker
Desktop は当面の間導入しないでおく。今のところ、その選択による不都合は ``docker
init`` が使えないくらいしかない。

.. contents::
   :depth: 1
   :local:

以前の Docker 環境の残滓を一掃する
----------------------------------------------------------------------

環境が完全にクリーンである場合にはここを飛ばしてインストール工程を読め。以前、何
かの Docker チュートリアルをやって上手くいかなかった場合にはこの工程が外せない。

`Install Docker Engine on Ubuntu
<https://docs.docker.com/engine/install/ubuntu/>`__ 文書内の Uninstall old
versions 節および Uninstall Docker Engine 節の記述に従い、ゴミを掃除する。

* 列挙されている非公式パッケージを ``sudo apt remove`` でアンインストールする。
* それ以外は ``suto apt purge`` でアンインストールする。
* :file:`/var/lib/docker/` および :file:`/var/lib/containerd` をディレクトリーご
  と削除する。

さらにユーザー設定ファイルも削除するべきだと考えられる。ディレクトリー
:file:`~/.docker` があれば、丸ごと削除する。後ほど XDG Base Directory 対応と同時
に設定ファイルを作り直す想定だ。

Docker Engine をインストールする
----------------------------------------------------------------------

同ページ内 Install using the :command:`apt` repository 節の記述に従う。

初めて Docker Engine をインストールする前に Docker リポジトリーを仕掛ける必要が
ある。著名なデータベース等のインストール手順と共通するコマンドが含まれており、慌
てることはない。急所は次の二つのファイルを準備することだ：

* :file:`/etc/apt/keyrings/docker.asc`
* :file:`/etc/apt/sources.list.d/docker.list`

それが済んだら ``sudo apt install docker-ce`` を実行。関連パッケージも同時にイン
ストール。

Docker の世界における Hello world は次のコマンドを実行することのようだ：

.. sourcecode:: console
   :caption: Docker Engine 動作確認コマンド

   $ sudo docker run hello-world

以上が完了すれば、チュートリアルをひたすら消化して Docker を体で覚える段階だ。

もう一工夫
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`Linux post-installation steps for Docker Engine
<https://docs.docker.com/engine/install/linux-postinstall/>`__ に記述されている
ことをいくつか実施しておくとよい。

* :command:`sudo` なしで Docker コマンドを実行可能にする
* :command:`systemd` を使って Docker を起動するように構成する
* ストレージを無駄にせぬようにログファイル出力を構成する

最後の項目については `Configure logging drivers
<https://docs.docker.com/config/containers/logging/configure/>`__ 内囲み記事 Tip
の記述を注意深く読み、後続の構成例を参考にしろ。既定値が旧版互換性を維持するため
に非効率であることを理解しろ。

Docker Hub のアカウントを開設する
----------------------------------------------------------------------

何かのチュートリアルで初めて必要になるのが普通だと考えられる。GitHub と同様に、

* 無料アカウントを作成する
* 二因子認証を構成する

ところまで行えば十分だ。

チュートリアルをこなす
----------------------------------------------------------------------

`Docker Doc`_ は Guides, Manuals, Reference の三本柱で成り立っている。Guides の
所々にチュートリアル記事が用意されている。

Guides
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* Getting started

  * Get Docker Desktop - ``docker run -d -p 8080:80 docker/welcome-to-docker``
  * Develop with containers - ``docker compose watch``
  * Build and push your first image - Docker Hub アカウントを作成 / ``docker
    push`` まで実施
  * What's Next - ここで行先を保留
* Docker concepts

  * The basics

    * What is a container? - ``docker ps``, ``docker stop``
    * What is an image? - ``docker search``, ``docker pull``, ``docker image``
    * What is a registry? - ``docker build``, ``docker tag``, ``docker push``
    * What is Docker Compose? - :file:`compose.yml`, ``docker compose``
  * Building images

    * Understanding the image layers - ``docker container commit``, ``docker rm``
    * Writing a Dockerfile - |Dockerfile|
    * Build, tag, and publish an image - ``docker build``, ``docker image``,
      ``docker push``
    * Using the build cache - |Dockerfile| 最適化 / :file:`.dockerignore`
    * Multi-stage builds - ``docker images``
  * Running containers

    * Publishing and exposing ports - オプション ``-p HOST_PORT:CONTAINER_PORT``,
      :file:`compose.yml` ``ports`` リスト
    * Overriding container defaults - オプション ``-e VAR=VALUE``, ``docker
      network``
    * Persisting container data - ``docker volume``, ``docker exec``
    * Sharing local files with containers - オプション ``--mount``, ``-v``
    * Multi-container applications - ``docker compose``
* Language-specific guides - どれか一つを選んで演習すればいい。ここで Minikube
  が要る。
* Use-case guides

  * Overview
  * Machine learning & AI - TODO
  * Data science with JupyterLab - 未実施
  * Suppress image vulnerabilities with VEX - 実験的らしいので急ぎなら飛ばす。
  * Use containerized databases - MySQL
* Build with Docker - これを第一チュートリアルとしてもよい。

  * Introduction - ``docker build``, ``docker run``, ``docker exec``, ``docker
    stop``
  * Layers - |Dockerfile| は記述順が重要
  * Multi-stage - ``FROM``
  * Mounts - ``--mount``
  * Build arguments - ``ARG``
  * Export binaries - ``--output``
  * Test - ``--target``
  * Multi-platform - ``--platform``
* Deployment and orchestration

  * Overview - Docker Desktop を使わない縛りを入れたので、Kubernetes を有効にす
    る方法については Minikube の文書に従うことにする。
  * Deploy to Kubernetes - 同上。
  * Deploy to Swarm - ``docker stack``, ``docker service``
* Docker workshop - これを第一チュートリアルとしてもよい。

  * Part 2: Containerize an application - |Dockerfile| を書いて ``docker build``
    や ``docker run`` を実行する。
  * Part 3: Update the application - ``docker stop``, ``docker rm``
  * Part 4: Share the application - Docker Hub, ``docker push``, ``docker tag``
  * Part 5: Persist the DB - ``docker volume``
  * Part 6: Use bind mounts - ``--mount type=bind``, ``docker logs``
  * Part 7: Multi-container apps - ``docker network``
  * Part 8: Use Docker Compose - :file:`compose.yaml`, ``docker compose``
  * Part 9: Image-building best practices - ``docker image``
* Educational resources

  * `Live Debugging Node.js with Docker
    <https://training.play-with-docker.com/nodejs-live-debugging/>`__ は完走可能。
  * `Docker CLI cheat sheet
    <https://docs.docker.com/get-started/docker_cheatsheet.pdf>`__ はペラ一枚。

Manuals
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How to と Quickstart を中心にやる。

* Get Docker - 生の Docker Engine を使いたいのでここは捨て置く。
* Docker Desktop - この章もほとんど飛ばすことになる。

  * WSL - ただ、この節は読んでおいたほうがいい。
* Docker Scout

  * Quickstart - 実践的なチュートリアル。やるべきだ。
  * Install - XDG Base Directory に従いたいので、スクリプト実行後にバイナリーを
    :command:`mv` する。スクリプトを修正してから実行するとなぜか上手くいかない。
* Docker Engine

  * Install

    * Install Docker Engine on Ubuntu - 前述のとおり、これをいの一番に実施する。
  * Networking

    * Networking tutorials

      * Bridge network tutorial - TODO
      * Host networking tutorial - TODO
      * Overlay networking tutorial - TODO
      * Macvlan network tutorial - TODO
  * CLI

    * Use the Docker CLI - 重要な設定項目があるのでチェックする。
    * Completion - これは信じ難い。Bash の補完機能が :file:`~/.local/share` 以下
      を確認するというのか？
    * Filter commans - ``--filter KEY=VALUE`` を受け入れるコマンドを知るといい。
    * Format command and log output - これを読んで思った。Go 言語を学習するのが
      いい。
  * Manage resources
  * Daemon
  * Logs and metrics
  * Security
  * Swarm mode
* Docker Build
* Docker Compose

  * Quickstart - TODO
* Docker Hub

  * Create an account - Docker をインストールしたらすぐに実行可能。
  * Quickstart - アカウントを開設したらすぐに実行可能。

* Administration - TODO

構成
======================================================================

TBD

基本コマンド
======================================================================

TBD

資料
======================================================================

`Docker Docs`_
   一級資料。この文書群を丹念に読んで分析すれば入門者には十分だ。
`Docker Hub <https://hub.docker.com/>`__
   Docker イメージの物置サービス。GitHub と意味が似ている。
`Play with Docker Classroom <https://training.play-with-docker.com/>`__
   Docker Docs の補助教材として利用する。説明が詳細でありながら明瞭で気に入って
   いる。Hands On ページの右側コンソールを使わぬと試せない機能 (Swarm, etc.) が
   あり、押さえておくがよかろう。
`Minikube <https://minikube.sigs.k8s.io/docs/>`__
   TBD

整理中
======================================================================

* Minikube



.. Docker Docs: https://docs.docker.com/
