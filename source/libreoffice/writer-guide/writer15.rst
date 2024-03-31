======================================================================
Writer Guide Chapter 15, Tables of Contents, Indexes, Bibliographies ノート
======================================================================

.. include:: ./abbrev.txt

.. contents:: 章見出し
   :depth: 3
   :local:

Introduction
======================================================================

This chapter describes how to create and maintain a table of contents, an index, and a bibliography for a text document using LibreOffice Writer. Other types of index are mentioned briefly. To understand the instructions, you need a basic familiarity with Writer and styles (see Chapter 8, Introduction to Styles, and Chapter 9, Working with Styles).

Tables of contents
======================================================================

Writer’s table of contents (TOC) feature lets you build an automated TOC from the headings in a document. Whenever changes are made to the text of a heading in the body of the document or the page on which the heading appears, those changes automatically appear in the table of contents when it is updated.
Before you start, make sure that the headings are styled consistently. For example, you can use the Heading 1 style for chapter titles and the Heading 2 and Heading 3 styles for chapter subheadings.
This section shows you how to:
    • Create a table of contents quickly, using the defaults.
    • Customize a table of contents.
    • Note
You can use any style you want for the different levels to appear in the TOC; the examples in this chapter uses the default Heading styles. You can specify other paragraph styles to appear in the TOC, as described in “Create From” on page 7.
    • Tips
If some of your headings do not show up in the table of contents, check that the headings have been tagged with the correct paragraph style. If a whole level of headings does not show up, check the settings in Tools > Heading Numbering. See Chapter 8, Introduction to Styles.
If you add or delete text (so that headings move to different pages) or you add, delete, or change headings, you need to update the table of contents. To do this: Right-click anywhere in the TOC and select Update Index in the context menu.
If you cannot place the cursor in the TOC, choose Tools > Options > LibreOffice Writer > Formatting Aids, and then select Enable cursor in the Protected Areas section.
The TOC appears with a gray background. This background is there to remind you that the TOC is a field; the text you see is generated automatically. The background is not printed and does not appear if the document is converted to a PDF. To turn off this gray background, go to Tools > Options > LibreOffice > Application Colors, then scroll down to the Text Document section and deselect Index and table shadings.
This change may leave a gray background showing behind the dots between the headings and the page numbers, because the dots are part of a tab. To turn that shading off, go to Tools > Options > LibreOffice Writer > Formatting Aids and deselect the option for Tabs in the Display formatting section.

Creating a table of contents quickly
----------------------------------------------------------------------

Most of the time you will find the default table of contents to be all you need, although the formatting may be inelegant. To insert a default TOC:
    1) Create a document, using the following paragraph styles for different heading levels (such as chapter and section headings): Heading 1, Heading 2, and Heading 3. These are what will appear in the TOC. Writer can evaluate up to ten levels of headings.
    2) Click in the document where you want the TOC to appear.
    3) Choose Insert > Table of Contents and Index > Table of Contents, Index or Bibliography.
    4) Click OK. The result will be a typical table of contents with the entries generated as hyperlinks.
    • Caution
If you have Edit > Track Changes > Show enabled when editing a document and you update the TOC, then errors may occur, as the TOC will still include any deleted headings and deleted text may cause page numbering in the TOC to be wrong. To avoid this problem, be sure this option is deselected before updating a TOC.

Customizing a table of contents
----------------------------------------------------------------------

The table of contents can be customized to suit the style and requirements of the document.
To start, right-click anywhere in an existing table of contents and choose Edit Index in the context menu, or click in the document where the TOC should appear and choose Insert > Table of Contents and Index > Table of Contents, Index or Bibliography, to open the Table of Contents, Index or Bibliography dialog shown in Figure 1.

The Table of Contents, Index or Bibliography dialog has five tabs. Each tab covers a different aspect of the TOC structure and appearance:
    • Type tab: set the attributes of the TOC.
    • Entries and Styles tabs: format the entries in the TOC.
    • Columns tab: put the TOC into more than one column.
    • Background tab: add color or an image to the background of the TOC.
To display a preview box, located on the right-hand side of the dialog, select the Preview option in the lower left of the dialog. The illustrations in this chapter show the dialog as it appears with the preview box hidden.
    • Note
The preview box shows the result of settings made on the Type, Entries, and Styles tabs. It does not show changes made on the Columns and Background tabs.
After making all the changes, click OK to apply them. To revert to the default settings for the Columns and Background tabs, select each tab in turn and click the Reset button. The settings on the Type, Entries, and Styles tabs must be reset manually; the Reset button has no effect.

Type tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Type tab (Figure 1) to set the attributes of the Table of Contens.
Title
To give the table of contents a different title, type it in the Title field. To delete the title, clear the Title field.
Type
Select a type in the drop-down list. For a TOC, be sure the Type is set to Table of Contents. See “Alphabetic indexes” on page 12 and “Other types of index” on page 20 for more about creating other types of indexes.
    • Note
You can change the type of index only when you first create it. Once you define an index type (for example, a table of contents) you cannot change it.
Protected against manual changes
By default, to prevent the TOC from being changed accidentally, this option is selected; the TOC can only be changed by using the context menu or the dialog. If the option is not selected, the TOC can be changed directly, just like other text. However, any manual changes will be lost when the TOC is updated, so they should be avoided.
Create Index or Table of Contents
In the For drop-down list in this area, you can select whether the TOC will cover all the headings of the document (Entire document) or just the headings of the chapter where it is inserted. In early versions of LibreOffice, the heading level designating a chapter was fixed; from version 7.4, it is the current heading level.
Evaluate up to level
Writer can use up to 10 levels of headings when it builds the table of contents. To specify the number of levels included, enter the required number in the Evaluate up to level box.
Create From
The third section of the Type tab determines what Writer should use to create the TOC. The choices (not mutually exclusive) are Headings, Additional styles, and Index marks.
Headings
By default, Writer uses the paragraphs formatted with the paragraph styles associated with heading levels in Tools > Heading Numbering.
You can change the paragraph styles used for heading levels, and you can include other paragraph styles by assigning an outline level to those styles. Both of these methods are described in in Chapter 8, Introduction to Styles.
Additional styles
You can add more paragraph styles to the TOC. This can be useful, for example, when you want to include the heading of an annex (appendix) in the TOC. If the Headings option is also selected, the additional styles will be included in the table of contents together with the ones defined in the heading numbering. Select this option and click the Assign styles button to open the Assign Styles dialog (FIgure 2).

Index marks
This selection adds any index entries inserted into the document by using Insert > Table of Contents and Index > Index Entry. Normally you would not use this selection for a table of contents. However, if you select Table of Contents in the Index drop-down list at the top of the Insert Index Entry dialog (Figure 3), Writer will distinguish between them and any index entries intended for inclusion in an alphabetic or other index.

Entries tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Entries tab (Figure 4) to define and format the entries in the TOC. Each level can be styled independently from the other levels by adding and deleting elements.

Click a number in the Level column. The Structure line contains the elements included in the entries for that level. Elements that can be added to the structure line are displayed just below the structure line, and are grayed out if they cannot be included (usually because they are already in use):
    • The LS icon represents the start of a hyperlink.
    • The N# icon represents the heading number assigned to a heading style in Tools > Heading Numbering. See Chapter 8, Introduction to Styles.
    • The E icon represents the heading text; that is, the text formatted with the paragraph style used for each level.
    • The T icon represents a tab stop.
    • The # icon represents the page number.
    • The LE icon represents the end of a hyperlink.
    • Each white field on the Structure line represents a blank space where you can add custom text or another element.
    • Note
In the Heading Numbering dialog (see Chapter 8, Introduction to Styles), if you have included any text in the Before or After boxes in the Separator section for any given level, then that text will be part of the N# field for that level. Take care when building the structure line not to create any unwanted effects in the appearance of the TOC.

Adding elements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To add an element to the Structure line:
    1) Click in the white field where you want to insert the element.
    2) Click one of the active buttons just below the Structure line. For example, to add a tab, click the Tab Stop button. An icon representing the new element appears on the Structure line.
    3) To add custom text, such as the word Chapter, type the text in the white field. Don't forget a trailing space.

Changing elements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To change an element in the Structure line, click the icon representing that element and then click a non-grayed out element in the row of buttons just below the Structure line. For example, to change a chapter number to a tab stop, click the N# icon on the Structure line (it shows then as being pressed) and then click the Tab Stop button in the row of available elements. To cancel before changing an element, click in one of the white spaces.
Applying changes to all levels
If you wish to apply the same structure and formatting to all levels, click the All button on the right.

Deleting elements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To delete an element from the Structure line, click the button representing that element and then press the Delete key on your keyboard. For example, to delete the default hyperlink setting, click the LS icon and then press the Delete key. Repeat this for the LE icon.

Applying character styles
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You might want an element to be a bit different from the rest of the line. For example, you might want the page number to be bold. To apply a character style to an element:
    1) Be sure you have previously defined a suitable character style.
    2) On the Structure line, click the button representing the element to which you want to apply a style.
    3) In the Character Style drop-down list, select the desired style.
To view or edit the attributes of a character style, select the style in the Character Style drop-down list and then click the Edit button.
    • Tip
The default character style for hyperlinks (such as those inserted by Insert > Hyperlink) is Internet Link, which by default is underlined and shown in blue.
The default hyperlinks of TOC entries are set to the Index Link character style, which may be different in appearance from the Internet Link style. If you want them to appear the same as internet links, you can select the LS icon on the Structure line and change the character style selection for TOC entries to Internet Link.
Alternatively, you can change the attributes for Index Link.

Tab parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Click on the Tab stop icon on the Structure line to bring up these controls:
    • Fill character: select the tab character you wish to use; the first choice is none (blank).
    • Tab stop position: specify the distance to leave between the left page margin and the tab stop. Optionally, select Align right for the tab stop; this selection inactivates the distance.

Tab position relative to paragraph style indent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When this option is selected, entries are indented according to the settings of their individual formats. Where a paragraph style specifies an indent on the left, tab stops are relative to this indent. If this option is not selected, tab stops are relative to the left margin position.

Styles tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Styles tab (Figure 5) to change which paragraph style is assigned to display the text of each level in the table of contents. In most cases, the best strategy is to keep the assigned styles but change their settings as needed to make the TOC appear the way you want.
To apply a custom paragraph style to an outline level:
    1) In the Levels list, select the level.
    2) In the Paragraph Styles list, click on the desired paragraph style.
    3) Click the < button to apply the selected paragraph style to the selected outline level.
The style assigned to each level appears in square brackets in the Levels list.
To remove paragraph styling from an outline level, select the outline level in the Levels list, and then click the Default button.
To view or edit the attributes of a paragraph style, click the style in the Paragraph Styles list, and then click the Edit button.

Columns tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Columns tab to change the number of columns for the TOC. Multiple columns are more likely to be used in an index than in a TOC, so this tab is described in the section on indexes. See Figure 10.

Background tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Background tab (Figure 6) to add color or an image to the background of the TOC. See Chapter 6, Formatting Pages: Advanced, for more about adding a background.

Adding color
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To add color to the background of the table of contents, select the Color button near the top of the dialog, then select a color from those provided and click OK.
See Chapter 20, Customizing Writer, for information about defining custom background colors.

Adding an image
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To add an image to the background of the table of contents, select the Image button. The Background tab now displays the image options.

Deleting a color or an image
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To delete a color or an image from the table background, select None at the top of the dialog.

Editing a table of contents
----------------------------------------------------------------------

To edit an existing TOC, right-click anywhere in the TOC and choose Edit Index in the context menu. You can also open the Navigator in the Sidebar, click the expansion symbol (+ sign or triangle) next to Indexes, then double-click on Table of Contents.
The Table of Contents, Index or Bibliography dialog (Figure 1 on page 6) opens. You can edit and save the TOC as described in the previous section.

Updating a table of contents
----------------------------------------------------------------------

Writer does not update the TOC automatically, so after any changes to the headings in a document, you need to update the TOC manually. Right-click anywhere in the TOC; in the context menu, choose Update Index.
You can also update the index from the Navigator: expand Indexes, right-click on the name of table of contents you want to update, and choose Index > Update.

Deleting a table of contents
----------------------------------------------------------------------

To delete the TOC from a document, right-click anywhere in the TOC and choose Delete Index in the context menu. You can also delete the index from the Navigator by choosing Index > Delete in the menu shown in Figure Error: Reference source not found. Writer will not prompt you to confirm the deletion.

Alphabetic indexes
======================================================================

An alphabetical index is a list of keywords or phrases used throughout a document that, if listed in order with page numbers, may help the reader find information quickly. Generally an index is found in the back of a book or document.
This section describes how to:
    • Add index entries manually.
    • Use a concordance file.
    • Create an alphabetic index quickly.
    • Customize the display of index entries.
    • Customize the appearance of the index.
    • View and edit existing index entries.

Adding index entries
----------------------------------------------------------------------

Before you can create an index, you must create some index entries, either manually or by using a concordance (see page 14). To create index entries manually:
    1) To add a word to the index, place the cursor anywhere in that word. To add multiple consecutive words as one entry, select the entire phrase.
    2) Choose Insert > Table of Contents and Index > Index Entry, or click the Insert Index Entry icon on the Insert toolbar, to display a dialog similar to the one in Figure 7. When the dialog opens, the selected text appears in the Entry box. You can accept the word or phrase shown, or change it to whatever you want.
    3) Click Insert to create the entry.

    • Tip
A cursor placed immediately before the first character of a word, or immediately after the last character of a word if it is followed by a space, counts as being in that word.
You can create multiple entries without closing the dialog. For each one:
    1) Click at the location in the document that you want to index.
    2) Click again on the dialog.
    3) Change the entry if needed, and click Insert.
    4) Repeat steps 1–3 until you have finished with the entries, then click Close.
Below is a brief explanation of the fields in the Insert Index Entry dialog and how to use them.
Index
The type of index this entry is for. The default is Alphabetical Index, but you can use this field to create extra entries for a table of contents or user-defined indexes or lists of almost anything. For example, you might want an index containing only the scientific names of species mentioned in the text, and a separate index containing only the common names of species. See “Other types of index” on page 20.
Entry
The word or phrase to be added to the selected index. This word or phrase does not need to be in the document itself; you can add synonyms and other terms that you want to appear in the index.
1st key
An index key is an entry that has no associated page number and has several subentries that do have page numbers. Using keys is a useful way of grouping related topics. (See “Example of using an index key” on page 14.)
2nd key
You can have up to a three-level index, where some of the first-level keys have level-2 entries that are also keys (without page numbers). This degree of index complexity is not often necessary.
Main entry
When the same term is indexed on several pages, often one of those pages has more important or detailed information on that topic, so you want it to be the main entry. To make the page number for the main, or most important, entry stand out, select this option and then define the character style for the page number of a main index entry to be bold, for example.
Apply to all similar texts
Select this option to have Writer automatically identify and mark any other word or phrase that matches the current selection. The Match case and Whole words only options become available if this option is selected. Use this option with care, as it may result in many unwanted page numbers (for minor uses of a word) being listed in the index.

Example of using an index key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

An index key is a primary entry under which subentries are grouped. For example, you might want to create a grouping similar to this:
LibreOffice
      Calc,  10
      Impress,  15
      Writer,  5
In this example, LibreOffice is the 1st key. The subentries (with the page numbers showing) are the indexed entries. To insert an index entry for the topic Writer, on the Insert Index Entry dialog  (Figure 7 on page 13), type Writer in the Entry box and LibreOffice in the 1st key box.
    • Note
If field shading is active (Tools > Options > LibreOffice > Application Colors > Text Document > Field shadings), when a selected word or phrase has been added to the index, it is shown in the text with a gray background. If the text of an index entry has been changed from the text of the word selected, the index entry is marked by a small gray rectangle at the start or end of that word.

Creating a concordance
----------------------------------------------------------------------

A concordance is a plain text file that lists words to add to the index. It has one word or phrase defined on each line. Each line has a strict structure, consisting of seven fields, separated by semicolons:
Search_term;Alternative_entry;1st_key;2nd_key;Match_case;Word_only
No space is entered between the semicolon and a field’s content. A key is a higher level heading that a search term is placed beneath.
If you choose not to have an alternative entry, a first key or a second key, leave those fields blank, so that one semi-colon immediately follows another.
The last two fields are structured somewhat differently. If you want only entries that have the same upper or lower case letters as your entries, enter 1 in the second to last field. Similarly, entering 1 in the last field sets the index to only include instances where the entry is a whole word, and not part of a larger one. You can also leave the last two fields blank, as you can with any of the others.
For example, entering:
Macaw;Ara;Parrots;;0;0
Would produce an entry for macaw with
    • A listing under macaw.
    • An alternate listing under ara (the scientific name).
    • A listing of Parrots, Macaw.
    • No second key (notice the two semi-colons).
    • Inclusion of instances that start with a lower or upper case letter (both “macaw” and “Macaw”).
    • Inclusion of instances in which the term is a whole word or part of a longer word.
Whether creating a concordance is faster than adding entries manually is debatable, but a concordance is certainly more systematic. The disadvantage of a concordance is that it can produce an index that includes instances of common words that are irrelevant for your purposes. In many cases, a useful index may require a combination of manual entries and a concordance.

Creating an alphabetic index quickly
----------------------------------------------------------------------

Now that you have some index entries, you can create the index.
Although indexes can be customized extensively in Writer, most of the time you need to make only a few choices.
To create an index quickly:
    1) Click in the document where you want to add the index and click Insert > Table of Contents and Index > Table of Contents, Index or Bibliography to open the Table of Contents, Index or Bibliography dialog.
    2) In the Type box on the Type tab (Figure 8), select Alphabetical Index.
    3) In the Options section, consider deselecting Case sensitive (so capitalized and lower-case words are treated as the same word) and Combine identical entries with p or pp.
    4) If using a concordance, select Concordance file in the Options section, then click the File button and select the concordance file you created.
    5) Click OK. The result will be a typical index.

Customizing an index
----------------------------------------------------------------------

To customize an existing index, right-click anywhere in the index and choose Edit Index in the context menu.
The Table of Contents, Index or Bibliography dialog (Figure 8) has five tabs. All of them can be used to customize the index.
    • Type tab: set the attributes of the index.
    • Entries and Styles tabs: to format the entries in the index.
    • Columns tab: put the index into more than one column.
    • Background tab: add color or an image to the background of the index.
After making your changes, click OK to save the index so it appears in your document.

Type tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Type tab (Figure 8) to set the basic attributes of the index.
To give the index a different title, edit the Title field. To delete the title, clear the Title field.
Be sure the type of index is set to Alphabetical Index.
By default, to prevent the index from being changed accidentally, the option Protected against manual changes is selected; the index can only be changed by using the context menu or the dialog. If the option is not selected, the index can be changed directly just like other text, but any manual changes to an index will be lost when it is updated, so they should be avoided.

In the drop-down list in the Create Index or Table of Contents section, select Entire document, or choose to create an index for just the current chapter.
Other options determine how the index handles entries.
Combine identical entries
Defines how identical entries are dealt with. Normally each page number of an indexed word or phrase will be shown in the index; however, these can be combined using the Combine identical entries with p or pp.
If you want a page range displayed, select Combine with – (which will produce something similar to 23–31). To include different entries based on what letters are capitalized, select Case sensitive.
AutoCapitalize entries
Automatically capitalizes the first letter of each entry regardless of how the terms show within the document.
Keys as separate entries
For the index keys to have their own page numbers, select this option.
Concordance file
Choose the concordance file to be used, if any. See page 14 for more information.
Sort
Defines how the entries are sorted when displayed. The only option is alphanumeric, but you can define which language alphabet will be used.

Entries tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Entries tab to set exactly how and what will be displayed for each of the entries. The tab is similar to Figure 9.
    • Note
Hyperlinking from the index to the location of entries in the text is new in Writer 7.6.

To begin, in the Level column select the index level whose elements you want to format. Level “S” refers to the single letter headings that divide the index entries alphabetically when the Alphabetical delimiter option is selected in the Format section. (You will be able to apply your changes to all index levels later.) In the Structure and Formatting section, the Structure line displays the elements for entries in that level. Each button on the line represents one element:
    • The E icon represents the entry text.
    • The T icon represents a tab stop.
    • The # icon represents the page number.
    • The HI icon represents chapter information. This is not present by default, but can be added by selecting the Heading info button.
Each white field on the Structure line represents a blank space. You can add, change, or delete elements as described on page 9 for a table of contents.

Heading Info
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Heading Info button inserts heading information, such as the heading number and contents, as selected from the Heading info list that appears when this option is selected. Heading information is specified in Tools > Heading Numbering.

Applying character styles
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Each element on the Structure line may be given additional formatting. For example, you may want the page number to be a different size from the rest of the index text. To do this, apply a character style to one of the elements in the Structure line, as for a table of contents (page 10).

Formatting entries
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Apply additional formatting using the options in the Format section.
Alphabetical delimiter
This separates the index entries into blocks that start with the same first letter, using that letter as a header. For example, if the index begins:
apple,  4
author, 10
break,  2
bus, 4
Then selecting this option will produce:
A
apple,  4
author, 10

B
break,  2
bus, 4
Key separated by commas
Arranges the entries in the index on the same line but separated by commas.
Tab position relative to Paragraph Style indent
When selected, entries are indented according to the settings of their individual formats. Where a paragraph style with an indent on the left is in use, tab stops will be relative to this indent. If this option is not selected, tab stops will be relative to the left margin position.

Styles and Background tabs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Styles tab to change which paragraph style is assigned to display the text of each level in the index. In most cases, the best strategy is to keep the assigned styles but change their settings as needed to make the index appear the way you want.
The Background tab is the same as for TOCs. Refer to “Styles tab” on page 11 and “Background tab” on page 11 for detailed information on these tabs.

Columns tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the Columns tab (Figure 10) to change the number of columns for the index.

Adding multiple columns
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To display the index in more than one column:
    1) Enter the number of columns desired in the box labeled Columns or select the icon representing the number of columns.
    2) To evenly distribute the columns according to the page width, select the AutoWidth box. If it is unchecked, you can manually set each of the following:
    • Width of each of the columns
    • Spacing between the columns
    3) To have a separator line between the columns:
    • Style: The default is None, or select from three choices of line style.
    • Width: The width (thickness) of the line. The default is 0.25pt.
    • Color: Choose the color of the separator line. The default is Black.
    • Height: The height of the line, as a percentage of the full column height. The default is 100%
    • Position: Position of the line relative to the columns (top, centered, or bottom) if the height is less than 100%.

Maintaining an index
----------------------------------------------------------------------

To modify the appearance of an index, right-click anywhere in the index and choose Edit Index in the context menu. The Table of Contents, Index or Bibliography dialog opens and you can edit and save the index using the five tabs described in the previous section.
To update or delete an index, right-click anywhere in the index and select Update Index or Delete Index.

Viewing and editing existing index entries
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once you have added the initial entries, you can make some amendments. You can view and edit these using the following steps:
    1) Ensure that field shading is active (View > Field Shadings or Ctrl+F8), so you can locate index entries more easily.
    2) Place the cursor in the field shading of an existing index entry in the body of the document, right-click, and select Edit Index Entry in the content menu. In the case of a changed-text entry, the field shading is immediately before the word. Placing the cursor immediately before a word marked as a text entry will satisfy both selection criteria.
    3) A dialog similar to Figure 11 appears. You can move through the various index entries using the forward and back arrow buttons. If there is more than one entry for a single word or phrase, a second row of buttons with a vertical bar at the point of the arrow head is displayed allowing you to scroll through each of these entries.
    4) Make the necessary modifications or additions to the index entries, and then click OK.

Other types of index
======================================================================

An alphabetical index is not the only type of index that Writer can produce. Other types include indexes of figures, tables, and objects, and you can even create a user-defined index. This chapter does not give examples of all the possibilities.
To create other indexes:
    1) Place the cursor where you want the index created.
    2) Select Insert > Table of Contents and Index > Table of Contents, Index or Bibliography on the Menu bar.
    3) On the Table of Contents, Index or Bibliography dialog, in the Type drop-down list, select the index wanted.
    4) Modify the various tabs, which are similar to those discussed in previous sections.
    5) Click OK when everything has been set.

Example: Creating a table of figures
----------------------------------------------------------------------

Creating a table of figures or tables is easy if the figure captions were created using Insert > Caption or manually using a number range variable as described in Chapter 17, Fields.
    1) On the Table of Contents, Index or Bibliography dialog, in the Type drop-down list, choose  Table of Figures. Optionally, change the Title.
    2) Be sure Captions is selected in the Create From section, and choose the category of caption. The default for Category is Figure; the example uses Figure for the captions.
    3) Under Display, you can choose References (to include the category, number, and caption text), Category and Number, or Caption Text. We have chosen References.
    4) Optionally select Create from additional paragraph style and select a style from the list.
    5) The other tabs of this dialog are similar to those described for tables of contents.

    6) Click OK. The result is shown in Figure 13.

Bibliographies
======================================================================

A bibliography is a list of references used in a document. The references can be stored in a bibliographic database or within the document itself.
This topic shows you how to use Writer's facilities to:
    • Create a bibliographic database; add and maintain entries.
    • Add a reference (citation) into a document.
    • Format the bibliography.
    • Update and edit an existing bibliography.

Citation styles and the bibliographic database
----------------------------------------------------------------------

Although you can create citations (references) within a document itself, creating a bibliographic database allows reuse in other documents and saves a lot of time.
Citations within the text require entries in different fields in the bibliography database, and different presentations in the text. Before creating a list of references, determine which citation style you need for a document. The five main styles are:
    • APA (American Psychological Association): Psychology, education, and other social sciences.
    • MLA (Modern Languages Association): Literature, art, and humanities.
    • Chicago: History and specific publications.
    • Turabian: A variation of the Chicago style for general use by university students.
    • AMA (American Medical Association): Medicine, Health, and Biology.
The Bibliography Database (Figure 14) is the source for citations in the text, no matter what citation style you use.
All citations use the Identifier field to set the format for a citation in the document. In this column, add the citation in the correct form for the citation style. All necessary information, including the Identifier field, should be entered before any citation is created in the document.
    • Tip
Writer has a single bibliography database for all documents. Since formatting entries can be tedious, consider creating a template with citations for each type of source material.

Creating a bibliographic database
----------------------------------------------------------------------

For most of this topic, the database table used is the sample one that comes with Writer. For information on creating a new table in the bibliographic database, see the Getting Started Guide.
The bibliography database has to cover many different media and circumstances, which is why it contains so many fields. It also includes fields such as ISBN that no citation style uses, but might be useful to you during your research.
    • Note
Any single entry in the bibliography needs only about half a dozen fields filled in, no matter what citation format you use. What differs is the fields needed for each type of source material and the order of the fields in each citation style.
To open the database select Tools > Bibliography Database. The Bibliography Database window, similar to that in Figure 14, opens. The upper part of the tab shows all of the records, in a table layout similar to that of a spreadsheet. The lower part of the tab shows all the fields of the selected record.
    • Note
The Identifier column in the database table and the Short Name field below the table are the same field. The sample entries in the sample database for these fields are meaningless. Replace them with the proper format for the citation style to be used.

Changing the data source
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To change the data source in use (for example, if you have more than one bibliographic database for different purposes), select Data > Choose Data Source on the Menu bar, or click the Data Source button on the toolbar near the top of the Database window. The Choose Data Source dialog lists registered data sources. Select one of them and click OK.
To add (register) a different data source, see instructions in the Getting Started Guide.

Filtering records
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To set up a filter for specific records within the bibliographic database, select Data > Filter on the Bibliographic Database Menu bar, or click the Standard Filter button on the toolbar near the top of the window. In the Standard Filter dialog (Figure 15), choose the fields, conditions, and values for the filter and click OK.

Adding entries to the database
----------------------------------------------------------------------

Entries can be added to the bibliography database in two ways: using the Data Source view of the database, or the Bibliography Database window.
To add entries using the Data Source view of the bibliography database:
    1) Select View > Data Sources on the Menu bar, or press Shift+Ctrl+F4, to open the data source window, similar to Figure 16.
    2) Make sure that the correct table is selected in the Bibliography database. You may have to expand some levels to be able to select the correct ones.

    3) Scroll to the bottom of the list and type into the relevant fields in a blank line. The Save current record icon (in the upper left) becomes active. Click on it to save the addition to the database.
To add entries using the Bibliography Database window:
    1) Select Tools > Bibliography Database on the Menu bar. The window shown in Figure 14 on page 23 opens.
    2) Select Data > Record on the Menu bar of the window, or click the + icon to the left of the horizontal scroll bar.
    3) Type a name for the entry in the Short Name box. Complete other fields as required.
    4) To complete the entry and add it to the database, click on any other cell in the table.

Maintaining entries in the database
----------------------------------------------------------------------

To maintain entries in the database, use either the Data Source view or the Bibliography Database window. Select the appropriate record and modify the fields as appropriate.
Modified entries are saved automatically to the database when the cursor moves off the record.

Advanced: Modifying the bibliographic database
----------------------------------------------------------------------

You can modify the bibliography database in several ways, as summarized below.
    • Note
For more information on how to use LibreOffice’s database features, see the Getting Started Guide.

Column details
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To change the details of columns in the bibliographic database, select Data > Column Arrangement on the Menu bar, or click the Column Arrangement button on the toolbar near the top of the window (Figure 14). On the Column Layout dialog (Figure 17), you can change which fields are allocated to columns. For example, you can select to have Author data go into the Identifier column, by changing the destination in the drop-down list. The Short name data column destination sets to <none> automatically, to prevent setting duplicate destinations for data.

Field details
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To make changes to the bibliography database (for example, rename fields or change the length of fields), do the following:
    1) In the main document (not the Bibliography Database window), press Shift+Ctrl+F4 or click View > Data Sources to open the Data Source window, similar to Figure 16.
    2) Make sure that the Bibliography database is selected as well as the correct table.
    3) Right-click the table entry (biblio in the example) and select Edit Database File in the context menu. This opens a window similar to Figure 18, which is the main menu for Base, the database component of LibreOffice.
    4) If Tables (in the Database section on the left) is not selected, select it now.
    5) Right-click the biblio table name in the Tables section and select Edit in the context menu to display a window similar to that shown in Figure 19.
    6) You can now select each of the fields. Select the text in the Field Name cell and change the entry as required. Click in the Field Type cell to open a selection menu to change the data type in that cell. In the Field Properties section, you can modify the data properties. For each field selected, a description of that field appears to the right of the section.
    7) When finished, you will be asked to confirm that you want the changes saved.

Adding references (citations) into a document
----------------------------------------------------------------------

Writer supports two methods of adding references to your document:
    • From a bibliography database, such as the one built into Writer.
    • Directly from the keyboard.

Entering references from a database
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To add references from the bibliographic database into a document:
    1) Place the cursor where you want the reference to appear.
    2) On the Menu bar, choose Insert > Table of Contents and Index > Bibliography Entry.
    3) In the Insert Bibliography Entry dialog (Figure 20), choose Bibliography database in the Bibliography Source section at the top of the dialog.

    4) Select the reference from the Short name drop-down list in the middle of the dialog. The Author and Title of the selected reference are shown below the Short name field, to help you verify that it is the reference you want.
    5) To insert the reference into the document, click Insert. You can keep the dialog open and insert another reference into the document; you do not need to close and reopen it.
    6) When you have finished inserting all the references, click Close.

Entering references from documents
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You may choose to enter bibliographic entries directly into the document, instead of from an external database. Click in the document where you want to add the entry.
    1) Select Insert > Table of Contents and Index > Bibliography Entry.
    2) In the Insert Bibliography Entry dialog (Figure 20), select Document content in the Bibliography Source section at the top of the dialog.
    3) Click New to open the Define Bibliography Entry dialog.
    a) Complete all the fields that are relevant to your entry. Type a unique name in the Short name box; the Insert Bibliography Entry dialog uses this entry for the citation.
    b) Select an option in the menu in the Type box to enable the OK button.
    c) Click OK when all the fields wanted are completed.
    d) Click Insert to add the Short name field to the document, and then click Close.
To re-use an entry in your document, restart the sequence above, and then select the Short name required from the current list of entries, instead of selecting to add a new entry.

Editing a reference
----------------------------------------------------------------------

To edit a reference:
    1) Right-click the entry (the cursor then displays to the left of the entry).
    2) In the context menu, select Bibliography Entry. The Edit Bibliography Entry dialog (similar to the Insert Bibliography Entry dialog) opens.
    3) To quickly edit only the Short name, click the text box, edit the entry and then click Apply.
    4) To edit more of the entry, click Edit to open the Define Bibliography Entry dialog.
       Make any changes required and then click OK to return to the Edit Bibliography Entry dialog.
    5) Click Apply to accept the changes and exit the dialog.
    • Note
Modified references are stored only in the document. If the source is a bibliography database, that database remains unmodified.

Creating the bibliography
----------------------------------------------------------------------

    1) Place the cursor at the point where you wish to insert the bibliography.
    2) Select Insert > Table of Contents and Index > Table of Contents, Index or Bibliography and change the Type to Bibliography, to display a dialog similar to that shown in Figure 21.

Type tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Writer supports two ways of displaying references (citations) in the text of a document:
    • Using the text recorded in the Short name field of each bibliographic entry, for example (Smith, 2001) depending on citation style.
    • By numbering the referenced documents in the sequence they occur in the text, for example [1].
    • Tip
To specify which citation style is used in the document, use the Type tab on the Table of Contents, Index or Bibliography dialog (Figure 21).
Formatting the bibliography involves choices made in two places:
    • Table of Contents, Index or Bibliography dialog, covered in this section.
    • Bibliography 1 paragraph style (see page 30).
The basic settings are selected on the Type tab.
    1) To give the bibliography a title, enter it in the Title field. (A title is not required.)
    2) You can protect the bibliography from being changed accidentally, by selecting Protected against manual changes. If this option is selected, the bibliography can only be changed using the right-click menu or the Table of Contents, Index or Bibliography dialog. If the option is not selected, the bibliography can be changed directly on the document page, just like other text, but any manual changes will be lost when you update the bibliography.
    3) To have the bibliographic entries (citations) numbered within the body of the document (for example, [1], [2]...), select Number entries. If, however, you wish to have the Short name field contents (from the database) appear in the document, deselect this option.
    4) Select the type of brackets that you want for the referenced entries shown within the body of the document.
    5) Define the sorting you require. Currently only alphanumeric sorting is supported. Sorting by the sequence that entries appear in the text is done on the Entries tab.

Entries tab
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The structure of the Entries tab (Figure 22) is similar to that for tables of contents and indexes.

The Type section refers to the kind of source, such as a book, periodical, or web page. Each entry in the Type list has a default structure format. You can define how the entry will appear, based on its source, by selecting from the Type list of entries, or simply apply the same format to all entries by clicking the All button.
The Structure of the entry is based on the fields available in the bibliographic database. Consult the citation style required for your document and modify the Structure line as needed.
To remove elements from the Structure line, click the element, then click the Remove button.
To add an element, click in the Structure line where it is to be inserted. Select either the Tab Stop, or an element in the drop-down list to the left of the Insert button, and then click Insert. The elements in the drop-down list are those fields found in the Bibliography Database.
All the elements on the Structure line can be formatted using the Character Style selection list. For example, you can define a character style so that book and journal titles are in italics or bold.
To determine how entries are sorted, modify the Sort by options. To sort by the sequence that entries appear in the text, choose Document position. In most modern citation styles, you will want Content (alphabetical descending order). Use Sort keys to group similar references.

Styles, Columns and Background tabs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Refer to “Styles tab” on page 11, “Columns tab” on page 18 and “Background tab” on page 11 for detailed information on these tabs.

Modifying the paragraph style for the bibliography
----------------------------------------------------------------------

You can modify the Bibliography 1 paragraph style to suit your requirements. For example, to number the entries in the bibliography list, you need to define a list style and link that list style to the Bibliography 1 paragraph style. To do this:
    1) On the Styles deck in the sidebar, click on the List Styles icon. Right-click on Numbering 123 and choose New in the context menu.
    2) In the List Style dialog, go to the Organizer tab and type a name for this style. In our example, we have named it Bibliography.
    3) In our example we want to have the numbers enclosed in square brackets. To do this, go to the Customize tab and type [ in the Before box and ] in the After box, as shown in Figure 23. Remove any other punctuation, such as a period, that may be in the After box.

    4) Now go to the Position tab of the List Style dialog (Figure 24). In the Indent at and Tab stop at boxes, specify how much indentation you want for the second and following lines of any item in the bibliography list of your document. Often you will need to experiment a bit to see what is the best setting. In our example, we have chosen 1 cm.

    5) Click OK to save these settings and close the List Style dialog. Return to the Styles deck, click the Paragraph Styles icon, choose All Styles in the list at the bottom of that window, then right-click on Bibliography 1 and choose Modify.
    6) On the Paragraph Style dialog, go to the Outline & List tab and select Bibliography in the List Style drop-down list (Figure 25). Click OK to save this change to the Bibliography 1 paragraph style.

Now when you generate the bibliography, the list will look something like the one shown in Figure 26. You may also need to modify the structure line on the Entries tab (Figure 22).

Updating, editing, and deleting an existing bibliography
----------------------------------------------------------------------

Right-click anywhere in the bibliography. From the context menu, select:
    • Update Index to update the bibliography.
    • Edit Index to open the Table of Contents, Index or Bibliography dialog so you can edit and save the bibliography.
    • Delete Index to delete the bibliography without a confirmation request.

External bibliography tool
----------------------------------------------------------------------

If you find Writer’s bibliography feature too limited, you may wish to try Zotero, a free and open source tool, available for macOS, Windows, and Linux. It is reported to work well with Writer (https://www.zotero.org/).
