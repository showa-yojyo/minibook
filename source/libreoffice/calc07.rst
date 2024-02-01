======================================================================
Calc Guide Chapter 7 Printing, Exporting, Emailing, and Signing ノート
======================================================================

.. contents::
   :local:

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
