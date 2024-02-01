======================================================================
Calc Guide Chapter 2 Entering and Editing Data ノート
======================================================================

.. contents::
   :local:

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
