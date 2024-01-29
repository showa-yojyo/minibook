Chapter 10 Data Analysis
======================================================================

Introduction
----------------------------------------------------------------------

関連機能はメインメニュー :menuselection:`&Data` と :menuselection:`&Tools` に分
散している。

Consolidating data
----------------------------------------------------------------------

複数のシートに散在しているデータを結合して集計する機能として
:menuselection:`&Data --> &Consolidate...` コマンドがある。これを実行すると
:guilabel:`Consolidate` ダイアログが開く。この使い方が自力ではわからない。

* :guilabel:`&Function` ドロップダウンリストから所望の集計関数を指定する。
* :guilabel:`&Source data ranges` 欄を指定する。それから :guilabel:`Add` ボタン
  を押して選択範囲を :guilabel:`Consolidation ranges` 一覧に追加する。この追加処
  理を所望の範囲をカバーするまで反復する。
* :guilabel:`Copy results &to` 欄を指定する。

:guilabel:`OK` を押して処理を実行する。指定した場所にある値を集計関数に入力とし
て渡して評価し、指定した場所に出力する。

Consolidation settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ダイアログ上のプラスマークをクリックすると、詳細オプション項目群が現れる。

ラベル系オプションは選択範囲それぞれの最初の列や最初の行がフィールドである場合、
かつそれらがすべて一致している場合にはオンにするのが自然だろう。

:guilabel:`&Link to source data` をオンにすると、:guilabel:`&Source data ranges`
の値が変化すると :guilabel:`Copy results &to` の値も自動的に更新される。

Consolidation example
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ガイド本文のデータを手で再現して Consolidation コマンドの動作を体で理解しろ。

   The source ranges and target range are saved as part of the document. If you
   later open a document with consolidated ranges, they will still be available
   in the Consolidation ranges list of the Consolidate dialog.

Creating subtotals
----------------------------------------------------------------------

小計を得る方法は二つだ：

* ``SUBTOTAL`` 関数
* :menuselection:`&Data --> Sub&totals...` コマンド

Using the ``SUBTOTAL`` function
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``SUBTOTAL`` 関数は Function Wizard の数学区分とサイドバーの関数デッキの下に一覧
されている。本関数はわずかな区分だけで使用する場合に効果的だ。

The Subtotals tool
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using scenarios
----------------------------------------------------------------------

Using the Multiple Operations tool
----------------------------------------------------------------------

Using Goal Seek
----------------------------------------------------------------------

Using the Solver
----------------------------------------------------------------------
