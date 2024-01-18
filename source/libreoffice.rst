======================================================================
LibreOffice 利用ノート
======================================================================

本稿は LibreOffice_ の Calc と Writer に集中して理解、習得するべき項目を記録する
ものだ。

.. note::

   :Platform: Windows 10
   :Version: 7.6.4.1 x86_64

.. contents::

LibreOffice 関連資料
======================================================================

LibreOffice_
   本拠地ホームページ。プログラム本体だけでなく利用者手引も入手するべし。
`libreofficehelp.com <https://www.libreofficehelp.com/>`__
   ブログ構造のチュートリアルを少しずつ習得していくのがよい。

LibreOffice 共通
=====================================================================

個人的必修技法
----------------------------------------------------------------------

* LibreOffice のバージョン (:menuselection:`&Help --> &About LibreOffice`)
* オプションダイアログは :kbd:`Alt` + :kbd:`F12` で開く
* キーバインド確認方法 (:menuselection:`&Tools --> &Customize...`)
* UI をチュートリアル推奨様式に変更

以下、各アプリケーション個別設定になる。

* パスワード付与保存 (:menuselection:`&File --> Save &As...`)
* 既定雛形変更 (:menuselection:`&File --> Te&mplates --> &Manage Templates...`)

個人的設定オプション
----------------------------------------------------------------------

ほとんどの項目で既定値が良い。自分好みの値に変更するものと、既定値のままであって
も意識するべき構成を以下に記す。

* LibreOffice

  * General

    * Help

      * :guilabel:`&Extended tis` をオン
      * :guilabel:`Warn if local help is not installed` はオフ
      * :guilabel:`Show "Tip of the Day" dialog on start-up` をオン
    * Help Improve LibreOffice

      * :guilabel:`Sen&d crash reports to The Document Foundation` をオン
  * Security

    * Security Options and Warnings の :guilabel:`O&ptions...` ボタン

      * :guilabel:`&Remove personal information on saving` をオン
  * Online Update

    * Online Update Options

      * :guilabel:`&Check for updates automatically` は :guilabel:`Every da&y`
    * User Agent

      * :guilabel:`&Send OS version and basic hardware information` をオン
* Load/Save

  * Save

    * :guilabel:`Save &AutoRecovery information every` をオンにして何分でもいい
      から指定
    * :guilabel:`Al&ways create backup copy` をオフ
* Language Settings

  * Languages

    * Language Of

      * :guilabel:`&User interface` を :guilabel:`English (USA)` に

    * Formats

      * :guilabel:`Date acceptance &patterns` から自分が使わないものを除外する
  * Asian Layout については既定値よりも良い設定がある可能性がある

個人的必修キーバインド共通編
----------------------------------------------------------------------

Writer, Calc など、LibreOffice プログラム共通に通用するキーバインドのうち、常用
するものを以下に記す。Windows 標準のキーバインドは省略。便利なものを積極的に採り
入れろ。

キーバインドは :menuselection:`&Tools --> &Customize...` ダイアログの
:guilabel:`Keyboard` で確認可能。ただしこの UI は使いにくい。

.. csv-table::
   :delim: |
   :header: キーバインド,コマンド,動作
   :widths: auto

   :kbd:`Shift` + :kbd:`Esc` | Search Commands | コマンドパレットを開く
   :kbd:`Ctrl` + :kbd:`H` | Find and Replace | :guilabel:`Find and Replace` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`K` | Hyperlink | ハイパーリンクを定義する
   :kbd:`Ctrl` + :kbd:`Q` | Exit | うっかり押して終了しないように覚えておくこと
   :kbd:`Ctrl` + :kbd:`W` | Close Window | これも
   :kbd:`Ctrl` + :kbd:`Y` | Redo | Redo コマンドはキーバインドが二種類ある
   :kbd:`Ctrl` + :kbd:`Z` | Undo | Undo コマンドはこれのみ
   :kbd:`Ctrl` + :kbd:`F5` | Control Focus | ウィンドウ右柱に注目
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`N` | Templates | :guilabel:`Templates` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`S` | Save As | :guilabel:`Save As` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`Y` | Repeat | 直前の入力を反復する？
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`Z` | Redo | Redo コマンドはキーバインドが二種類ある
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`PageUp` | Zoom In | ウィンドウ主領域をズーム
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`PageDown` | Zoom Out | ウィンドウ主領域をズーム
   :kbd:`Alt` + :kbd:`1` | Open the Properties Deck | 画面右端のドックを開く
   :kbd:`Alt` + :kbd:`2` | Open the Styles Deck | 画面右端のドックを開く
   :kbd:`Alt` + :kbd:`4` | Open the Navigator Deck | 画面右端のドックを開く
   :kbd:`Alt` + :kbd:`F12` | Options | 設定ダイアログを表示
   :kbd:`Ctrl` + :kbd:`Alt` + :kbd:`C` | Comment | 付箋作成

Calc
======================================================================

個人的必修機能 Calc 編
----------------------------------------------------------------------

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
----------------------------------------------------------------------

* Chapter 1: 後回し

  * CSV ファイルのインポート方法。:guilabel:`Text Import` ダイアログで上手く指定
    する。
* Chapter 2

  * セル自動補完で候補が複数ある場合は :kbd:`→` で次候補が得られるかもしれない。
  * :menuselection:`&Sheet --> F&ill Cells --> Fill &Down`, etc.
  * :kbd:`Ctrl` + :kbd:`D`
  * :menuselection:`&Sheet --> F&ill Cells --> Fill S&eries...`
  * 連続データ自作方法はオプションダイアログの :menuselection:`LibreOffice Calc
    --> Sort Lists` を調べろ。
  * セルに同列項目からなるドロップダウンリストを表示 :kbd:`Alt` + :kbd:`↓`
  * 自動補完は使えないが :menuselection:`&Data --> F&orm...` というレコード追加
    機能がある。
  * 内容に基づくセル分割技法

    * コマンド :menuselection:`&Data --> Te&xt to Columns...` を使え。区切り文字
      に基づく文字列分割がもっとも自然かつ容易だ。
    * 文字列関数 ``MID``, ``LEFT``, ``RIGHT`` などと ``FIND`` を組み合わせて各部
      分を別のセルに出力することも可能だ。元のセルを損なわない。
  * セルに対して :menuselection:`&Data --> &Validity...` を使えば入力値に制約を
    定義できる。

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
    * 書式を取り消すなら :kbd:`BackSpace` 押しで :guilabel:`Delete Contents` ダ
      イアログを開け
  * 貼り付け

    * コマンド :menuselection:`Paste &Special` は :kbd:`Ctrl` + :kbd:`Shift` +
      :kbd:`V` で実行したい。
  * Calc でもフィールドが使える :menuselection:`&Insert --> Fiel&d`
  * グループ機能は使わない
  * フィルター機能

    * :menuselection:`&Data --> More &Filters --> &Standard Filter...` で絞り込
      みダイアログを開く
    * 自動フィルターは :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`L` でオンオフしろ
    * 自動フィルターダイアログでは色や条件指定で絞り込むことも可能
    * :menuselection:`&Data --> More &Filters --> &Advanced Filter...` は条件を
      どこかのセルから与える
  * ソートについては :menuselection:`&Data --> &Sort...` で指定ダイアログが開く
  * 検索と置換

    * :kbd:`Ctrl` + :kbd:`F` の検索バーは簡易版
    * :kbd:`Ctrl` + :kbd:`H` で :guilabel:`Find and Replace` ダイアログが開く
    * 正規表現を使える

個人的必修キーバインド Calc 編
----------------------------------------------------------------------

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

Writer
======================================================================

個人的必修機能 Writer 編
----------------------------------------------------------------------

* PDF 保存 (:menuselection:`&File --> &Export As --> &Export as PDF...`)
* 改頁挿入（原稿用紙上所望の位置で :kbd:`Ctrl` + :kbd:`Enter` を押す）
* ダミーテキスト挿入（原稿用紙上で ``df`` とタイプして :kbd:`F3` を押す）
* 自動保存オンオフ（オプションダイアログから）
* ヘッダーおよびフッター挿入 (:menuselection:`&Insert -> He&ader and Footer`)
* ヘッダーおよびフッター編集（当該箇所に専用メニューが現れる）
* ページ番号挿入 (:menuselection:`&Insert --> &Page Number`)
* TOC 作成 (:menuselection:`&Insert --> Table of contents and Inde&x --> Table
  of contents, &Index or Bibliography...`)

  * 章・節見出しを定義（書式設定による）

* 原稿用紙の縦長横長設定 (Orientation)
* 段落記号表示オンオフ (:kbd:`Ctrl` + :kbd:`F10` )
* ズーム（己の「ホーム倍率」設定のキーバインドを記憶しろ）
* 番号あり・なしリスト操作 (:kbd:`Shift` + :kbd:`F12`; :kbd:`F12`)
* ハイパーリンク (:kbd:`Ctrl` + :kbd:`K`)
* 画像挿入 (:menuselection:`&Insert --> &Image...` )
* 画像圧縮（画像上でコンテキストメニューを見ろ）
* 画像とテキストの配置制御（チュートリアルを繰り返し実習しろ）
* MRU ファイル一覧削除
* 行間設定 (:menuselection:`Format& --> &Spacing...`)

個人的必修キーバインド Writer 編
----------------------------------------------------------------------

.. csv-table::
   :delim: |
   :header: キーバインド,コマンド,動作
   :widths: auto

   :kbd:`F2` | Edit Formula | 数式編集欄を開く
   :kbd:`F3` | Run AutoText Entry | ノートで述べた
   :kbd:`F4` | Image Properties | :guilabel:`Image` ダイアログを開く
   :kbd:`F5` | Navigator | :guilabel:`Navigator` ダイアログを開く
   :kbd:`F8` | Select Cycle | 選択部分を徐々に拡張する
   :kbd:`F9` | Fields | フィールドを更新する
   :kbd:`F12` | Ordered List | ノートで述べた
   :kbd:`Shift` + :kbd:`F3` | Cycle Case | 英文編集でよくやる変換
   :kbd:`Shift` + :kbd:`F8` | MultiSelection On | 複数のテキスト選択を続ける
   :kbd:`Shift` + :kbd:`F11` | New | :guilabel:`New Style from Selection` ダイアログを開く
   :kbd:`Shift` + :kbd:`F12` | Unordered List | ノートで述べた
   :kbd:`Shift` + :kbd:`Enter` | Insert Manual Row Break | 改行挿入
   :kbd:`Ctrl` + :kbd:`0` | Body Text | 本文スタイル
   :kbd:`Ctrl` + :kbd:`1` | Heading 1 | 見出しスタイル
   :kbd:`Ctrl` + :kbd:`2` | Heading 2 | 見出しスタイル
   :kbd:`Ctrl` + :kbd:`3` | Heading 3 | 見出しスタイル
   :kbd:`Ctrl` + :kbd:`4` | Heading 4 | 見出しスタイル
   :kbd:`Ctrl` + :kbd:`5` | Heading 5 | 見出しスタイル
   :kbd:`Ctrl` + :kbd:`B` | Bold | 太字
   :kbd:`Ctrl` + :kbd:`D` | Double Underline | 二重下線
   :kbd:`Ctrl` + :kbd:`E` | Center | 中央揃え
   :kbd:`Ctrl` + :kbd:`G` | Go to Page | :guilabel:`Go to Page` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`I` | Italic | 斜体
   :kbd:`Ctrl` + :kbd:`J` | Justified | 両端（均等）揃え
   :kbd:`Ctrl` + :kbd:`L` | Left | 左揃え
   :kbd:`Ctrl` + :kbd:`R` | Right | 右揃え
   :kbd:`Ctrl` + :kbd:`U` | Underline | 下線
   :kbd:`Ctrl` + :kbd:`[` | Decrease | 文字サイズ調整
   :kbd:`Ctrl` + :kbd:`]` | Increase | 文字サイズ調整
   :kbd:`Ctrl` + :kbd:`F2` | More Fields | :guilabel:`Fields` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`F3` | AutoText | ノートで述べた
   :kbd:`Ctrl` + :kbd:`F8` | Field Shadings | フィールド部分の網掛けオンオフ切り替え
   :kbd:`Ctrl` + :kbd:`F9` | Field Names | DeepL とかぶるキーバインド
   :kbd:`Ctrl` + :kbd:`F10` | Formatting Marks | ノートで述べた
   :kbd:`Ctrl` + :kbd:`F12` | Table | Insert Table ダイアログを開く
   :kbd:`Ctrl` + :kbd:`↓` | To Next Paragraph | 次のパラグラフの先頭へジャンプ
   :kbd:`Ctrl` + :kbd:`↑` | To Paragraph Begin | 前のパラグラフの先頭へジャンプ
   :kbd:`Ctrl` + :kbd:`PageUp` | To Header | ヘッダーへジャンプ
   :kbd:`Ctrl` + :kbd:`PageDown` | To Footer | フッターへジャンプ
   :kbd:`Ctrl` + :kbd:`Enter` | Page Break | 改頁を挿入する
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`J` | Full Screen | 全画面表示切り替え
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`R` | Rulers | 定規表示切り替え
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`V` | Paste Special | :guilabel:`Paste Special` ダイアログを開く
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`F5` | Go to Page | もう一つのキーバインド
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`F8` | Block Area | 矩形選択モード切り替え
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`F12` | No List | リストを解除する
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`BackSpace` | Delete to Start of Sentence | キャレットから当該文末まで削除する
   :kbd:`Ctrl` + :kbd:`Shift` + :kbd:`Delete` | Delete to End of Sentence | キャレットから当該文頭まで削除する
   :kbd:`Alt` + :kbd:`5` | Open the Page Deck | ウィンドウ右ドックを開く
   :kbd:`Alt` + :kbd:`6` | Open the Style Inspector Deck | ウィンドウ右ドックを開く
   :kbd:`Alt` + :kbd:`PageUp` | To Begin of Previous Page | 前のページの先頭文字へジャンプ
   :kbd:`Alt` + :kbd:`PageDown` | To Begin of Next Page | 次のページの先頭文字へジャンプ
   :kbd:`Alt` + :kbd:`Shift` + :kbd:`F8` | Block Area | もう一つのキーバインド
   :kbd:`Alt` + :kbd:`Shift` + :kbd:`PageUp` | Select to Begin of Previous Page | これは使い物にならない
   :kbd:`Alt` + :kbd:`Shift` + :kbd:`PageDown` | Select to Begin of Next Page | キャレットから次ページの先頭文字まで選択する
   :kbd:`Ctrl` + :kbd:`Alt` + :kbd:`↓` | Move Item Down | 対象項目を下へずらす
   :kbd:`Ctrl` + :kbd:`Alt` + :kbd:`↑` | Move Item Up | 対象項目を上へずらす
   :kbd:`Ctrl` + :kbd:`Alt` + :kbd:`Shift` + :kbd:`V` | Paste Unformatted Text | 書式抜きでテキストを貼り付ける

.. _LibreOffice: https://www.libreoffice.org/
