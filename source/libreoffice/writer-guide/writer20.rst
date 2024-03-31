======================================================================
Writer Guide Chapter 20, Customizing Writer ノート
======================================================================

.. include:: ./abbrev.txt

.. contents:: 章見出し
   :depth: 3
   :local:

Introduction
======================================================================

This chapter briefly describes some of the setup options found under Tools > Options (LibreOffice > Preferences on macOS) on the Menu bar in Writer. Additional options, and more details about the ones given here, are covered in the Help and in the Getting Started Guide. Several of the most relevant options are discussed in other chapters of this book, in the context of tasks where they are most applicable.
This chapter also briefly describes some common customizations to menus, toolbars, and keyboard shortcuts, including adding new menus and toolbars and assigning macros to events. Other customizations are made easy by extensions that can be installed from the LibreOffice website or from other providers. You can also activate and use some experimental features; see page 33.
    • Tip
Many options are intended for power users and programmers. If you don’t understand what an option does, it is usually best to leave it on the default setting unless instructions in this book recommend changing the setting.
    • Note
Customizations to menus and toolbars can be saved in a template. To do so, first save them in a document and then save the document as a template as described in Chapter 10, Working with Templates. If you work on more than one project, you may find that having different menus and toolbars can be useful.

Choosing options for all of LibreOffice
======================================================================

This section covers some of the settings that apply to all the components of LibreOffice (Writer, Calc, Impress, Draw, Math, and Base) and that are particularly important when using Writer.
Go to Tools > Options (LibreOffice > Preferences on macOS) and then click the marker (+ or triangle) by LibreOffice on the left-hand side. A list of pages drops down. Select an item in the list to display the relevant page on the right-hand side of the dialog.
    • Tip
The Reset button (located in the lower part of any page of the Options dialog) resets the values on that page to the values that were in place when you opened the dialog. It may be called Revert on some installations.
If you are using a version of LibreOffice other than US English, some field labels may be different from those shown in the illustrations.

User data
----------------------------------------------------------------------

Because Writer can use the name or initials stored in the LibreOffice – User Data page for several things, including document properties (‘created by’ and ‘last edited by’ information), the name of the author of comments and changes, and the sender address in mailing lists, make sure that the correct information appears here.
Fill in the form, or amend or delete any existing information. If you do not want user data to be part of the document’s properties, deselect Use data for document properties.
    • Tip
To have documents open at the page where the cursor is located when they were saved, select Use data for document properties on this dialog page, and go to File > Properties for each document and select Apply user data on the General tab. Unless both of these settings are selected, the document will open at the first page.
Alternatively, select Load view position with the document even if it was saved by a different user on the Load/Save – General page (see page 9).
In the Cryptography section, you can set the preferred public key for OpenPGP encryption and digital signature. These preferred keys will be pre-selected in the key selection dialog when you sign or encrypt a document (see Chapter 7, Printing and Publishing).

View options
----------------------------------------------------------------------

The options on the LibreOffice – View page affect how the document window looks and behaves. Set them to suit your personal preferences. For details, see the Help or the Getting Started Guide.

Print options
----------------------------------------------------------------------

On the LibreOffice – Print page, set the print options to suit your default printer and your most common printing method.
In the Warnings section on the right side of the page, you can choose whether to be warned if the paper size or orientation specified in the document does not match the paper size or orientation available for your printer. Having these warnings turned on can be quite helpful, particularly if you work with documents produced by people in other countries where the standard paper size is different from yours.

    • Tip
If your printouts are incorrectly placed on the page or chopped off at the top, bottom, or sides, or the printer is refusing to print, a likely cause is page size incompatibility.

Paths options
----------------------------------------------------------------------

On the LibreOffice – Paths page, you can change the location of files associated with, or used by, LibreOffice to suit your needs. For example, you might want to store documents by default somewhere other than My Documents, or you might want to store project templates in folders not in the supplied template paths. Multiple paths are possible. For more information, see the Getting Started Guide.

Fonts options
----------------------------------------------------------------------

If a document contains fonts that are not on your system, LibreOffice will substitute fonts for those it does not find. To specify different fonts from the ones that the program chooses, use the LibreOffice – Fonts page to specify replacement fonts.
    • Tip
Liberation fonts (Serif, Sans, and Mono) are often good choices to substitute for Times, Arial, and Courier.
    • Note
The choices made here do not affect the default fonts in documents. To do that, see “Basic Fonts options” on page 14. To change more than the basic fonts, create a new default template for Writer documents; see Chapter 10, Working with Templates.

Security options
----------------------------------------------------------------------

Use the LibreOffice – Security page to choose security options for saving documents and for opening documents that contain macros. For information on the options not mentioned here, refer to the Help or the Getting Started Guide.
Security Options and Warnings
If you record changes, save multiple versions, or include hidden information or notes in your documents, and you do not want some recipients to see that information, you can set warnings to remind you to remove it, or you can have LibreOffice remove some of it automatically. Note that unless the information is removed, much of it is retained even when the file has been saved to other formats, including PDF.
Click the Options button to open a separate dialog with several options, including:
Remove personal information on saving
Select this option to always remove user data from the file properties when saving the file. To save personal information with documents and still be able to manually remove personal information only from specific documents, do not select this option.
Ctrl-click required to open hyperlinks
The default behavior in LibreOffice is that using Ctrl+click on a hyperlink opens the linked document or website. This is because many people find writing and editing documents is easier when accidental clicks on links do not activate the links. To set LibreOffice to activate hyperlinks using just an ordinary click, do not select this option.

Application colors
----------------------------------------------------------------------

Writing, editing, and (especially) page layout are often easier when the page margins (text boundaries), the boundaries of tables and sections, grid lines, and other features are visible. In addition, you might prefer to use colors that are different from LibreOffice’s defaults.
On the LibreOffice – Application colors page (Figure 3), you can specify which user interface elements are visible and the colors used to display them.
    • To show or hide items such as text boundaries, select or deselect the boxes in the On column next to the names of the elements.
    • To change the default colors for a specific element, click the down-arrow in the Color setting column by the name of the element and select a color from the drop-down list.
    • To save your color changes as a color scheme, click Save, type a name in the Scheme box, and then click OK.

    • Note
To change the color settings used in Track Changes mode, go to Tools > Options > LibreOffice Writer > Changes.

Choosing options for loading and saving documents
======================================================================

You can set the options for loading and saving documents to suit the way you work.
If the Options dialog is not already open, click Tools > Options. Click the expansion symbol (+ or triangle) to the left of Load/Save.

General
----------------------------------------------------------------------

Most of the choices on the Load/Save – General page (Figure 4) are familiar to users of other office suites. Some items of interest are described below.

Load user-specific settings with the document
When a LibreOffice document is saved, certain settings from the user's system are saved with it. When the document is opened on another user’s system, it will use the settings saved from the previous user’s system. Deselecting this option causes the current user’s settings to override the settings previously saved with the document.
Even if this option is not selected, some settings are always loaded with the document:
    • Settings in File > Print > Options.
    • Spacing options for paragraphs before text tables.
    • Information about automatic updating for links, field functions, and charts.
    • Information about working with Asian character formats.
    • Settings for any data sources linked to a document.
Load printer settings with the document
If this option is enabled, the printer settings of the previous user will be loaded with the document. In an office setting, this may cause a document to be printed on a distant network printer unless the printer is manually changed in the Print dialog. If disabled, the current user’s default printer will be used to print the document. The current printer settings will be stored with the document whether or not this option is selected.
Load view position with the document even if it was saved by a different user
The “view position” is the location of the cursor in the document. This option causes the last-saved view position to be loaded regardless of who saved the document.
Save AutoRecovery information every __ minutes
Choose whether to enable AutoRecovery and how often to save the information used by the AutoRecovery process. AutoRecovery in LibreOffice saves the information needed to restore all open documents in case of a crash. If you have this option set, recovering your document after a system crash will be easier. This option is on by default.
Edit document properties before saving
If this option is selected, the document’s Properties dialog prompts you to enter relevant information the first time you save a new document (or whenever you use Save As).
Always create backup copy
Saves the previously saved version of a document as a backup copy in a separate folder whenever you save a document. When LibreOffice creates a new backup copy, the previous backup copy is replaced. The backup copy gets the extension .bak. To see or change the backup folder, go to Tools > Options > LibreOffice > Paths. When opening a backup file, you will be prompted to specify the program to open it with; choose LibreOffice. This option is on by default.
    • Tip
Authors whose work may be very lengthy should always consider enabling LibreOffice to create an automatic backup copy.
Save URLs relative to file system / to internet
Use these options to select the default for relative addressing of URLs in the file system and on the Internet. For details, see the Getting Started Guide.
Default File Format and ODF Settings
ODF format version: LibreOffice by default saves documents in OpenDocument Format (ODF) version 1.3 Extended. While this allows for improved functionality, there may be backwards compatibility issues. When a file saved in ODF 1.3 Extended is opened in an editor that uses an earlier version of ODF, some of the advanced features may be lost. If you plan to share documents with people who use editors that use older versions of ODF, you may wish to save the document using ODF 1.2 Extended (compatibility mode).
Document type: If you routinely share documents with users of Microsoft Word, you might want to change the Always save as option to one of the Word formats. However, you can choose a Word format when you save any individual file.

VBA Properties
----------------------------------------------------------------------

On the VBA Properties page, choose whether to keep any macros in Microsoft Office documents that are opened in LibreOffice. For details, see the Getting Started Guide.

Microsoft Office
----------------------------------------------------------------------

On the Load/Save – Microsoft Office page, choose what to do when importing and exporting Microsoft Office OLE objects (linked or embedded objects or documents such as equations or spreadsheets): convert them into or from the corresponding LibreOffice OLE object or load and save them in their original format. For details, see the Getting Started Guide.

HTML compatibility
----------------------------------------------------------------------

Choices made on the Load/Save – HTML Compatibility page affect HTML pages imported into LibreOffice and those exported from LibreOffice. For more information, see the Help and the Getting Started Guide.

Choosing Writer-specific options
======================================================================

Settings chosen in the LibreOffice Writer section of the Options dialog determine how Writer documents look and behave while you are working on them. If the Options dialog is not already open, choose Tools > Options. Click the marker (+ or triangle) by LibreOffice Writer on the left side of the dialog.

General options
----------------------------------------------------------------------

The choices on the LibreOffice Writer – General page (Figure 5) affect the updating of links and fields, the units used for rulers and other measurements, and the default tab stop positions.

Automatically Update [Fields and Charts]
You may not want fields or charts to update automatically while you are working, because that slows down performance. Alternatively, you may want automatic updates if you are referring to information in the fields or charts.
Update Links when Loading
Depending on your work patterns, you may not want links to be updated when you load a document. For example, if your file links to other files on a network, you won’t want those links to try to update when you are not connected to the network.
Settings
Measurement unit
Document designers recommend using points as the default measurement because you can easily relate things like font size to things like indents and tabs.
Tab stops
The Tab stops setting specifies the distance the cursor travels for each press of the Tab key. This setting is also used for the indent distance applied by the Increase Indent and Decrease Indent buttons on the Formatting Toolbar, which affect the indentation of entire paragraphs.
    • Tip
To avoid unwanted changes, do not rely on default tab settings. Rather, define tabs in paragraph styles or individual paragraphs (see Chapter 4, Formatting Text).
Word Count
Additional separators
For counting words, specifies the characters that are considered to separate words, in addition to spaces, tabs, line breaks, and paragraph breaks.
Show standardized page count
Editors and publishers often define a “standard” page as containing a specified number of characters or words; this field allows quick calculation of the number of these pages.

View options
----------------------------------------------------------------------

Two pages of options set the defaults for viewing Writer documents: View (described here) and Formatting Aids (described on page 13). View is a good page to check if, for example, you cannot see graphics on the screen.
Guides – Helplines While Moving
Helplines assist with precisely position a frame or drawing object on a page. When enabled, horizontal and vertical lines appear that are the height and width of a selected object. These lines extend across the complete working area as the object is moved.
Display Fields
Hidden text
Display text that is hidden by Conditional Text or Hidden Text fields.
Hidden paragraphs
Display paragraphs that contain a Hidden Paragraph field. This option has the same function as the menu command View > Field Hidden Paragraphs.
Display tracked changes
Tracked deletions in margin
By default, deletions are shown in the text with a strikethrough font. To show deletions in the margin, not in the text, select this option.
Tooltips on tracked changes
When this option is selected, hold the mouse pointer over a tracked change to show the type of change, the author, date, and time of day for the change. To hide these tooltips, deselect this option.
Outline Folding
Show outline-folding buttons
When this option is selected, a button with an arrow is visible near any selected heading in your document. Click on it to “fold” (hide) all text from the current heading to the next heading.
Include sub levels
If this option is also selected, clicking on a heading folds all text from that heading to the next same-level heading with all its subheadings.
The other options should be self-explanatory. If not, please refer to the Help.

Formatting Aids options
----------------------------------------------------------------------

On the LibreOffice Writer – Formatting Aids page (Figure 7), select the desired options.

Layout Assistance – Math baseline alignment
To set the default vertical alignment for formula (Math) objects to use the text base line as a reference, select this option. To enable changing the vertical positioning of objects, deselect this option; you can then set the position for individual objects. See the Math Guide for more information.
Display Formatting
The Display Formatting options determine which symbols show when you select View > Formatting Marks on the Menu bar or the Formatting Marks icon on the Standard toolbar. Symbols such as paragraph ends and tabs can help in writing, editing, and page layout. For example, they can show if there are any blank paragraphs or if any tables or graphics are too wide and intrude into the margins of the page.
Protected Areas – Enable cursor
When this option is selected, you can set the cursor in a protected area, but you cannot make any changes. To make changes, you first need to unprotect the area. The methods of protecting and unprotecting vary with the area.
Direct Cursor
Direct Cursor lets you enter text, images, tables, frames, and other objects in any blank area in your document. Writer then inserts your choice of tabs, spaces, indents, and so on to position the text or objects. For details on these choices, please see the Help.
    • Note
The direct cursor feature can lead to many formatting oddities and is incompatible with rigorous use of styles.
Image – Anchor
Choose the default anchor for newly added images: To Paragraph, To Character, or As Character. For more about anchoring images, see Chapter 11, Images and Graphics.

Grid options
----------------------------------------------------------------------

Snap to grid automatically moves an object to the nearest gridlines. This can be very helpful when you are trying to align several objects such as graphics or tables.
On the LibreOffice Writer – Grid page (Figure 8), you can choose whether to enable this feature and what grid intervals to use. If the grid intervals (subdivisions) are too large, you may find that you do not have enough control in placing the objects.

Basic Fonts options
On the LibreOffice Writer – Basic Fonts (Western) page (Figure 9), you can choose the fonts and font sizes for the Default Paragraph Style, headings, lists, captions, and indexes. These values are applied to new documents unless different settings are selected in the document itself or defined in the document’s template.
To reset the values to the defaults when LibreOffice was installed, click the Default button.
If Asian and/or CTL have been activated in Languages, extra pages are provided for their font options.

Print options
----------------------------------------------------------------------

On the LibreOffice Writer – Print page, you can choose which items are printed with a Writer document by default. These options are in addition to the general options for all LibreOffice components on the LibreOffice – Print page (see page 6).

Some considerations:
    • To save printer ink or toner when working on drafts, you might want to deselect some of the items in the Contents section.
    • The Print text in black option causes color text (but not graphics) to print as black on a color printer; on a black-and-white printer, this option causes color text to print as solid black instead of shades of gray (dithered).
    • By comparison, the Convert colors to grayscale option on the Options – LibreOffice – Print page (Figure 2), prints all text and graphics as grayscale on color printers. (On black-and-white printers, color in graphics normally prints as grayscale.)
    • If you are printing double-sided on a non-duplexing printer, you might choose to print only left or right pages, then turn the stack over and print the other pages.
    • Tip
You can override any of these defaults when printing a specific document. Click File > Print, then use the options on the various pages of the Print dialog.

Table options
----------------------------------------------------------------------

On the LibreOffice Writer – Table page (Figure 11), you can specify the default behavior of tables. See the Help or Chapter 13, Tables, for more information.

Some considerations:
    • If most of your tables will require borders or headings, you may wish to select those options. If most of your tables are used for page layout, deselect Border and Heading.
    • Select Do not split to prevent tables from being split across pages.
    • Number recognition can be very useful if most of your tables contain numerical data. Writer will recognize dates or currency, for example, and format the numbers appropriately. However, if you want the numbers to remain as ordinary text, this feature can be quite irritating, so you may want to deselect it.
    • The Keyboard Handling section specifies the distances that cells move when you use keyboard shortcuts to move them and the size of rows and columns inserted using keyboard shortcuts. If you don’t use keyboard shortcuts for this purpose, you can ignore these settings. See the Help for more information.
    • The Behavior of rows/columns section specifies the effects that changes to rows or columns have on adjacent rows or columns and the entire table. You might need to test these selections to fully understand the effects.

Changes options
----------------------------------------------------------------------

If you plan to use the change-tracking feature of Writer (described in Chapter 3, Working with Text: Advanced), use the LibreOffice Writer – Changes page (Figure 12) to choose the way changes to text and formatting are marked. Change bars can show where a change has been made to a line of text and are formatted under Lines Changed.

Comparison options
----------------------------------------------------------------------

The options on the LibreOffice Writer – Comparison page determine the level of detail used by the Compare Document feature (Edit > Track Changes > Compare Document), described in Chapter 3, Working with Text: Advanced.
Choose whether to compare word-by-word, character-by-character, or using an algorithm (Auto, which is the default). When By word or By character is selected, the random number choices are activated; optionally specify the minimum number of characters to be compared (Ignore pieces of length __).

Compatibility options
----------------------------------------------------------------------

The settings on the LibreOffice Writer – Compatibility page (Figure 14) are used mainly when importing documents from Microsoft Word. If you are not sure about the effects of these settings, leave them as the defaults provided by LibreOffice. For information about settings that are not described below, see the Help. All settings selected will apply only to the current document, unless you select the Use as Default button at the bottom (not shown in the figure).

Add spacing between paragraphs and tables
Paragraph spacing is treated differently in LibreOffice Writer than it is in Microsoft Word. If you have defined spacing between paragraphs or tables in LibreOffice, this spacing is added to the spacing defined in Microsoft Word. This only affects the current document.
If this option is selected, Microsoft Word-compatible spacing is added between paragraphs and tables in LibreOffice Writer documents.
Add paragraph and table spacing at tops of pages
You can define paragraphs and tables to have space appear before (above) them. If this option is selected, any space above a paragraph will also appear if the paragraph is at the beginning of a page or column, or if the paragraph is positioned on the first page of the document, or after a manual page break. This only affects the current document.
If you import a Microsoft Word document, the spaces are automatically added during the conversion.
Add paragraph and table spacing at bottom of table cells
Specifies that the bottom spacing is added to a paragraph, even when it is the last paragraph in a table cell.

AutoCaption options
----------------------------------------------------------------------

LibreOffice can automatically insert captions for tables, pictures, frames, and OLE objects in a Writer document. To set this up, use the options on the LibreOffice Writer > AutoCaption page. Select the object you want to be automatically captioned (LibreOffice Writer Table in Figure 15). With the item highlighted, specify the characteristics of the caption.
The categories supplied for captions are Illustration, Table, Text, Drawing, and Figure. To use another name (for example, Photo) for the caption label, type it in the Category box.

    • Note
You may not want captions for every table, for example if you use tables for layout as well as for tables of data. You can always add captions to individual tables, graphics, or other objects (right-click > Insert Caption).
Information about numbering captions by chapter, character styles, frame styles, and other items on the AutoCaption page is given in other chapters in this book.

Mail Merge Email options
----------------------------------------------------------------------

Using a data source such as an address book, Writer can insert personal, address, and other information into form letters. These documents can be printed for mailing or they can be emailed through Writer. See Chapter 14, Mail Merge, for details.

Use the LibreOffice Writer – Mail Merge Email page (Figure 19) to set up the user and server information for sending form letters by email. If you are not sure what information to put in any of the fields, consult your email program or your internet service provider.

Choosing language settings
======================================================================

You may need to do several things to get the language settings you want:
    • Install the required dictionaries.
    • Change some locale and language settings.
    • Choose spelling and grammar options.
    • Enable Language Tool.

Install the required dictionaries
----------------------------------------------------------------------

LibreOffice automatically installs many language modules with the program. A language module can contain up to three submodules: spelling dictionary, hyphenation dictionary, and thesaurus. These are usually referred to as “dictionaries” in Writer.
To add other dictionaries, be sure you are connected to the Internet, and then choose Tools > Language > More Dictionaries Online on the Menu bar. LibreOffice will open your default web browser to a page containing links to additional dictionaries that you can install. Follow the prompts to select and install the ones you want.

Change some locale and language settings
----------------------------------------------------------------------

You can change some details of the locale and language settings that LibreOffice uses for all documents or for specific documents. See the Help for details on all these options.
In the Options dialog, click the expansion symbol (+ sign or triangle) by Language Settings and choose Languages. On the right-hand side of the Language Settings – Languages page (Figure 17), change the settings as required.

In the example, English (USA) has been chosen for all the appropriate settings, but you could choose a mixture of languages. For example, if you were working in Germany, you might prefer the user interface to be in English (USA), but German (Germany) for the Locale setting, which influences settings for numbering, currency, and units of measure.
If you want the language setting to apply to the current document only, instead of being the default for all new documents, select For the current document only.
Changes to the system input language normally affect text typed into a document after the change. If you do not want this to happen, select Ignore system input language; new text will then continue to follow the language of the document or the paragraph, not the system language.
If necessary, select the options to enable support for Asian languages (Chinese, Japanese, Korean) and support for CTL (complex text layout) languages such as Hindi, Thai, Hebrew, and Arabic. If you choose either of these options, the next time you open the Options dialog, you will see some extra pages under Language Settings. These pages are not discussed here.
Choose spelling and grammar options
To change the options for checking spelling and grammar, use the Language Settings > Writing Aids page (Figure 18).

Some considerations:
    • You can over-ride the Check spelling as you type setting in a document using Tools > Automatic Spell Checking on the Menu bar or the Toggle Automatic Spell Checking icon on the Standard toolbar.
    • To have grammar checked as you type, also enable Check spelling as you type.
    • If you use a custom dictionary that includes words in all uppercase and words with numbers (for example, AS/400), select Check uppercase words and Check words with numbers.
    • Check special regions means that text in headers, footers, frames, and tables are also checked when checking spelling.
Here you can also select which of the user-defined (custom) dictionaries are active, add a new custom dictionary, edit dictionaries, and delete custom dictionaries. Dictionaries installed by the system cannot be deleted. For details on using the Available Language Modules and User-defined Dictionaries sections, please see the Help.
    • Tip
When checking spelling, words marked “Add to Dictionary” are added by default to the standard dictionary. Words marked “Ignore All” are added to the List of Ignored Words dictionary. See Chapter 2, Working with Text: Basics.

Defining and using custom dictionaries
----------------------------------------------------------------------

You can add a variety of custom (user-defined) dictionaries, including a dictionary of exceptions (words to be avoided, which will be marked as incorrect) or dictionaries of project-specific terms (words that will not be marked as incorrect). You can then select which, if any, of these custom dictionaries to use (in addition to a standard dictionary) when setting up a document.
For more information, see Writing Aids in the Help.

Sentence checking
----------------------------------------------------------------------

LibreOffice can check sentences in many languages. These checkers are enabled by default if the language is the computer’s default language, and others can be added using the Extensions dialog (see page 30). The set of rules for the sentence checkers depends on the language.
On the Language Settings > English Sentence Checking page, you can choose which items are checked for, reported to you, or converted automatically. This menu is also found in the English dictionaries extension installed by default by LibreOffice (select Tools > Extensions, select English spelling dictionaries and click the Options button to reveal the menu). Select which of the optional features you wish to check (see Chapter 2, Working with Text: Basics).
After selecting the additional grammar checks, you must restart LibreOffice, or reload the document, for them to take effect.

Activating Language Tool
----------------------------------------------------------------------

Language Tool is a multilingual grammar, style, and spelling checker provided by https://languagetool.org/. Its use is not described in this guide; please see the website for details.
If you have an API key for LanguageTool, you can activate the tool by selecting Enable LanguageTool in Language Settings > LanguageTool Server Settings, then supply the requested information (Base URL, Username, and API Key).

Customizing menus
======================================================================

You can add to and rearrange menus on the Menu bar, add commands to menus, and make other changes. You can also modify context (right-click) menus in a similar way.
To customize a menu, choose Tools > Customize. On the Customize dialog, go to the Menus tab (Figure 19) or the Context Menus tab.

Modifying an existing menu
----------------------------------------------------------------------

    1) In the Scope drop-down list in the upper right of the Customize dialog, choose whether to apply the customized menu to all of LibreOffice Writer or only to a specific document.
    2) In the Target drop-down list, select the menu that you want to customize. The list includes the main menus and submenus. The commands on the selected menu are shown in the Assigned Commands list.
    3) To add a command to the selected menu, click on a command in the Available Commands list and then click the large right arrow. You can narrow the search by using the Search box on the top left or selecting the Category in the drop-down list. Use the up and down arrows on the right-hand side to move the command into the position where you want it in the list.
    4) To remove a command from the selected menu, click on it in the Assigned Commands list and then click the large left arrow.
    5) To insert a separator or submenu, select the item directly before where you want the inserted item to appear, and use the commands in the Insert drop-down.

    6) To rename a menu item, select it in the Assigned Commands list and choose Rename in the Modify drop-down.

    7) When you have finished making all your changes, click OK to save them.

Creating a new menu
----------------------------------------------------------------------

You might find a “Favorites” menu useful, or a menu collecting tools for a specific project. To create a new menu:
    1) On the Menus tab of the Customize dialog, click the symbol next to Target and select Add in the drop-down list (Figure 22) to display the New Menu dialog (Figure 23).

    2) Type a name for the new menu in the Menu name box.
    3) Use the up and down arrow buttons to move the new menu into the required position on the Menu bar.
    4) Click OK to save and return to the Customize dialog.
The new menu now appears on the list of menus in the Customize dialog. It will appear on the Menu bar itself after you save your customizations.
After creating a new menu, you need to add some commands to it, as described above for modifying a menu.

Customizing toolbars
======================================================================

You can customize toolbars in several ways, including choosing which icons are visible and locking the position of a docked toolbar (as described in Chapter 1, Introducing Writer), and adding or deleting icons (commands) in the list of those available on a toolbar. You can also create new toolbars.

Modifying existing toolbars
----------------------------------------------------------------------

The procedures for creating and modifying a toolbar are similar to those for menus.
    1) Choose Tools > Customize on the Menu bar.
    2) On the Toolbars tab of the Customize dialog (Figure 24), in the Scope drop-down list on the upper right, choose whether to save this changed toolbar for Writer or for a selected document.
    3) In the Target drop-down list, select the toolbar that you want to customize. The current toolbar content is displayed in the Assigned Commands list.
    4) Select a command in the Available Commands list on the left. You can narrow your search by using the Search box on the top left or choosing a category in the drop-down list just below.
    5) Click on the large right arrow to add the selected command to the Assigned Commands list for the toolbar (on the right). Use the up and down arrows in the far right to position the command in the toolbar.
    6) To remove a command from a toolbar, select it in the Assigned Commands list on the right and click the large left arrow.
    7) To show or hide a command assigned to a toolbar, select or clear the checkbox by its icon in the Assigned Commands list on the right.
    8) To insert a separator, select the item directly before where you want the separator to appear, and use the command in the Insert drop-down.
    9) To rename a toolbar item, select it in the Assigned Commands list and choose Rename in the Modify drop-down.
When you have finished making all your changes, click OK to save them.

Creating a new toolbar
----------------------------------------------------------------------

To create a new toolbar:
    1) Choose Tools > Customize on the Menu bar.
    2) On the Toolbars tab of the Customize dialog, click the symbol next to Target and select Add in the list, to display the Name dialog.
    3) On the Name dialog, type the new toolbar's name and choose in the Save In drop-down list where to save this new toolbar: for Writer or for a selected document.
The new toolbar now appears on the list of toolbars in the Customize dialog. After creating a new toolbar, you need to add some commands to it, as described above.

Choosing icons for toolbar commands
----------------------------------------------------------------------

Toolbar buttons usually have icons, not words, on them, but not all of the commands have associated icons. If the command does not have an icon, you can choose an icon for it. To choose an icon, select the command in the list on the right, and click Modify > Change Icon. On the Change Icon dialog (Figure 25), scroll through the available icons, select one, and click OK to assign it to the command.
To use a custom icon, create it in a graphics program and import it into LibreOffice by clicking the Import button on the Change Icon dialog. Custom icons should be 16×16 pixels in size to achieve the best quality and should not contain more than 256 colors.

Customizing the user interface
======================================================================

By default, LibreOffice Writer’s commands are grouped in cascading menus and in toolbars filled with icons—the standard user interface described in Chapter 1. In addition, Writer provides other user interface variations, displaying contextual groups of commands and contents. These are described in Chapter 21, User Interface Variants.
When you set up Writer, you can choose one of these user interfaces, and you can switch between them and the standard interface at any time.
In three variants (Tabbed, Tabbed Compact, and Groupedbar Compact), the area at the top of the workspace is divided into tabs, where each tab displays a set of icons grouped by context. The context can change depending on the object selected in the document, for example a table or an image.
After one of these variants has been selected (using View > User Interface), you can use the checkboxes on the Notebookbar tab of the Customize dialog (Figure 26) to show and hide the individual options on the various tabs that are provided in the Tabbed mode user interface.
Use the Reset button to reset the selected configuration to the default settings.

Assigning shortcut keys
======================================================================

In addition to using the built-in keyboard shortcuts, you can define others. You can assign shortcuts to standard LibreOffice functions or your own macros and save them for use with Writer or with the entire LibreOffice suite.
To adapt shortcut keys to your needs, use the Keyboard tab of the Customize dialog (Figure 27).
    1) Choose whether to have the shortcut key assignment available in all components of LibreOffice or only in Writer.
    2) Select the desired shortcut key in the Shortcut Keys list at the top of the page.
    3) Select the required function in the Category and Function lists.
    4) Click the Modify button. The selection now appears in the Keys list on the lower right.
    5) Click OK to accept the change.
Repeat as required.

    • Note
Shortcut keys that are grayed-out in the listing on the Customize dialog, such as F1 and F10, are not available for reassignment.

Saving changes to a file
----------------------------------------------------------------------

Changes to the shortcut key assignments can be saved in a keyboard configuration file for use at a later time, so you can create and apply different configurations as needed. To save keyboard shortcuts to a file:
    1) After making keyboard shortcut assignments, click the Save button at the right of the Customize dialog (Figure 27).
    2) On the Save Keyboard Configuration dialog, type a name for the keyboard configuration file in the File name box, or select an existing file from the list. Browse to the location where you want to save the file. (The file extension is .cfg for Configuration.)
    3) Click Save. A confirmation dialog appears if you are about to overwrite an existing file, otherwise there will be no feedback and the file will be saved.

Loading a saved keyboard configuration
----------------------------------------------------------------------

To load a saved keyboard configuration file and replace your existing configuration, click the Load button on the Customize dialog, and then select the configuration file on the Load Keyboard Configuration dialog.

Resetting the shortcut keys
----------------------------------------------------------------------

To reset all of the keyboard shortcuts to their default values, click the Reset button on the Customize dialog. Use this feature with care; no confirmation dialog will be displayed.

Assigning macros to events
======================================================================

In LibreOffice, when something happens, we say that an event occurred. For example, a document is opened, a key is pressed, or the mouse moved. You can associate a macro with an event, so the macro is run when the event occurs. For example, a common use is to assign the “open document” event to run a macro that performs certain setup tasks for the document.
To associate a macro with an event, use the Events tab of the Customize dialog. For more information, see the Getting Started Guide.
Adding functionality with extensions
An extension is a package that can be installed into LibreOffice to add new functionality. Template sets, spelling dictionaries, clipart galleries, macros, and dialog libraries can be packaged as LibreOffice extensions. They can add new top-level menus, submenus or toolbar icons. Extensions may also have their own settings.
Several extensions are shipped bundled with LibreOffice and are installed with the program. These can only be removed by changing the installation options. Others can be downloaded from various websites. The official extension repository is located at https://extensions.libreoffice.org/. These extensions are free of charge.
Some extensions from other sources are free of charge; others are available for a fee. Check the descriptions to see what licenses and fees apply to the ones that interest you.
Download the extension to your computer in any folder that you want (usually Downloads).

Installing extensions
----------------------------------------------------------------------

To install an extension that is listed in the repository, follow these steps:
    1) In LibreOffice, select Tools > Extensions on the Menu bar.
    2) In the Extensions dialog (Figure 28), click Get more extensions online.
    3) An internet browser window opens. Find and select the extension you want to install and download it to your computer.
    4) After the extension is downloaded and saved, return to the Extensions dialog and click Add. Find and select the extension you want to install and click Open. The extension begins installing. You may be asked to accept a license agreement.
    5) When the installation is complete, the extension is listed in the Extensionsr dialog.
To install an extension that is not listed in the repository, download the extension, then continue with step 3 above.

Updating extensions
----------------------------------------------------------------------

Click the Check for Updates button on the Extensions dialog to check for updates to installed extensions.

Removing and disabling extensions
----------------------------------------------------------------------

To remove (uninstall) an extension that you installed, select the extension in the main window of the Extensions dialog and click the Remove button.
To disable an extension without removing (uninstalling) it, select the extension in the main window of the Extensions dialog and click the Disable button, which then changes to Enable.

Adding fonts
======================================================================

LibreOffice supports PostScript (.pfb), TrueType (.ttf), and OpenType (.otf) font file formats. Other font formats exist, and may be supported by your operating system, but these formats may be limited in selection and quality.
If you have administration privileges, you can install additional fonts through your operating system; they will then be available for use by LibreOffice and will appear in Writer’s font lists.

Finding free-licensed fonts
----------------------------------------------------------------------

In addition to proprietary fonts from sources like Adobe, hundreds of free-licensed fonts are available. You can use, share, and edit free-licensed fonts as you please. Most are available at no cost. Many are clones or near-variations of classic fonts, but some are original fonts.
Many Linux distributions include a few free-licensed fonts in their package repositories. Other places where you can find free-licensed fonts include The League of Moveable Type (https://www.theleagueofmoveabletype.com/) and the Font Library (https://fontlibrary.org/).

Adding custom colors
======================================================================

To add custom colors to a color palette, for example to exactly match a corporate color scheme, follow this procedure:
    1) Insert any drawing object, such as a square, into any document.
    2) Right-click on the object and choose Area in the context menu.
    3) Go to the Color tab (Figure 29). Under Colors > Palette, choose which palette you wish to add the new color to. Under New, define the new color using RGB or Hex notation, or click the Pick button to select the color on the Pick a Color dialog (Figure 30).

    4) Click Add in the lower left corner, enter a name for the new color in the pop-up dialog, and click OK to save.
    5) Delete the drawing object from the document, if it is not needed.

Setting up document themes
======================================================================

Document themes collect various format selections into a set that can be applied and changed with two clicks. Theme colors have been implemented in LibreOffice Writer 7.6; font and format settings are planned for a later release.
LibreOffice supplies several sets of theme colors. To define your own set:
    1) Choose Format > Theme on the Menu bar. In the Theme dialog (Figure 31), select a theme to use as a starting point and click Add.
    2) In the Theme Color Edit dialog (FIgure 32), name the new theme and select colors from any available palette.
    3) Click OK to save the new theme, which will now appear in the Theme dialog.
See Chapter 6, Formatting Page: Advanced, for instructions on using document themes.
    • Note
User-defined theme color sets are saved only in the document; to use them in other documents, you need to make a template.
Themes enhance compatibility with Microsoft Word. However, they are not yet part of ODF (OpenDocument Format), so you need to save to ODF 1.3 Extended to use them.
