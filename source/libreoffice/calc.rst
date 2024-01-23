======================================================================
LibreOffice Calc 利用ノート
======================================================================

.. note::

   :Platform: Windows 10
   :Version: 7.6.4.1 x86_64

.. contents::

個人的必修機能 Calc 編
======================================================================

私が考える習得優先度の高い順に排列したいが、難しい。習得方法はすべて前述のチュー
トリアルにある。

* ワークシート基本操作：追加、削除、移動、複製、名前変更
* 行、列、セルの固定 (:menuselection:`&View --> Freeze &Cells`, etc.)
* 検索 (:kbd:`Ctrl` + :kbd:`F`)
* セルの書式設定 (:kbd:`Ctrl` + :kbd:`1`)

  * 特に重要なのは :guilabel:`Numbers` タブにおける設定だ。数値や日付の表記仕様
    を細かく指示するのはここでしかできない。
  * 日付、時刻の書式コードはややクセがある（和暦のコードがある）。
* 空行を削るにはコツがある。データをフィルターで絞り込んで空行を連続させてからコ
  マンド :menuselection:`&Delete Rows` を実行する。
* コマンド :menuselection:`Paste &Special` は :kbd:`Ctrl` + :kbd:`Shift` +
  :kbd:`V` で実行したい。
* 内容に基づくセル分割技法

  * コマンド :menuselection:`&Data --> Te&xt to Columns...` を使え。区切り文字に
    基づく文字列分割がもっとも自然かつ容易だ。
  * 文字列関数 ``MID``, ``LEFT``, ``RIGHT`` などと ``FIND`` を組み合わせて各部分
    を別のセルに出力することも可能だ。元のセルを損なわない。
* TODO: :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`Enter`
* :kbd:`Ctrl` + :kbd:`;` による日付の入力はシート再計算時に更新されない
* Auto Filter オンオフ (:kbd:`Ctrl` + :kbd:`Shift` + :kbd:`L`)
* 条件付き書式設定 :menuselection:`F&ormat --> &Conditional --> &Condition`

* 列を隠す（右クリックメニューから）
* 隠した列をまた見せる（前後の列を選択する必要がある）
* 列幅最適化

  * 列ヘッダー境目をダブルクリック
  * :menuselection:`F&ormat --> Colu&mns --> &Optimal Width` などを実行するのは
    複数列を一度に調整したいときだ。

* 関数

  * その入力時に、関数の引数リストの区切り文字を ``,`` ではなく ``;`` にすると紛
    れがない。
  * 文字列を連結する方法は複数ある。``CONCATNATE``, ``TEXTJOIN``, ``&``, etc.

  * ``SUMIF``, ``SUMIFS``: 条件を与えて和を得る
  * ``COUNTA``, ``COUNTBLANK``, ``COUNTIF``: セルの個数を得る（状況に応じて使い
    分ける）
  * ``WEEKDAY(date, 3)`` で Python の ``datetime`` ルールに相当する
  * ``DATEDIF`` は日付二つの間の日数を返す
  * ``TODAY()``: 入力時点の日付
  * ``EXACT``, ``MATCH``
  * ``AND``, ``OR``: 論理演算
  * ``IF``, ``IFS``: 条件分岐
  * ``INDEX``
  * ``SUBSTITUTE``, ``REPLACE``: 文字列置換
  * ``SEARCH``, ``FIND``: 文字列検索
  * ``TEXT(number, format)``: 文字列に変換する関数とみなせる

    * 引数 ``format`` に指定する書式文字列はさまざまだ。応用が多い。
    * 数値をメートル法単位接頭辞を付けて表す e.g. :samp:`TEXT({num},"#.#0,,") & "M"`.
    * 数値を百分率表記で返す e.g. :samp:`TEXT({num}, "0.0%")`.
    * 数値を分数表記で返す e.g. :samp:`TEXT({num}, "?/?")`.
    * 数値を科学的記法で返す e.g. :samp:`TEXT({num}, "0.0E+00")`.
    * 日付や時刻あるいはその両方に対し、書式を指定して文字列を返す
      e.g. :samp:`TEXT({date}, "yyyy-mm-dd")`, :samp:`TEXT({time}, "HH:MM:SS AM/PM")`.

  * ``TRIM(text)``
  * ``VLOOKUP``: 表を上から下へ検索する。キーを検索して合致する値に関連する値を
    返す。

    * 検索範囲指定（第二引数）を絶対参照で行うべきだ。
    * この関数が存在するので、表においては最初の列をキーにするのが最善だ。
    * 最後のフラグ引数は検索比較の緩さを許容するかどうかを示す。

* 相対参照、絶対参照の仕組み
* 絶対参照と相対参照を切り替える (:kbd:`F4`)
* ハイパーリンクは :kbd:`Ctrl` + :kbd:`K` で定義するものと、関数
  ``HYPERLINK(url, text)`` で実現するものがある。

* :menuselection:`&Data --> More &Filters --> &Advanecd Filter...` で重複削除な
  どが可能
* セル同士の差分を検証する

  * 単純に ``=`` で比較する
  * ``MATCH``, ``EXACT`` の値を使う
  * 強調には :menuselection:`F&ormat --> &Conditional --> &Condition` を利用
* 自動埋め

  * マウスドラッグによる範囲拡張方法

    * 数値が増えるのを抑止するには :kbd:`Ctrl` を押しながらドラッグする。

  * :kbd:`Ctrl` + :kbd:`D`
  * :menuselection:`&Sheet --> F&ill Cells --> Fill &Down`, etc.

* 空セルを埋める技法：補助セル列を定義する。各行の内容は一行上のセルを相対参照す
  るものとする。そして :menuselection:`Paste &Special...` の :guilabel:`Skip
  empty cells` を上手く使う。作業後、補助セル列は削除していい。
* 印刷プレビュー切り替え :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`O`
* 印刷範囲定義 :menuselection:`F&ormat --> Prin&t Ranges --> &Edit...`
* 印刷ヘッダーおよびフッター設定方法
* 印刷ページ共通ヘッダー行設定方法

Calc Guide からのメモ
======================================================================

Chapter 1 Introduction
----------------------------------------------------------------------

CSV ファイルのインポート方法。:guilabel:`Text Import` ダイアログで上手く指定す
る。

TBD

Chapter 2 Entering and Editing Data
----------------------------------------------------------------------

* セル自動補完で候補が複数ある場合は :kbd:`→` で次候補が得られるかもしれない。
* :menuselection:`&Sheet --> F&ill Cells --> Fill &Down`, etc.
* :kbd:`Ctrl` + :kbd:`D`
* :menuselection:`&Sheet --> F&ill Cells --> Fill S&eries...`
* 連続データ自作方法はオプションダイアログの :menuselection:`LibreOffice Calc
  --> Sort Lists` を調べろ。
* セルに同列項目からなるドロップダウンリストを表示 :kbd:`Alt` + :kbd:`↓`
* 自動補完は使えないが :menuselection:`&Data --> F&orm...` というレコード追加機
  能がある。
* 内容に基づくセル分割技法

  * コマンド :menuselection:`&Data --> Te&xt to Columns...` を使え。区切り文字に
    基づく文字列分割がもっとも自然かつ容易だ。
  * 文字列関数 ``MID``, ``LEFT``, ``RIGHT`` などと ``FIND`` を組み合わせて各部分
    を別のセルに出力することも可能だ。元のセルを損なわない。
* セルに対して :menuselection:`&Data --> &Validity...` を使えば入力値に制約を定
  義できる。

  * ドロップダウンリスト実装方法
  * 制約を決めるのに有用な名前付き範囲定義方法 (:menuselection:`&Sheet -->
    &Named ranges and expressions --> &Define`)
* 上の制約に関する不正データ検出用コマンド

  * :menuselection:`&Tools --> &Detective --> &Mark Invalid Data`
  * :menuselection:`&Tools --> &Detective --> Remove All Traces`
* セル削除技法

  * 中身を消去するだけなら :kbd:`Delete` 押しで十分
  * 行または列を削除するならば :kbd:`Ctrl` + :kbd:`-` 押しが早い
  * 選択セルによっては :guilabel:`Delete Cells` ダイアログが開く場合がある
  * 書式を取り消すなら :kbd:`BackSpace` 押しで :guilabel:`Delete Contents` ダイ
    アログを開け
* 貼り付け

  * コマンド :menuselection:`Paste &Special` は :kbd:`Ctrl` + :kbd:`Shift` +
    :kbd:`V` で実行したい。
* Calc でもフィールドが使える :menuselection:`&Insert --> Fiel&d`
* グループ機能は使わない
* フィルター機能

  * :menuselection:`&Data --> More &Filters --> &Standard Filter...` で絞り込み
    ダイアログを開く
  * 自動フィルターは :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`L` でオンオフしろ
  * 自動フィルターダイアログでは色や条件指定で絞り込むことも可能
  * :menuselection:`&Data --> More &Filters --> &Advanced Filter...` は条件をど
    こかのセルから与える
* ソートについては :menuselection:`&Data --> &Sort...` で指定ダイアログが開く
* 検索と置換

  * :kbd:`Ctrl` + :kbd:`F` の検索バーは簡易版
  * :kbd:`Ctrl` + :kbd:`H` で :guilabel:`Find and Replace` ダイアログが開く
  * 正規表現を使える

Chapter 3 Creating Charts and Graphs
----------------------------------------------------------------------

* :menuselection:`&Insert --> &Chart...` でウィザードダイアログが開く
* チャートの見てくれをサイドバーで調整可能
* チャートを編集するにはダブルクリック、または右クリックメニューから
  :menuselection:`&Edit` を選択する

  * チャート編集モードに入ると、Calc メイン GUI 構成が変化する。
* チャートの型は作成後でも変更可能 :menuselection:`F&ormat --> Chart T&ype...`
* チャートの題名、副題、軸ラベルを設定するには :menuselection:`&Insert -->
  &Titles...` でダイアログを開く
* 凡例の調整

  * サイドバー :menuselection:`Elements --> Legend` 区画
  * チャート編集モードメニュー :menuselection:`&Insert --> &Legend...`
* 背景色設定

  * サイドバー :menuselection:`Area --> Fill` 項目
  * チャート編集モードメニュー :menuselection:`F&ormat --> Chart &Area...`

.. todo:: TBD

Chapter 4 Formatting Data
----------------------------------------------------------------------

* セルで複数行テキストを表示する方法（どれでも可）

  * :guilabel:`Format Cells` ダイアログ :guilabel:`Alignment` タブ内
    :guilabel:`Wrap text automatically` をオン
  * サイドバー :guilabel:`Wrap Text` をオン
  * ツールバー
* セルに改行文字挿入を入力する方法

  * 直接編集ならば :kbd:`Ctrl` + :kbd:`Enter` 押し
  * 数式バー編集ならば :kbd:`Shift` + :kbd:`Enter` 押し
* セルの数値書式設定

  * ツールバーのボタンで間に合うならそれを使え
  * キーバインドも設定されている (e.g. :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`3`)
* フォント周りは割愛
* セル枠周りは割愛

AutoFormat
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

少なくとも三列・行（ヘッダーを含む）上で書式を設定したいセルを選択する。メニュー
:menuselection:`F&ormat --> AutoFormat &Styles...` でダイアログを開く。そこから
プリセットのスタイルを選択するか、逆に、シート上でスタイリングしてから
:guilabel:`Add` ボタンで追加するという機能だ。

値強調表示
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

値強調の表示切替は :kbd:`Ctrl` + :kbd:`F8` 押しが良い。

この表示は初期状態で有効にしたい。設定ダイアログの :menuselection:`LibreOffice
Calc --> View --> Display --> Value highlighting` をオンに設定しろ。

条件付き書式
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

事前条件は :menuselection:`&Data --> Ca&lculate --> Auto&Calculate` がオンになっ
ていることだ。

セルを選択してから :menuselection:`F&ormat > C&onditional` 以下のサブメニュー各
項目を選択するとダイアログがそれぞれ開く。

Condition
   条件を満たすセルデータを強調表示するための書式を規定する。
Color Scale
   セル値に応じて背景色を設定する。何段階かに色分けして表示する。
Data Bar
   棒グラフの棒一本一本を各セル内に描画してデータを表現する。All Cells 限定。
Icon Set
   各セルのデータの横に図像を表示し、設定範囲内のどこにデータが位置するのかを視
   覚的に表現する。All Cells 限定。
Date
   現在を基準として特定の日付範囲を指定書式で表記する。

いったん定義した条件付き書式は :menuselection:`F&ormat --> C&onditional -->
&Manage...` で編集可能。

データ表示切替
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

シートを非表示とする場合は、シートタブの右クリックメニューから
:menuselection:`&Hide Sheet` を実行する。

列または行を非表示にする場合は、列ヘッダーまたは行ヘッダーをクリックして選択状態
にし、右クリックメニューから:menuselection:`&Hide Row` または
:menuselection:`&Hide Column` を実行する。

セルを非表示にする場合、次の少し複雑な手順を要する。この手続きで、画面上では空欄
になる：

1. セルの :kbd:`Ctrl` + :kbd:`1` ダイアログ :guilabel:`Cell Protection` タブのそ
   れらしい項目をオンにする。
2. 当該セルのあるシートタブの右クリックメニューから :menuselection:`&Protect
   Sheet...` を実行し、:guilabel:`Protect this sheet and the contents of
   protected cells` をオンにする。ダイアログ上のその他の項目も適宜設定する。

非表示にしたシート、列、行を復元する方法は対応する Show コマンドを実行すればいい
のだが、先頭列を非表示から表示に戻す場合には選択にコツがいる。行 :guilabel:`1`を
選択し、列ヘッダー :guilabel:`B` の右クリックメニューから :menuselection:`Show
Columns` を実行するのだ。列の場合、縦横を入れ替えて同様の操作をすることで表示を
戻すことになる。

非表示（保護）セルの復元方法は、先ほどのダイアログ指定値を通常セルのものと同等に
すればいいだろう。パスワードに注意。

個人的必修キーバインド Calc 編
======================================================================

Windows 標準のキーバインドは省略。便利なキーバインドを積極的に習得しろ。

.. csv-table::
   :delim: |
   :header: キーバインド,コマンド,動作
   :widths: auto

   :kbd:`F2` | Cell Edit Mode | セル内容編集を開始する
   :kbd:`F4` | Cycle Cell Reference Types | 相対参照と絶対参照をトグルしていく
   :kbd:`F5` | Navigator | :guilabel:`Navigator` ダイアログを開く
   :kbd:`F9` | Recalculate | 数式などの評価を更新する
   :kbd:`F11` | Styles | :kbd:`Alt` + :kbd:`2` 相当だがトグル操作なので便利
   :kbd:`F12` | Group | セルをグループ化する
   :kbd:`Insert` | Paste Special | ノートで述べた
   :kbd:`Shift` + :kbd:`F3` | Cycle Case | 英文編集でよくやる変換
   :kbd:`Shift` + :kbd:`F5` | Trace Dependents | 対象セルの参照元を強調する
   :kbd:`Shift` + :kbd:`F9` | Trace Precedents | 対象セルの参照先を強調する
   :kbd:`Shift` + :kbd:`F11` | Save as Template | :guilabel:`Save as Template` ダイアログを開く
   :kbd:`Shift` + :kbd:`Space` | Select Row | 対象セルを含む行を選択する
   :kbd:`Shift` + :kbd:`BackSpace` | Undo Selection | セル選択解除
   :kbd:`Ctrl` + :kbd:`1` | Format Cells | ノートで述べた
   :kbd:`Ctrl` + :kbd:`D` | Fill Down | ノートで述べた
   :kbd:`Ctrl` + :kbd:`;` | Insert Current Date | ノートで述べた
   :kbd:`Ctrl` + :kbd:`F2` | Function | :guilabel:`Function Wizard` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`F3` | Manage Names | :guilabel:`Manage Names` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`F12` | Ungroup | グループ化したセルを解除する
   :kbd:`Ctrl` + :kbd:`Home` | To File Begin | データ領域の左上へジャンプ
   :kbd:`Ctrl` + :kbd:`End` | To File End | データ領域の右上へジャンプ
   :kbd:`Ctrl` + :kbd:`PageUp` | To Previous Sheet | Tab を使うキーバインドもある
   :kbd:`Ctrl` + :kbd:`PageDown` | To Next Sheet | 同上
   :kbd:`Ctrl` + :kbd:`Space` | Select Column | 対象セルを含む列を選択する
   :kbd:`Ctrl` + :kbd:`+` | Insert Cells | :guilabel:`Insert Cells` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`-` | Delete Cells | :guilabel:`Delete Cells` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`*` | Select Data Area | データ領域全体を選択する
   :kbd:`Ctrl` + :kbd:`/` | Select Array Formula | ノートで述べた
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`J` | Full Screen | 全画面表示切り替え
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`L` | AutoFilter | ノートで述べた
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`T` | Sheet Area Input Field | :guilabel:`Name Box` にフォーカス
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`V` | Paste Special | ノートで述べた
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`;` | Insert Current Time | 入力時点での現在時刻
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`F5` | Sheet Area Input Field | もう一つのキーバインド
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`Space` | Select All | 全セル選択
   :kbd:`Alt` + :kbd:`5` | Open the Functions Deck | 画面右端のドックを開く
   :kbd:`Alt` + :kbd:`↓` | Selection List | セルにドロップダウンリストを表示
   :kbd:`Ctrl` + :kbd:`Alt` + :kbd:`C` | Edit Comment | 共通キーバインドが上書きされている
   :kbd:`Ctrl` + :kbd:`Alt` + :kbd:`Shift` + :kbd:`V` | Paste Unformatted Text | 書式抜きでテキストを貼り付ける

.. _LibreOffice: https://www.libreoffice.org/
