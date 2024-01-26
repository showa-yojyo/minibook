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

Chapter 5 Using Styles and Templates
----------------------------------------------------------------------

シートに画像を追加する方法
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

次のどちらの方法でも、画像データを埋め込むか、参照で済ませるかを選べる：

* 画像をシート内にドラッグ＆ドロップする（リンクは :kbd:`Ctrl` + :kbd:`Shift` 押
  し）
* メインメニュー :menuselection:`&Insert --> &Image...` を実行する（リンクオプ
  ションあり）

リンクを多用する場合にはメインメニュー :menuselection:`&Edit --> Lin&ks to
External Files...` コマンドが重要だ。参照を差し替えたり、埋め込みに変えたりする
ことが可能だ。

その他の追加方法：

* システムクリップボードの内容が画像データの場合、貼り付けコマンド実行でそれを埋
  め込める。
* スキャナーが PC に接続されている場合、そこから取り込むコマンドもあるが、通常は
  いったん画像ファイルに保存して整形してからそれを上記の方法で追加するのが品質上
  望ましい。
* :menuselection:`View --> &Gallery` から画像を追加する。

画像を修正する方法
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

簡易な修正ならば Calc にある機能を用いてよい。:guilabel:`Image` ツールバーで基本
的な編集が可能だ。サイドバーでもよい。

位置、寸法、配置
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

画像の幾何を修正するには、他の描画ソフトの感覚でマウスを用いればいい。キーボード
を併用する編集動作もある。

数値的に制御したいならば右クリックメニューから :menuselection:`Position and
Si&ze...` を実行してダイアログから場所や寸法を指示する。座標単位系は設定ダイアロ
グによる。

その他の細かい調整機能（右クリックメニューから実行する場合）：

* :menuselection:`A&rrange -->` 各種（例：最背面移動）
* :menuselection:`Anc&hor -->` 各種（例：ページに固定）
* :menuselection:`Alig&n Objects -->` 各種（例：上端を揃える）
* 画像グループ（考え方は Inkscape などと同じ）

  * :menuselection:`&Group`, :menuselection:`&Ungroup`
  * :menuselection:`&Enter Group`, :menuselection:`&Exit Group`

LibreOffice 共通の描画ツール
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

いわゆる図形ツールだ。:menuselection:`&View --> &Toolbars --> Dra&wing` で図形
ツールバーを表示する。これを使って簡単な図形をシートに挿入することが可能だ。

その他のツール
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

画像の右クリックメニューにはその他雑多なコマンドがある。個人的に注意したいものは
:menuselection:`Co&mpress...` だ。埋め込んだ画像データを圧縮すればファイルサイズ
が小さくなる。

フォントワーク
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

文字列だけからロゴタイプを生成する機能だ。:menuselection:`&View --> &Toolbars
--> Fontwor&k` コマンドを実行してツールバーを表示する。使い方は見ればわかる。

QR コード
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:menuselection:`&Insert --> &OLE Object --> QR and &Barcode...` コマンドで開くダ
イアログは、入力文字列からコード画像を生成して現在のシートに出力する。

Chapter 7 Printing, Exporting, Emailing, and Signing
----------------------------------------------------------------------

Printing
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* :guilabel:`Standard` ツールバーに :guilabel:`Print Directly` ボタンを表示させ
  ておくと便利だ。
* 印刷をさらに制御するには :kbd:`Ctrl` + :kbd:`P` 押しで印刷ダイアログを開く。
* :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`O` で印刷プレビューモード切り替え

Using print ranges
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* 印刷範囲を自分で定義してもよい。セル範囲を選択してから :menuselection:`F&ormat
  --> Prin&t Ranges --> &Define` を実行する。
* 印刷範囲を変える場合には :menuselection:`F&ormat --> Prin&t Ranges -->
  &Edit...` を実行する。
* :menuselection:`&View --> &Page Break` で改行プレビュー

Page breaks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ページ分割は列方向と行方向の二種類ある。改行プレビューでは太い青線で描かれる。

* :menuselection:`&Sheet --> Insert Page &Break -->` 各コマンドでセルの上または
  左にページ行分割または列分割を挿入する。
* :menuselection:`&Sheet --> Delete Page &Break -->` 各コマンドは上記それぞれの
  逆操作だ。

Printing options for page styles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:guilabel:`Page Style: Default` ダイアログを開く方法を知る。複数ある：

* メインメニューから :menuselection:`F&ormat --> &Page Style...` コマンドを実行
* サイドバー :guilabel:`Styles` 内で

  1. :guilabel:`Page Styles` ボタンを押して
  2. :guilabel:`Default` 項目右クリックメニューから :guilabel:`&Edit Style...`
     コマンドを実行
* ステータスバー :guilabel:`Default` をダブルクリック

:guilabel:`Sheet` タブの設定に注意する。

Headers and footers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:guilabel:`Page Style: Default` ダイアログの :guilabel:`Header` タブと
:guilabel:`Footer` タブでそれぞれ設定可能。

特に :guilabel:`&Edit...` ボタンを押すと、Writer と同じようにフィールドを使って
内容を設定することが可能だ。

Exporting to PDF
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

直近に適用した PDF 設定に基づいてスプレッドシート全体を PDF に保存するには、
:guilabel:`Standard` ツールバー :guilabel:`Export Directly as PDF` アイコンをク
リックするのがよい。

:guilabel:`PDF Options` ダイアログで出力 PDF のオプションを細かく指定可能。職務
経歴書やスキルシートを PDF に変換して提出する前に利用したい。

Exporting to other formats
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Calc では次の二つのコマンドの意味を区別している：

* :menuselection:`&File --> Save &As...`
* :menuselection:`&File --> Expor&t...`

Emailing spreadsheets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:menuselection:`&File --> Sen&d -->` 各種コマンド実行で、シートを当該項目形式に
変換保存されたファイルが添付された状態のメール草稿編集中のメールクライアント画面
が開く。

Digital signing of documents
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:menuselection:`&File --> Di&gital Signatures --> Digital Signatu&res...` コマン
ドで署名。:guilabel:`Digital Signatures` ダイアログが開く。

.. admonition:: 利用者ノート

   Windows だと難しいかもしれない。

Removing personal data
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

オプションダイアログの :menuselection:`LibreOffice --> Security` の
:guilabel:`O&ptions...` を押してダイアログを開き、良さそうなオプションをオンにし
ろ。

:menuselection:`&File --> Proper&ties...` コマンドを実行。:guilabel:`General` タ
ブで：

* :guilabel:`&Apply user data` をオフにする
* :guilabel:`&Reset Properties` を押す

Chapter 8 Using Formulas and Functions
----------------------------------------------------------------------

Introduction
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

数式は数とテキストを評価するセルデータと考えられる。

Setting up a spreadsheet
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

オプションダイアログ内 :menuselection:`LibreOffice Calc --> View` 内
:guilabel:`Formula indicator and hint` をオンにしろ。これにより、数式を含むセル
の左下に小三角形が描かれ、ツールチップには数式が示される。数式バー非表示派の利用
者の使い勝手が向上する。

Creating formulas
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

数式を入力する方法：

* セルに対して直接入力
* Function Wizard を利用 (:menuselection:`&Insert --> &Function...` or
  :kbd:`Ctrl` + :kbd:`F2`)
* サイドバーの Functions を利用 (:kbd:`Alt` + :kbd:`5`)

意識したい演算子：

* 演算子 ``%`` は後置単項演算子として働く（意味は百分率）
* 不等式は ``<>`` を用いる
* 二項演算子 ``&`` は文字列連結演算
* セル指定のためのドットやコロン
* セル union 演算子 ``~``, e.g. ``A1:C3~B2:D2``
* セル intersection 演算子 ``!``, e.g. ``A2:B4 ! B3:D6``

相対参照と絶対参照について、これらの概念を理解しろ。セルのコピーやリンクに欠かせ
ない。参照様式を切り替えるのには :kbd:`F4` キーを使いこなせ。

セル自体を指すにはセルアドレスの他に名前を使える。セルや範囲に名前を付けること
で、数式の可読性と文書の保守性が向上する。名前を与える方法：

* :menuselection:`Sheet > &Named Ranges and Expressions > &Define...` コマンドを
  実行する。ダイアログで対象セル・範囲と名前を指示する。
* または、シートからセル・範囲を選択し、数式バーの左にある名前ボックスで名前を入
  力する。

このような名前の管理は :kbd:`Ctrl` + :kbd:`F3` 押しで開くダイアログで行う。

数式に名前をつけることも可能だ。

Understanding functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Calc が MS Excel のスプレッドシートを開くと、特定の関数で発生する非互換性を回避
する措置が自動的に働く。

関数は単体では存在できず、いつでも数式の部分である必要がある。

関数入力はサイドバーよりもウィザードのほうが使用頻度が高いらしい。

* ダイアログを開くのは :kbd:`Ctrl` + :kbd:`F2` 押しが早くて良い。
* :guilabel:`Structure` タブでは関数呼び出しの木構造が示される。

配列数式を理解しろ。配列式は一般に複数の値を同時に扱う。複数の値を処理できるだけ
でなく、複数の値を返すこともある。結果も配列になる。

* 配列式は計算式を一度評価し、配列のサイズと同じ回数だけ計算を実行するため、各セ
  ルの計算式を解釈する時間を節約できる。計算式自体の記憶領域節約にもなる。
* 配列として認識させるには :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`Enter` 押しで確定
  する。
* Function Wizard を使用して配列式を作成する場合は、結果が配列で返されるように
  :guilabel:`Array` を毎回オンにしろ。

Strategies for creating formulas and functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

スプレッドシートを自分以外が使用する場合は特に、どこでどのような入力が必要である
かを容易に理解するように示せ。表計算シートの目的、入出力仕様は最初のシートに記載
することが多い。

分割統治法に則れ。数式を部分に分解し、それらを組み立てるように構えろ。

大量データを捌くために配列式を使え。理由は先述。

``SUM``, ``SUMIF``, ``SUMIFS``, ``SUMPRODUCT``, etc., コレクションに作用する関数
を優先的に使え。

Finding and fixing errors
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

数式とその数式が参照しているセルを調べるため、エラーメッセージ、入力の色分け、検
出各機能が用意されている。

数式のエラーメッセージは、通常 501 から 540 までの数、あるいは ``#NAME?`` エラー
メッセージの場合はセルに表示され、エラーの簡単な説明がステータスバーの右側に示さ
れる。

入力の色分けというのは、数式中のセル参照や範囲参照の文字列色のことを指す。出力に
も色分けがあり、字の並びとしては同一でも、型が異なる場合（例：数値とテキスト）を
見分けるときに有用だ。

セル参照の連鎖をたどるには :menuselection:`&Tools --> &Detective -->` 各種コマン
ドを実行する。これで矢印がシート内に描かれる。

* 対象セルにカーソルを置き :kbd:`Shift` + (:kbd:`F9` or :kbd:`F5`) を押すのが早
  い
* 矢印の向きが気に入らない
* 矢印を消去するには :menuselection:`&Tools --> &Detective --> Remove All
  Traces` コマンドを実行

知的余裕があれば :menuselection:`&Tools > &Detective > Trace &Error` の使い方を
習得しろ。

Examples of functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

初心者は算術、統計に区分されている関数から学べ。

* 名前が ``A`` で終わる関数は、値がテキストである場合に特別な処理をする
* ``ROUND`` 関数は呼び出し有無の比較を検討すると安心だ

Volatile / non-volatile functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

   Functions that are *always* recalculated whenever a recalculation occurs are
   termed :dfn:`volatile` functions.

例えば乱数生成関数やタイムスタンプ関数は揮発性だ。

シートを明示的に再計算する方法は：

* :menuselection:`&Data --> Ca&lculate --> &Recalculate` コマンドを実行
* :kbd:`F9` を押す

Using wildcards and regular expressions in functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

関数には、その実引数に正規表現またはワイルドカードを使用可能であるものがある。具
体例：

* 名前が ``D`` から始まるデータベース関数
* 平均値、勘定関数、最大値、最小値、和を得る各関数
* 表探索関数
* 当然ながら検索・置換関数

MS Excel はこのような正規表現を扱っていない。Calc 文書を変換して提出するような状
況では使用を避けろ。

設定ダイアログ :menuselection:`LibreOffice Calc --> Calculate` ページに関連設定
項目がある：

* :guilabel:`Formula Wildcards` ではワイルドカードのみが有効になっている
* :guilabel:`General Calculate` 項目の一部が正規表現の関係する動作に影響する。

Advanced functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Calc 文書はユーザー定義関数またはアドインによって機能拡張可能だ。

ユーザー定義関数は、マクロ (Chater 13) を使用するか、個別のアドインや拡張機能を
記述することで設定可能。マクロは Basic, BeanShell, JavaScript, Python のいずれか
で記述される。

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
