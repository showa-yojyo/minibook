======================================================================
Writer Guide Chapter 18, Forms ノート
======================================================================

.. include:: ./abbrev.txt

.. contents:: 章見出し
   :depth: 3
   :local:

Introduction
======================================================================

この章では、Writer文書内での対話型フォームの使用について説明する。フォームには、編集されないセクションと、読者が変更できるように設計されたセクションがある。たとえば、アンケートには導入部と質問 (変更はできない) があり、読者が回答を入力したり、与えられた選択肢から選択したりするためのスペースがある。

Writer には、チェックボックス、オプションボタン、テキストボックス、プルダウン一覧など、フォームに情報を入力するためのいくつかの方法が用意されている。

LibreOffice のフォームには多くの機能がある。この章では、そのすべてを説明するわけではない。特筆すべきは、HTML 文書でのフォームの使用と、フォームコントロールにリンクするマクロの記述だ。

LibreOffice Calc、Impress、および Draw も、Writer とほぼ同様にフォームをサポートしている。

When to use forms
======================================================================

フォームには三つの使い方がある：

* 受信者が記入するための簡単な文書を作成する。例えば、アンケートを記入して返送するグループに送信する。
* データベースやデータソースにリンクし、使用者が情報を入力できるようにする。営業部門の誰かが、購入者の情報をフォームを使ってデータベースに入力する。
* データベースやデータソースにある情報を見ること。図書館員が本に関する情報を呼び出す。

データベースにアクセスするためにフォームを使用すると、複雑なグラフィカルフロントエンドを迅速かつ簡単に構築することができる。フォームには、データソースにリンクするフィールドだけでなく、テキスト、画像、テーブル、図面、その他の要素を含めることができる。

シンプルなフォームの典型的な使い方は以下の通りです：

#. フォームをデザインし、保存する。
#. そのフォームを他の人に送る（例えばEメールで）。
#. 他の人がフォームに記入し、保存してあなたに送り返す。
#. あなたがフォームを開き、その回答を見る。

.. tip::

   データソースを使ったり、ウェブ上で更新するフォームを設定したりすることで、データを自動的に収集することができる。しかし、これらの方法はより複雑なので、この章では扱いない。

Alternatives to using forms in Writer
----------------------------------------------------------------------

LibreOffice Base は、データソースにアクセスする別の方法を提供する。Base と Writer のフォームには多くの共通点があるが、特定のタスクにはどちらを使用したほうがよい場合もある。Base は、フォームがデータソースにアクセスする場合にのみ適している。

Creating a simple form
======================================================================

このトピックでは、データソースやデータベースへのリンクを持たず、高度なカスタマイズも行わないシンプルなフォームの作成方法を説明する。

Create a document
----------------------------------------------------------------------

フォームとして使用する文書を作成する際に特別なことをする必要はないが、コントロールを正確に配置できるようにグリッドを有効にするとよいだろう。メニューの「表示」＞「グリッドとヘルプライン」と進み、「グリッドを表示」を選択する。また、「グリッドにスナップ」を選択することもできる。

Create a new Writer document with File > New > Text document.

Open the form toolbars
----------------------------------------------------------------------

つのツールバーがフォームの作成をコントロールする：フォームコントロール（図2）とフォームデザイン（図3）だ。メニューの「表示」→「ツールバー」→「フォームコントロール」と「表示」→「ツールバー」→「フォームデザイン」を選択すると、両方が表示される。また、フォームコントロールツールバー上でフォームデザインツールバーを開くこともできる。

フォームコントロールツールバーには、よく使われるコントロールの種類ごとに図像がある。これらのコントロールのいくつかはフォームメニューにもある (図 1)。

これらのツールバーは、Writerウィンドウのさまざまな場所にドッキングすることも、フローティングのままにすることもできる。フローティングの場合、ツールバーを垂直から水平に変更したり、1列に並ぶツールの数を変更したりすることもできる。これらの変更を行うには、ツールバーの角をドラッグする。

これらのツールバーのツールの説明については、6 ページの「フォームコントロールのリファレンス」を参照しろ。

Activate design mode
----------------------------------------------------------------------

デザインモードをオンにするには、フォームコントロールツールバーのデザインモード図像をクリックする。(もう一度クリックするとオフになる。) これにより、フォーム・コントロールを挿入するための図像がアクティブになったり、非アクティブになったりし、編集用のコントロールが選択される。

デザインモードがオフの場合、フォームはエンド使用者と同じように動作する。ボタンを押したり、チェックボックスを選択したり、一覧項目を選択したりすることができる。

Insert form controls
----------------------------------------------------------------------

#. フォームコントロールを文書に挿入するには、コントロールの図像をクリックして選択する。マウスポインタの形が変わる。
#. コントロールを表示したい文書内の場所をクリックする。(後で移動できる）。
#. マウスの左ボタンを押したまま、コントロールをドラッグしてサイズを調整する。コントロールによっては、固定サイズのシンボルの後にコントロール名（チェックボックスやオプションボタンなど）が付いているものもある。
#. コントロールの図像はアクティブのままなので、ツールバーに戻ることなく、同じタイプのコントロールを複数挿入することができる。
#. 他のツールに変更するには、ツールバーの図像をクリックする。
#. コントロールの挿入を止めるには、フォームコントロールツールバーの選択図像 をクリックするか、挿入したコントロールのどれかをクリックする。マウスポインタは通常の表示に戻る。

.. tip::

   フォームコントロールを正方形にするには、Shiftキーを押しながら作成する。既存のコントロールの比率を同じにするには、Shiftキーを押しながらサイズを変更する。

Configure controls
----------------------------------------------------------------------

コントロールを挿入した後は、コントロールの外観や動作を設定する必要がある。文書内でフォームコントロールを右クリックし、コンテキストメニューからコントロールを選択するか、フォームコントロールをダブルクリックすると、選択したコントロールのプロパティダイアログボックスが開く。

プロパティダイアログボックスには三つのタブがある：一般」、「データ」、「イベント」だ。単純なフォームでは、「全般」タブだけが必要だ。詳細については、11 ページの「フォーム・コントロールの設定」、21 ページの「フォーム・コントロールの書式設定オプション」、およびヘルプの説明を参照しろ。データベースで使用するための設定については、17 ページの「データ入力用のフォームを作成する」で説明する。

このダイアログボックスのフィールドはコントロールのタイプによって異なる。追加フィールドを見るには、スクロールバーを使うか、ダイアログボックスを縦に拡大する。

Use the form
----------------------------------------------------------------------

フォームを使用するには、デザインモード図像をクリックしてデザインモードを解除する。フォーム文書を保存する。

Form controls reference
======================================================================

.. rubric:: Form menu on Menu bar

.. rubric:: Form Controls toolbar

Writerで表示される図像は、ここに表示されているものと異なる場合や、ツールバーの順序が異なる場合がある。

Table 1: Tools on Form Controls toolbar
Form Controls toolbar

1
Select
Selects a form control to perform some other action on it.
2
Design Mode
Toggles between design mode on (to edit forms) and design mode off (to use forms).
3
Toggle Form Control Wizards
Some form controls (List Box and Combo Box) have optional wizards. If you do not want the wizard to launch when you create one of these controls, use the Wizards On/Off icon to switch wizards off.
4
Form Design
Launches the Form Design toolbar, which can also be opened with View > Toolbars > Form Design.
5
Label
A text label. The difference between this and just typing on the page is that, as a control, you can link a label field to macros so, for example, something happens when the mouse passes over it or clicks on it.
6
Text Box
A control to create a box into which the form’s user can type any text.
7
Check Box
A box that can be selected or deselected on the form. You can label the box.
8
Option Button
Creates an option button (also known as a radio button). When multiple buttons are grouped together, only one can be selected at a time. The easiest way to group multiple buttons is to use the Group Box icon on the More Controls toolbar, with wizards enabled.
9
List Box
Creates a list of options as a pull-down menu that the user can choose from. If the form is linked to a data source and wizards are on, creating a list box launches the List Box Wizard.
If the form is not linked to a data source, turn wizards off and create an empty list box. Then in the List Entries field on the General tab, enter the options you want to appear on the list.
10
Combo Box
As with a List Box, you set up a list of choices. In addition, a panel at the top either displays the choice made or allows the form user to type in something else. This works the same as the List Box.
11
Push Button
Creates a button that can be linked to a macro. The label is the name that appears on the button.
12
Image Button
Behaves exactly like a push button, but displays as an image. Choose the image in the Graphics option on the General tab in the Control Properties dialog.
13
Formatted Field
A control allowing numeric formatting options. For example, you can set maximum and minimum values for the number entered, or the number type (decimal places, scientific, currency).
14
Date Field
Stores a date. You need to configure the earliest and latest dates the field will accept, the default date, and the date format. You can add a spinner.
15
Numerical Field
Displays a number. You need to specify formatting, maximum, minimum and default values. You can add a spinner.
16
Group Box
Group boxes have two uses. If wizards are on, creating a group box launches the Group Element wizard. This creates a group of options buttons (in which only one may be selected at a time). In most cases, using a group box is the best way to create a set of option buttons.
If wizards are off, a group box is simply a visual box to group together different controls. It has no effect on the way the controls operate.
17
Time Field
Works like a date field but specifies a time.
18
Currency Field
Works like a numeric field; additionally you can add a currency symbol.
19
Pattern Field
Useful when the form links into a data source. Specify an Edit Mask to restrict what a user can enter into the field. Specify a Literal Mask to restrict which data is displayed from the data source.
20
Table Control
Table controls are only useful with a data source. If no data source is specified, you will be prompted to choose one in the Table Element Wizard. You then pick the fields to display and, when design mode is off, the data appears in the table. The table also includes controls to step through the records.
Records can be added, deleted, and modified in the table.
21
Navigation Bar
A navigation bar is the same as the Form Navigation toolbar (View > Toolbars > Form Navigation), but can be placed anywhere in the document and be resized.
22
Image Control
Only useful when the form is connected to a data source and a field in the data source exists that can hold images. You can add new images to the database or retrieve and display images from it.
23
File Selection
Allows a user to select a file, either by typing the path and name directly or by clicking on a Browse button and choosing the file from a dialog.
24
Spin Button
Allows form users to choose a number by cycling through the list of numbers. You can specify maximum, minimum, default, and the step between numbers.
This control is not commonly used in Writer.
25
Scrollbar
Creates a scrollbar, with a number of options to define the exact appearance. This control is not commonly used in Writer.
Form Design toolbar

Table 2: Tools on Form Design toolbar
Form Design toolbar

1
Select anchor for object
Any form control can be anchored to page, paragraph, or character and also anchored as a character.
2
Align Objects
Disabled unless the control is anchored as a character. You can align a control in different ways, for example so the top or bottom of the control lines up with the top or bottom of the text.
3
Bring to Front
Places the control on top of any other controls or text.
4
Forward One
Brings the control one level up in the stack.
5
Back One
Sends the control one level down in the object stack.
6
Send to Back
Sends the control to the bottom of the stack.
7
To Foreground
Moves the object in front of the text.
8
To Background
Moves the object behind the text.
9
Select
Selects a form control to perform some other action on it.
 10
Design Mode
Toggles between design mode on (to edit forms) and design mode off (to use forms).
 11
Control Properties
Launches form control properties dialog. This dialog can be kept open whiles different controls are selected.
 12
Form Properties
Launches form properties dialog, which controls properties for the form as a whole, such as which data source it connects to.
 13
Form Navigator
Displays all the forms and controls in the current document and allows you to edit and delete them easily.
If you use the Form Navigator, give your controls names (in the properties dialog) so you can tell which is which in the navigator.
 14
Add Field
Useful only if you have specified a data source for the form. Otherwise, an empty box opens.
If you have specified a data source, Add Field opens a list of all the fields in the specified table, which you can then drag and drop onto the page. The fields are placed on the page with the name of the field before them.
 15
Activation Order
Allows you to specify the order in which focus shifts between controls. You can test the order by leaving design mode and using Tab to switch between the controls.
 16
Open in Design Mode
Opens the current form in design mode (to edit the form rather than entering data into it).
 17
Automatic Control Focus
If activated, focus is set to the first form control.
 18
Position and Size
Opens the Position and Size dialog, where you can type precise values, rather than dragging the control. You can also lock the size or position so they do not get changed accidentally. For some controls, you can rotate and set the slant and corner radius.
 19
Display Grid
Displays a grid of dots on the page, to help you line up controls.
 20
Snap to Grid
When a control is brought close to a grid point or line, it will snap to the grid. This makes it is easier to line up controls.
 21
Helplines While Moving
When a control is being moved, lines extend from the control horizontally and vertically to help you position it accurately.

Example: a simple form
======================================================================

この例では、図4のようなフォームを作成する。指定されたステップに従えば、このようなフォームになる。

Create the document
----------------------------------------------------------------------

新規文書を開き（ファイル＞新規＞テキスト・文書）、含めるテキストを入力する（例は図5参照）。後で簡単に変更できるが、フォームをデザインするときのガイドとして、最終的な結果をスケッチしておくとよいだろう。

Add form controls
----------------------------------------------------------------------

次のステップは、文書にフォーム・コントロールを追加することだ。つのコントロールを用意する：

* 名前はテキストボックスだ。
* 性別は、男性、女性、その他の三つのオプションボタンだ。
* 好きな形は、選択肢の一覧だ。
* あなたが好きなすべての形は、一連のチェックボックスだ。

これらのコントロールを追加するには

#. [ 表示 ] > [ ツールバー ] > [ フォームコントロール ] を選択して、 フォームコントロールツールバーを開く。
#. ツールがアクティブでない場合は、デザインモード図像をクリックしてアクティブにする。
#. [テキストボックス] 図像をクリックし、文書内をクリックして、[名前] テキストボックスの形をドラッグして希望のサイズに合わせます。Name: ラベルと一直線になるようにドラッグする。
#. Toggle Form Control Wizards がオフになっていることを確認する。オプションボタンの図像をクリックする。クリックしてドラッグし、文書のGender: ラベルの近くに三つのオプションボタンを作成する。これらは次のセクションで設定する。
#. 一覧ボックスの図像をクリックし、文書内のFavourite shape:のそばに一覧ボックスを描きます。これは今のところ単なる空のペインになる。
#. チェックボックスの図像をクリックし、「好きな図形すべて」によるチェックボックスを、ページをまたいで四つ並べて作成する。

これであなたの文書は図6のようになるはずだ。コントロールがうまく並んでいなくても心配するな。

Configure form controls
----------------------------------------------------------------------

Text box
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Nameフィールドにはこれ以上の設定は必要ないが、フィールドの高さや幅、背景色、その他の書式を変更したいかもしれない。その場合は

#. デザインモードがオンで、ウィザードがオフであることを確認する。
#. Name フィールドをダブルクリックして、Properties：テキストボックス］ダイアログボックスを開く（図7）。
#. [全般]タブで下にスクロールし（または下端を下にドラッグしてダイアログボックスを展開し）、[幅]と[高さ]のプロパティを見つけます。必要に応じてこれらを変更する。
#. ダイアログボックスを閉じるか、開いたままにして他のコントロールを設定する。

Option buttons
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Gender オプションボタンは、三つのうち一つだけを選択できるように設定する必要がある。これには、ここで説明するような個別のオプションボタンを使用する方法と、Group Box（14ページ参照）を使用する方法がある。

#. Design Mode がオンで、Wizards がオフであることを確認する。
#. Properties ダイアログボックスが開いている場合は、最初のオプションボタンを 1 回クリックして、ダイアログボックスを Properties に変更する：オプションボタンに変更する。ダイアログボックスが開いていない場合は、最初のオプションボタンをダブルクリックする。プロパティ」ダイアログボックス（図8）の「全般」タブで、「ラベル」フィールドに「男性」、「グループ名」フィールドに「性別」と入力する。
#. 他の二つのオプションも同様に、ラベルに「Female」、グループ名に「Gender」を使用する。(グループ化により、一度に選択できるオプションは一つだけです)。

オプションボタンが離れすぎている場合は、それぞれを順番にクリックし、左右にドラッグする。

オプションボタンがきれいに並んでいない場合は、このようにしろ：

#. フォームコントロールツールバーの［選択］ボタンをクリックし、マウスで三つのオプシ ョンボタンコントロールの周囲にボックスを描いて、すべてを選択する（図9）。
#. 右クリックして、コンテキスト・メニューから「整列 > 上部」を選択する。図10にその結果を示す。

List box
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

一覧ボックスに選択肢の一覧を追加するには、次のようにする：

#. デザインモードがオンで、ウィザードがオフであることを確認する。一覧ボックスコントロールをダブルクリックして、コントロールのプロパティダイアログボックスを開く（図11）。Generalタブを選択する。
#. スクロールダウンして List Entries テキスト入力ボックスを見つける。図形の名前（円、三角形、四角形、五角形）を一つずつ入力する。それぞれの後に、図11に示すように、Shift+Enterを押す。

   ダイアログボックスのList entriesボックスから離れてクリックすると、"Circle"; "Triangle"; "Square"; "Pentagon "という行が表示されるはずである（図12）。

Check boxes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

チェックボックスに名前を付けるには

#. デザインモードがオンで、ウィザードがオフであることを確認する。最初のチェックボックスコントロールをダブルクリックする。
#. プロパティダイアログボックスでProperties: Check Box ダイアログボックス（図 13）で、Label フィールドのテキストを Circle に変更し、Enter を押す。キャレットが次の行に移動し、文書のチェックボックスのラベルが直ちに変更される。
#. 他の三つのチェックボックスを順番にクリックする。プロパティダイアログボックスのラベルテキスト入力ボックスのテキストを、三角形、四角形、五角形に順番に変更する。
#. プロパティダイアログボックスを閉じる。
#. デザインモードをオフにする。

これで、10ページの図4のようなフォームが完成した。

Group box
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Gender 用に個別のオプションボタンを作成するのではなく（12 ページで解説）、Group Box を使ってオプションボタンのグループを挿入することもできる。グループボックスは、（16 ページの図 17 に示すように）選択項目を 1 つずつ積み重ねますが、個々のボタンは好きな配置に移動させることができる（12 ページでは水平に配置した）。

個々のオプション・ボタンの代わりにグループ・ボックスを使うには：

#. デザインモードとウィザードの両方がオンになっていることを確認する。Group Box 図像をクリックし、Gender: ラベルの横にボックスを描きます。グループ要素ウィザード（図14）が自動的に開く。
#. 左のボックスに「Male」と入力する。ボタンをクリックして、右側の Option fields ボックスに移動する。
#. FemaleとOtherも同様に入力する。ウィザードは図15のようになる。Next > をクリックする。
#. ウィザードの次のページ（図16）で、「No, one particular field is not going to be selected as default」を選択する。Next＞をクリックする。
#. 次のページでは、何も変更しない。次へ」をクリックする。
#. 次のページで、キャプション領域から「Group Box」の文字を削除する。フォームに「Gender:」ラベルがすでにない場合は、キャプションに「Gender」と入力するとよいだろう。
#. 完了をクリックする。アンケートフォームは図 17 のようになる。

Finishing touches
----------------------------------------------------------------------

フォームは完成しているが、文書にさらに変更を加えたいと思うかもしれない。これを他の人に送信して記入してもらうつもりなら、おそらく文書を読み取り専用にして、使用者がフォームに記入することはできても、文書に他の変更を加えることができないようにしたいだろう。

文書を読み取り専用にするには、[ファイル] > [プロパティ] を選択し、[セキュリティー] タブを選択して [ファイルを読み取り専用で開く] を有効にする。

.. note::

   文書が読み取り専用の場合、フォームに記入する人は、「ファイル」＞「名前を付けて保存」で文書を保存する必要がある。

Accessing data sources
======================================================================

フォームの最も一般的な用途は、データベースに情報を入力することだ。例えば、他の人が連絡先データベースに情報を入力するためのフォームをデザインすることができる。フォームはWriter文書の一部なので、画像、書式、表、その他の要素を含めることができ、思い通りの外観にすることができる。フォームの変更は、文書の編集と同じくらい簡単だ。

LibreOffice は多数のデータソースにアクセスできる。ODBC、MySQL、Oracle JDBC、スプレッドシート、テキストファイルなどだ。原則として、データベースは読み書きのためにアクセスできるが、その他のデータソース (スプレッドシートなど) は読み取り専用だ。

.. tip::

   ご使用のOSでサポートされているデータ・ソース・タイプの一覧を表示するには、[ファイル] > [新規作成] > [データベース]を選択する。データベース・ウィザードの最初のページで、「既存のデータベースに接続する」を選択し、ドロップダウン一覧を開く。

この章では、データベースまたはその他のデータソースを作成し、Writer で使用するために登録したものとする。第14章メールマージでは、データベースの作成と登録方法について説明する。

Creating a form for data entry
----------------------------------------------------------------------

データベースが LibreOffice に登録されたら、次の手順に従ってフォームをデータソースにリンクする：

#. Writer で新規文書を作成する (ファイル > 新規 > テキスト文書)。
#. 実際のフィールドを入れずにフォームをデザインする (後でいつでも変更できる)。
#. フォームコントロールとフォームデザインツールバーを表示する。
#. デザインモード図像をクリックして、文書をデザインモードにする。
#. テキストボックスの図像をクリックする。文書内をクリックしてドラッグし、最初のフォームフィールド用のテキストボックスを作成する。
#. 任意のタイプのフィールドを、同じ方法（クリックしてドラッグ）で追加できる。

ここまでは、最初のフォームを作成したときと同じ手順を踏んでいる。登録したデータソースとフォームをリンクするには、次のようにする：

#. フォームデザインツールバーの［フォームプロパティ］図像をクリックするか、 挿入したフィールドのいずれかを右クリックして［フォームプロパティ］を選択 し、［フォームプロパティ］ダイアログボックスを開く (図 18)。
#. ［フォーム・プロパティ］ダイアログボックスで、［データ］タブを選択する。

   * データ・ソースを登録したデータ・ソースに設定する。
   * 中身・タイプをテーブルに設定する。
   * アクセスしたいテーブル名を中身に設定する。
   * ダイアログボックスを閉じる。
#. 各フォームコントロールを順番にクリックして選択し（周囲に小さな緑色のボックスが表示される）、プロパティダイアログボックスを起動する：右クリックしてコントロールプロパティを選択するか、フォームコントロールツールバーのコントロールプロパティ図像をクリックする。
#. プロパティダイアログボックスで、データタブをクリックする（図 19）。フォームを正しくセットアップしていれば、データ・フィールド・オプションにデータ・ソース の異なるフィールド（例えば、名前、住所、電話番号）の一覧が表示される。必要なフィールドを選択する。
#. フィールドに割り当てるべきコントロールがすべて割り当てられるまで、各コントロールを 順番に繰り返する。

.. caution::

   LibreOffice Base でデータベースを作成し、主キーフィールドの AutoValue を Yes に設定した場合、そのフィールドはフォームの一部である必要はない。AutoValue が No に設定されている場合、そのフィールドを含める必要があり、使用者は新規入力のたびにそのフィールドに一意の値を入力する必要がある。

Entering data into a form
----------------------------------------------------------------------

フォームを作成し、データベースと結びつけたら、そのフォームを使ってデータベースにデータを入力したり、すでにあるデータを修正したりする：

#. フォームがデザインモードでないことを確認する。(フォームコントロールツールバーのデザインモード図像をクリックする。デザインモードがオフの場合、ツールバーのほとんどのボタンは灰色で表示される)。
#. フォームナビゲーションツールバーがオンになっていることを確認する (表示 > ツールバー > フォームナビゲーション)。このツールバーは通常、ワークスペースの一番下に表示される。
#. データソースに既存のデータがある場合は、フォームナビゲーションツールバー のコントロールボタンを使用して、さまざまなレコードを参照する。レコードのデータを修正するには、フォームの値を編集する。変更を送信するには、最後のフィールドにキャレットがある状態で Enter キーを押する。レコードが保存され、次のレコードが表示される。
#. フォームにデータがない場合は、フォームのフィールドに入力して情報を入力する。新しいレコードを送信するには、最後のフィールドにキャレットがある状態で Enter キーを押す。
#. フォームナビゲーションツールバーから、レコードの削除や新規レコードの追加など、その他の機能を実行できる。

.. note::

   ユーザがフォームに入力しようとして、"Attempt to insert null into a non-nullable column" というエラーが表示された場合、フォーム設計者はデータベースに戻り、主キー・フィールドに Auto Value が Yes に設定されていることを確認する必要がある。このエラーにより、フォーム・ユーザはレコードを保存できなくなる。

Advanced form customization
======================================================================

Linking a macro to a form control
----------------------------------------------------------------------

任意のフォーム・コントロール（例えば、テキスト・ボックスやボタン）に、何らかのイベントがトリガーされたときにアクションを実行するように設定することができる。

マクロをイベントに割り当てるには

#. マクロを作成する。入門ガイド』の第 13 章「マクロを始める」を参照しろ。
#. フォームがデザインモードであることを確認する。フォームコントロールを右クリックし、コンテキストメニューから「コントロールプロパティ」 を選択し、「イベント」タブをクリックする（図 21）。
#. イベントの横のブラウズ図像をクリックして、アクションの割り当て ダイアログボックスを開く（図 22）。
#. マクロボタンをクリックし、マクロ選択ダイアログボックス（図示せず）の一覧からマクロ を選択する。Assign action ダイアログボックスに戻る。必要に応じてこれを繰り返し、OK をクリックしてダイアログボックスを閉じる。

マクロは、フォーム全体に関するイベントに割り当てることもできる。これを行うには、文書内のフォームコントロールを右クリックし、「フォームのプロパティ」を選択し、「イベント」タブをクリックする。

Fine-tuning database access permissions
----------------------------------------------------------------------

既定では、フォームからデータベースにアクセスすると、レコードの追加、削除、修正など、あらゆる変更が可能になる。レコードの追加、削除、修正が可能だ。例えば、使用者は新しいレコードを追加することしかできないようにしたり、既存のレコードを削除することを禁止したりすることができる。

デザイン・モードでフォーム・コントロールを右クリックし、コンテキスト・メニューから Form Properties を選択する。フォーム・プロパティ・ダイアログボックス（図23）のデータ・タブで、以下の各オプションを「はい」または「いいえ」に設定し、使用者のデータ・ソースへのアクセスを制御する：追加を許可する」、「削除を許可する」、「変更を許可する」、「データの追加のみ許可する」。

個々のフィールドを保護することもできる。これは、品目の説明が固定で数量が変更可能な在庫一覧のように、使用者がレコードの一部を変更でき、他の部分のみを表示できるようにしたい場合に便利だ。

個々のフィールドを読み取り専用にするには、デザインモードで、文書内のフォームコントロールを右クリックし、コンテキストメニューからコントロールを選択する。Generalタブを選択し、Read-onlyをYesに設定する。

Form control formatting options
----------------------------------------------------------------------

フォーム・コントロールの外観や動作は、さまざまな方法でカスタマイズできる。これらはすべてデザイン・モードで行いる。フォームコントロールを右クリックし、コンテキストメニューからコントロールのプロパティを選択し、プロパティダイアログボックスの全般タブを選択する。

* ラベル・ボックス（ラベル・フィールドと呼ばれるボックスと混同しないように）にコントロールのラベルを設定する。プッシュ・ボタンやオプション・ボタンなどのいくつかのフォーム・コントロールには、設定可能な可視ラベルがある。また、テキストボックスのように、ラベルを設定できないものもある。
* 印刷オプションで文書を印刷する場合、フォームコントロールが印刷されるかどうかを設定する。
* Font設定を使用して、フィールドのラベルまたはフィールドに入力されたテキストのフォント、書体、サイズを設定する。この設定は、チェック・ボックスやオプション・ボタンのサイズには影響しない。
* テキスト・ボックスでは、テキストの最大長を設定できる。これは、データベースにレコードを追加するときに非常に便利だ。すべてのデータベースのテキストフィールドには最大長が設定されており、入力されたデータが長すぎる場合、LibreOffice はエラーメッセージを表示する。フォームコントロールの最大テキスト長をデータベースフィールドの最大テキスト長と同じに設定することで、このエラーを回避できる。
* フォーム・コントロールの既定・オプションを設定することができる。既定では、コントロールは空白、またはすべてのオプションが選択されていない状態だ。特定のオプションや一覧項目が選択された状態でコントロールを開始するように設定することができる。
* パスワードが入力されるコントロールの場合、パスワード文字（たとえば*）を設定すると、その文字だけが表示され、使用者が実際に入力した内容は保存される。

  * フォームコントロールに追加情報やヘルプテキストを追加することができる。
  * コントロールの表示方法をさらに定義するために、背景色、立体的な外観、テキストフォーマット、スクロールバー、境界線などの他のフォーマットコントロールを使用することができる。

Using content controls
======================================================================

中身・コントロールはプレースホルダーだ。雛形、フォーム、文書で使用するために、中身・コントロールを追加したりカスタマイズしたりすることができる。中身・コントロールには、その使用方法を示すことができる。この章で前述したコントロールと似ているものもあるが、作業や書式設定がより簡単になる。ただし、いくつかのフィールドとは異なり、中身・コントロールはデータベース内のデータには接続しない。

Rich Text
   カスタムフォーマットされたテキストや、表、画像、その他の中身コントロールなどのアイテムが含まれる。
Plain Text
   単一または複数の段落のプレーンテキストに限られる。リッチテキストとは異なり、表、画像、その他の中身コントロールなどの他のアイテムを含めることはできない。
Picture
   文字として固定された画像を一つ含む。中身・コントロールをクリックするとファイルを開くダイアログボックスが開き、プレースホルダーを置き換える画像を選択できる。
Check Box
   対話するためのチェックボックス文字が一つ含まれている。中身コントロールをクリックすると、チェックボックスのチェック状態が切り替わります。
Combo Box
   選択可能な一覧項目のドロップダウン選択と、直接編集可能なテキストボックスを含む。
Drop-down List
   表示テキストと値のペアの一覧を持つドロップダウンボタンコントロールが含まれている。コンボボックスとは異なり、ドロップダウン一覧は、使用者がカスタム入力を入力することはできない。
Date
   カレンダーコントロールを含む。テキストを1段落に制限する。

文書、雛形、またはフォームに中身コントロールを挿入するには

#. コントロールを表示したい場所にキャレットを置く。
#. メニューの［フォーム］→［中身コントロール］→［必須コントロール］の順に選択する。
#. メニューの [ フォーム ] > [ 中身コントロール ] > [ 中身コントロールのプロパティ ] を選択する。これはピクチャコントロールでは使用できない。
#. 「中身コントロールのプロパティ」ダイアログボックス（図 24）で、オプションで 「中身はプレースホルダテキスト」を選択し、表題とタグを入力する。プロパティはコントロールごとに異なる。詳細はヘルプを参照しろ。
