======================================================================
Bash 手筋集
======================================================================

編集方針が定まっていないが出航。

.. contents:: 本章見出し
   :local:

チュートリアル
======================================================================

`Bash Scripting Tutorial - Linux Shell Script and Command Line for Beginners <https://www.freecodecamp.org/news/bash-scripting-tutorial-linux-shell-script-and-command-line-for-beginners/>`__
   シェルスクリプト作成に集中した手引。スクリプトのデバッグ手法に関する記述があ
   りがたい。

   * 今自分が使っているシェルが何かわからない場合は :program:`ps` で確認する。
   * めったに使わぬゆえ忘れていたがコマンド :command:`read` を使ってユーザー入力
     を読むことができる。
   * よく使われるコマンド一覧にディスク空き容量を見るための :program:`df` がある
     が、ほとんど使ったことがない。
   * Case statements: 入門者向けの記事で ``case`` 文を扱うのは珍しいかもしれない。
   * スクリプトの最初に ``set -x`` を設定する。デバッグモードが有効になり、Bash
     が実行したコマンドそれぞれの先頭に ``+`` 記号を付けて端末に出力する。端末で
     やってもよい。解除は ``set +x`` とする。
   * Bash はエラーが発生すると、エラーの内容を示す終了コードを変数 ``?`` に設定
     する。値 0 は成功を表し、それ以外の値はエラーを表す。``[ $? -ne 0 ]``
   * ``set -e`` を用いると、スクリプト内のコマンドが失敗した場合に Bash がエラー
     で終了するようになり、エラーの特定が容易になる。
`Bash Scripting Tutorial - Linux Tutorials - Learn Linux Configuration <https://linuxconfig.org/bash-scripting-tutorial>`__
   * ``date +20220209`` には何の意味が？
   * ``args=("$@")`` は面白い記法だ。``${args[0]}``, ... のほうが可読性はある。
   * Bash スクリプトの中で別のシェルコマンドを実行する最善の方法は
     :samp:`$({command})` 構文を使ってサブシェルを作成することだ。
   * :command:`read` は変数を複数取れる。特に、``read -a`` で配列が使える。
   * Bash Trap Command: :command:`trap` を Bash スクリプトで使用すると、スクリプ
     トに送られた信号を捕捉し、その信号が発生したときにサブルーチンを実行するこ
     とができる。:kbd:`C-c` を押した時に止めるコードなどを実現できる。
   * Read file into bash array: このコードは :command:`exec` を用いたリダイレク
     ト操作を理解するのが難しい。
   * 算術比較演算子と文字列比較演算子を区別して理解しろ。
     ``-n``, ``-z`` は文字列に対する単項演算子。
   * さらに出番の少ない ``select`` 文。
   * ``$' '`` という特殊な引用構文？がある。
   * STDERR from bash script to STDOUT: ``2>&1`` は頻出。

     * ``>&`` や ``&>`` という記法もある。
   * エラーだけ要る場合は ``2>``
   * 最後のリンク集も当然気になる。
`Bash Scripting Tutorial - Ryans Tutorials <https://ryanstutorials.net/bash-scripting-tutorial/>`__
   TBW
`Bash Tutorial | Bash Scripting Tutorial - Javatpoint <https://www.javatpoint.com/bash>`__
   TBW

手筋
======================================================================

`Bash Shell Scripting: 10 Must-Know Tips for Beginners <https://www.fosslinux.com/105140/10-must-know-bash-shell-scripting-tips-and-tricks-for-beginners.htm>`__
   この記事はかなり入門者向け。

   * 変数名をいつでも braces で囲むと曖昧さがなくなる。``$varname`` ではなく
     ``${varname}``
   * この記事を読むまで気づかなかったが、:samp:`$({command})` 形式で自作関数を指
     定可能。
`Bash Command Line Tips to Help You Work Faster <https://www.freecodecamp.org/news/bash-command-line-tips-to-help-you-work-faster/>`__
   * :samp:`nohup {command} &` パターン
   * :samp:`time {command}` パターン
   * 整数の算術演算は :samp:`echo $(({arithmetic-expr}))` パターンと
     :program:`bc` にパイプするパターンがある。
   * Brace expansion は日常的に用いる。
`Stupid Bash tricks: History, reusing arguments, files and directories, functions, and more | Enable Sysadmin <https://www.redhat.com/sysadmin/stupid-bash-tricks>`__
   * 最初の例は ``^status^start^`` でもいい？
   * ``HISTSIZE`` を 5000 にしている。私の五倍ある。
   * ``history -d`` のほうがゴミコマンドを柔軟に削除できまいか？
   * ``$_`` の値は直前コマンドの最終引数。``mkdir work && cd $_`` のように使う。
   * 再帰の深さを制限する変数 ``FUNCNEST`` を何かのために覚えておく。
   * :command:`kubectl` のラッパー関数を作成するハメになるのは、オリジナルの設計
     が良くないか、構成ファイルに見落としがあるか、等ではないか？
`Bash tips for everyday at the command line | Opensource.com <https://opensource.com/article/18/5/bash-tricks>`__
   * Bash オプション ``histappend`` はオンにする。
   * 今まで :kbd:`↑` 押しでいいではないかと思ってまったく使わなかった ``!!`` の
     真価。
   * ``!*`` は「直前コマンドの ``$0`` 以外」に展開される。
   * 履歴の中で最も実行されたコマンドの例は、履歴一覧書式によって :program:`awk`
     部分を書き換える。また、無視されるコマンドは当然現れない。
   * Bash オプション ``cdspell`` はオンにする。
   * キーバインドの確認には ``bind -p`` を実行する。
   * コマンドラインでの :kbd:`C-u` は ``unix-line-discard`` なので使おう。
   * 長いジョブ実行中のポーズを試したい。キーバインドは :kbd:`C-s` らしい。アン
     ポーズは :kbd:`C-q` 押し。コマンド ``sleep 1`` 実行中に試したところ、確かに
     機能しているらしい。
   * ``2>&1`` リダイレクトの技法は基本的。
   * 組み込みコマンド :command:`command` を ``-V`` 付きで呼び出すと
     :command:`which` 以上に便利。
`Tips and Tricks for the Novice Bash User // High Performance Computing // Marquette University <https://www.marquette.edu/high-performance-computing/tips-and-tricks.php>`__
   * Wildcards: ``*``, ``?``, ``[]`` の三つともワイルドカードの一種。一度にこれ
     らを複数組み合わせることが可能。
   * Curly Brace Expansions: ``{}`` で範囲を指定するときは ``..`` を使う。角括弧
     と異なる。列挙はカンマ。パターンの展開順序は左から。ワイルドカードと混ぜて
     パターンを組める。
   * ワイルドカードは現在ディレクトリーの中身に基づいて展開される。
   * Environment Variables: :envvar:`PATH` の独特な更新方法について。
   * For Loops and If Statements: ``for`` ループで理解が不確かなのは ``in`` の引
     数の書き方だ。配列のようなものだとは思うが。

     * ``if`` 文の条件記述では :samp:`[ {condition} ]` を用いる。演算子は覚える
       しかない。
`6 Bash Scripting Tips and Tricks - Codecov <https://about.codecov.io/blog/6-bash-scripting-tips-and-tricks/>`__
   * Printing to stdout and saving to variable from stderr: 再現しようとすると改
     行文字が変数中から失われるが？
   * Print the length of an array: 基本なので ``$#ARRAY[@]`` を覚える。
   * Transform a space-separated list into an array: 中括弧を使って
     ``${ARRAY[@]}`` や ``${#ARRAY[@]}`` と書くと正しい値が出力される。ちなみに
     配列定義は ``ARRAY=($(echo "one two three"))`` と一気に書ける。
   * Join an array with “: ``[@]`` と ``[*]`` の違いをよく理解する。先ほどの配列
     長を得るのに前者が本質的だった理由がこれでわかる。
