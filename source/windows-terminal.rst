======================================================================
Windows Terminal 利用ノート
======================================================================

`Windows Terminal <https://aka.ms/terminal>`__ はさまざまな CLI プロセス群を一箇
所にまとめることができる便利なソフトウェアだ。

* タブインターフェイス、
* ウィンドウ分割ペイン、
* Unicode/UTF-8 対応、
* GPU による高速レンダリング、
* テーマ（配色、フォント）
* ショートカットキー設定

など、機能を豊富に備えている。

.. note::

   :Version: 1.14.2281.0
   :OS: Windows 10 Home

.. contents::

インストールする
======================================================================

Windows Terminal をインストールには複数の方法が用意されているようだが、次のどち
らかが望ましい。

* Microsoft Store 経由でインストール
* Windows 標準のコマンドライン上などから :program:`winget` でインストール

新マシンでのインストール手段は、旧マシンで :program:`winget export` したプログラ
ムリストを :program:`winget import` してインストールすることを想定している。

アップグレードする
======================================================================

Windows Terminal は自動更新機能を実装していないようなので、採用したインストール
手段に対応したアップグレード手段を採る。

* Microsoft Store の更新ボタンを押す
* コマンド :program:`winget upgrade` を実行する

.. note:: 関連ノート

   :doc:`/winget`

設定をバックアップする
======================================================================

Windows Terminal の設定内容は次のパスで示される JSON ファイルに保存されている。
これをバックアップなりバージョン管理するだけだ。

.. code:: text

   %LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json

使用方法
======================================================================

初めて Windows Terminal を起動したときには設定が出荷時のものに過ぎないから、おそ
らく使い物にならない。後述の構成設定を適宜済ませてから、再度メインウィンドウに戻る。

Windows Terminal を適切に構成すると、メインウィンドウにタブが一つ以上表示される。
各タブが何らかのコンソール画面に対応しているので、作業したいものをアクティブにして、
コマンドライン操作をすればいい。

Windows Terminal を終了する必要がある場合には、すべてのタブに対するコンソール上
でシェル固有の :command:`exit` コマンドを実行するか、メインウィンドウ自体をバツ
ボタンを押すなどする。

構成設定
======================================================================

Windows Terminal の設定は上述の JSON ファイルを直接的に編集するか、設定画面経由
で間接的に編集することで実現する。設定画面を表示するには、メインウィンドウのメ
ニューバー的なところの :guilabel:`v` をクリックすると出現するメニュー内にある項目
:guilabel:`設定` を選択する。

以下、要となるオプションのみを記す。

Startup
    Windows Terminal 起動時に影響するオプションを決定する。

    * :guilabel:`Default profile`: :guilabel:`Bash (WSL2)`
    * :guilabel:`When Terminal starts`: :guilabel:`Open a tab with the default profile`
    * :guilabel:`Launch size` で列数（横）と行数を適宜指定する。
Interaction
    Windows Terminal と私との間に起こる動作に影響するオプションを選択する。

    * :guilabel:`Automatically copy selection to clipboard`: OFF
    * :guilabel:`Text format when copying`: :guilabel:`Plain text only`
    * :guilabel:`Remove trailing white-space in rectangular selection`: ON
    * :guilabel:`Remove trailing white-space when pasting`: ON
    * :guilabel:`Snap window resizing to character grid`: ON
    * :guilabel:`Automatically focus pane on mouse hover`: OFF
    * :guilabel:`Automatically detect URLs and make them clickable`: ON
Appearance
    Windows Terminal の見てくれを調整するオプション画面だ。

    どのソフトウェアを使うときにも言えることだが、
    Google 検索で調べ物をするときの便宜を図るべく、UI を英語にしておく。
    そして、見てくれの調整に注力して時間を浪費するようなことは避ける。

    * :guilabel:`Language (requires relaunch)`: :guilabel:`English (United States)`
    * :guilabel:`Always show tabs`: ON
    * :guilabel:`Hide the title bar (requires relaunch)`: OFF
    * :guilabel:`Always on top`: OFF
    * :guilabel:`Tab width mode` を好みの値に設定。
    * :guilabel:`Pane animations`: OFF
Color schemes
    Windows Terminal の配色を調整する、あるいは配色全体を定義するための画面だ。
    したがって、ここに手を出す必要はない。
Rendering
    Windows Terminal の描画効率最適化を図る項目からなる画面だが、素人お断りという空気だ。
    全部既定値のままでよかろう。
Actions
    Windows Terminal で定義されているショートカットキーの集合だ。
    常用するシェルのキーバインドと衝突するものがないかどうかを確認しておくべきだ。

Profiles
----------------------------------------------------------------------

:guilabel:`Defaults` とプロファイル個別の設定を二段構えで指定する構えを取っている。
前者でコンソールすべてに共通する設定をし、後者でシェルごとの設定項目を上書きすると考えればいい。

Defaults
    コンソールすべてに共通する設定をする。

    :guilabel:`Run this profile as Administrator`: OFF

    Appearance
        コンソール画面すべてに共通する設定項目の集合。

        * :guilabel:`Font face`: こだわりのフォントがあるならば設定してもよい。
        * :guilabel:`Font size`: 上記に合わせて指定する。
        * :guilabel:`Cursor shape`: キャレットの形状を指定する。
        * :guilabel:`Scrollbar visibility`: :guilabel:`Visible`
    Advanced
        どの範疇にも該当しないような設定項目の居場所となる画面だ。

        * :guilabel:`History size`: 大きい数字にしておく。
        * :guilabel:`Profile termination behavior`: 場合によっては無条件に閉じるでいいかもしれない。
プロファイル個別画面
    私の現在の環境では Bash (WSL2), Windows Powershell, cmd, etc. と並んでいる。
    どの設定画面も項目の構造に差異はないので、まとめて説明する。

    * :guilabel:`Command Line` は念入りに確認しておく。WSL2 の場合には
      :code:`wsl.exe ~ -d Ubuntu` のように指定しておく。
    * :guilabel:`Icon` は適宜指定しておく。見てくれに関する項目ではあるが、
      他人に画面を見せるときにわかりやすさが圧倒的に良くなるので、明示的にファイルパスを与える。

    Appearance, Advanced 各サブ画面については先述のとおり。ただし
    :guilabel:`Run this profile as Administrator` については ON に上書きするプロ
    ファイルが考えられる。管理者権限で起動したい :program:`cmd` などがあり得る。

Windows Terminal 自身へのコマンドライン引数
======================================================================

TBW
