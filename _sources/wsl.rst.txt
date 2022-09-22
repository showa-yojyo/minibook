======================================================================
Windows Subsystem for Linux 利用ノート
======================================================================

Linux 用 Windows Subsytem for Linux (WSL) を使用すると、従来の仮想マシンなどの
オーバーヘッドなしで、コマンドラインツール、ユーティリティー、アプリケーションな
どを含む GNU/Linux 環境のほとんどを、変更せずに Windows 上で直接実行できる。

.. note::

   本ノートを記すのに用いている Windows 本体、WSL および Ubuntu のバージョン情報
   はそれぞれ次のとおりだ。

   :OS: Windows 10 Home version 22H2 ビルド 19045.2006
   :WSL2: 5.10.102.1
   :Ubuntu: 20.04 LTS

.. contents::

インストール
======================================================================

公式文書によると最初から :program:`wsl` が利用可能であるようだ。次のコマンドを実
行しろとある：

.. code:: doscon

   > wsl --install

これが上手くいくと WSL が利用可能になる。上のコマンドではインストールオプション
を指定していないため、Linux のディストリビューションとして Ubuntu が暗黙的に選択
される。

既定の Linux ディストリビューションが Ubuntu であることと、私がそれしか利用しな
いことから、本稿ではこれ以降、この二つの単語を区別なしに記述するかもしれない。

アップグレードする
======================================================================

WSL 自体のアップグレード方法は次のコマンド実行による。これで WSL Linux カーネル
が（存在すれば）最新版に更新される。

.. code:: doscon

   > wsl --update
   更新をチェック中...
   利用できる更新はありません。
   カーネル バージョン: 5.10.102.1

Linux ディストリビューションのアップグレード方法を Ubuntu を例にとって記す。
おそらく次の方法すべてが等価で有効だ：

1. コンソールから :command:`winget upgrade -e --id Canonical.Ubuntu` を実行
2. Microsoft Store から :program:`Ubuntu on Windows` を更新

Use Cases
======================================================================

プログラム :program:`wsl` が利用者に用意している機能は次の二つに分類される：

* Linux プログラムを実行する
* WSL を管理する

Linux プログラムを実行する
----------------------------------------------------------------------

Linux コマンドを指定しないで実行すると、Linux シェルを起動する。

.. code:: doscon

   > wsl
   > wsl --distribution Ubuntu

Linux コマンド ``COMMAND_LINE`` を実行するには次のどちらかの形式を入力する。前者
はコマンドラインがシェルに渡る。後者はシェルを起動せずに実行するので、コマンドラ
イン文字列が解析されない。

.. code:: doscon

   > wsl COMMAND_LINE
   > wsl --execute COMMAND_LINE

オプションを付与することもできる。
``--distribution DISTRO_NAME`` で Linux ディストリビューションを指定したり、
``--cd WD`` や ``--user USER`` を使うことがあるかもしれない。

.. code:: doscon

   > wsl --cd /tmp -e pwd
   /tmp

Bash のような引数リストマーカー ``--`` も使える。

WSL を管理する
----------------------------------------------------------------------



構成
======================================================================

.wslconfig


.. code:: doscon

   > wsl --list --verbose
     NAME      STATE           VERSION
   * Ubuntu    Running         2

コマンド :program:`wsl` 自体の使い方
======================================================================

（実行頻度ではなく）実行可能性が比較的高いコマンドをまとめておく。

.. csv-table::
   :delim: @
   :header: コマンドライン,動作

   :command:`wsl` @ 現在のコンソールで既定の Linux ディストリビューションを起動する。
   :command:`wsl --install` @ 初回インストール時のコマンド。上記参照。
   :command:`wsl --list --verbose` @ Linux および WSL のバージョンを出力する。
   :command:`wsl --list --online` @ 使用可能 Linux ディストリビューション一覧。
   :command:`wsl --shutdown` @ 仮想マシンのシャットダウンコマンド。メモリー解放に援用できることに注意。
   :command:`wsl --update` @ WSL カーネルを更新しようとする。
   :command:`wsl --status` @ Linux 現時点でのディストリビューションと WSL の双方の一般的な情報を出力する。
   :command:`wsl --export Ubuntu` @ Linux ディストリビューションを TAR ファイルにアーカイブする。
   :command:`wsl --import` @ TAR ファイルから新しいディストリビューションに展開する。
   :command:`wsl --terminate` @ Linux ディストリビューションを停止する。
   :command:`wsl ~ -d Ubuntu` @ HOME ディレクトリーから Ubuntu を開始する。

関連文書
======================================================================

`Windows Subsystem for Linux に関するドキュメント | Microsoft Learn <https://learn.microsoft.com/ja-jp/windows/wsl/>`__

