======================================================================
Writer Guide Chapter 18, Forms ノート
======================================================================

.. include:: ./abbrev.txt

.. contents:: 章見出し
   :depth: 3
   :local:

Introduction
======================================================================

This chapter covers the use of interactive forms within Writer documents. A form has sections that are not to be edited, and other sections that are designed for the reader to make changes. For example, a questionnaire has an introduction and questions (which do not change) and spaces for the reader to type answers or select from supplied choices.
Writer provides several ways to enter information into a form, including check boxes, option buttons, text boxes, pull-down lists, and other items, collectively known as form controls.
LibreOffice forms include a lot of features. Not everything is described in this chapter. Notable omissions are using forms in HTML documents and writing macros to link to form controls.
LibreOffice Calc, Impress, and Draw also support forms in much the same way that Writer does.

When to use forms
======================================================================

Forms are used in three ways:
    • To create a simple document for the recipient to complete, such as a questionnaire sent out to a group of people who fill it in and return it.
    • To link into a database or data source and allow the user to enter information. Someone in a sales department might enter purchasers’ information into a database using a form.
    • To view information held in a database or data source. A librarian might call up information about books.
Using forms to access a database offers a fast and easy way to build complex graphical front ends. Your form can include not only the fields that link to the data source, but also text, graphics, tables, drawings and other elements.
A typical way to use a simple form is:
    1) You design the form, then save it.
    2) You send the form to others (for example, by email).
    3) They fill in the form, save it, and send it back to you.
    4) You open the form and see what their answers are.
    • Tip
By using a data source, or setting a form to update over the web, you can gather data automatically. However, those methods are more complex and are not covered in this chapter.

Alternatives to using forms in Writer
----------------------------------------------------------------------

LibreOffice Base provides an alternative way to access a data source. Forms in Base and Writer share a lot of similarities, but one may be better for a particular task than the other. Base is appropriate only if the form accesses a data source; you would not use it for simple forms.

Creating a simple form
======================================================================

This topic explains how to create a simple form without any links to a data source or database and without advanced customization.

Create a document
----------------------------------------------------------------------

You do not need to do anything special when creating a document to use as a form, though you may wish to enable the grid so that controls can be positioned accurately. Go to View > Grid and Helplines on the Menu bar and select Display Grid. You may also wish to select Snap to Grid.
Create a new Writer document with File > New > Text document.

Open the form toolbars
----------------------------------------------------------------------

Two toolbars control form creation: Form Controls (Figure 2) and Form Design (Figure 3). Select View > Toolbars > Form Controls and View > Toolbars > Form Design on the Menu bar to show them both. You can also open the Form Design toolbar on the Form Controls toolbar.
The Form Controls toolbar has an icon for each of the most commonly used types of control. Some of these controls are also located on the Form menu (Figure 1).
You can dock these toolbars in different places on the Writer window, or leave them floating. When they are floating, you can also change them from vertical to horizontal and change the number of tools on a row; to make these changes, drag a corner of the toolbar.
See “Form controls reference” on page 6 for descriptions of the tools on these toolbars.

Activate design mode
----------------------------------------------------------------------

Click the Design Mode icon on the Form Controls toolbar to turn design mode on. (Click it again to turn it off.) This activates or deactivates the icons for inserting form controls and selects controls for editing.
When design mode is off, the form behaves as it would for the end user. Buttons can be pressed, check boxes selected, list items selected, and so on.

Insert form controls
----------------------------------------------------------------------

    1) To insert a form control into the document, click the control’s icon to select it. The mouse pointer changes shape.
    2) Click in the document where you want the control to appear. (You can move it later.)
    3) Hold the left mouse button down and drag the control to size it. Some controls have a fixed size symbol followed by the name of the control (for example, Check Box or Option Button).
    4) The control icon remains active, so you can insert several controls of the same type without needing to go back to the toolbar.
    5) To change to another tool, click its icon on the toolbar.
    6) To stop inserting controls, click the Select icon on the Form Controls toolbar, or click any of the controls you have just inserted. The mouse pointer changes back to its normal appearance.
    • Tip
To make a form control square, hold down the Shift key when creating it. To keep the proportions of an existing control the same, hold down Shift when resizing it.

Configure controls
----------------------------------------------------------------------

After inserting the controls, you need to configure them to look and behave as you want. Right-click a form control within the document and select Control in the context menu, or double-click on a form control, to open the Properties dialog for the selected control.
The Properties dialog has three tabs: General, Data, and Events. For simple forms, only the General tab is needed. See “Configure form controls” on page 11, “Form control formatting options” on page 21, and the descriptions in the Help for more information. Configuration for use with a database is discussed in “Creating a form for data entry” on page 17.
The fields on this dialog vary with the type of control. To see additional fields, use the scroll bar or enlarge the dialog vertically.

Use the form
----------------------------------------------------------------------

To use the form, leave design mode by clicking the Design Mode icon to deactivate it. Save the form document.

Form controls reference
======================================================================

Form menu on Menu bar

Form Controls toolbar
The icons you see in Writer may differ from the ones shown here or they may be in a different order on the toolbar.

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

In this example, we will create the form shown in Figure 4. If you follow the given steps, your form will look similar to this one.

Create the document
----------------------------------------------------------------------

Open a new document (File > New > Text Document) and type any text to be included (see Figure 5 for an example). It is a good idea to sketch the final result to use as a guide when designing the form, although it can easily be changed later.

Add form controls
----------------------------------------------------------------------

The next step is to add the form controls to the document. We will have four controls:
    • Name is a text box.
    • Gender is three option buttons: male, female, or other; user can select one.
    • Favorite shape is a list of options; user can select one.
    • All shapes you like is a series of check boxes; user can select one or more.
To add these controls:
    1) Select View > Toolbars > Form Controls to open the Form Control toolbar.
    2) If the tools are not active, click the Design Mode icon to activate them.
    3) Click the Text Box icon, then click in the document and drag the shape of the Name text box to approximately the size you want. Drag it to line up with the Name: label.
    4) Make sure Toggle Form Control Wizards is OFF. Click the Option Button icon. Click and drag to create three option buttons near the Gender: label in the document. We will configure these in the next section.
    5) Click the List Box icon and draw a list box by Favourite shape: in the document. This will just be an empty pane for now.
    6) Click the Check Box icon and create four check boxes by All shapes you like, side by side across the page.
Your document should now look something like Figure 6. Do not worry if the controls are not lined up well; we will fix this later.

Configure form controls
----------------------------------------------------------------------

Text box
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No further configuration is required for the Name field, but you may wish to change the height or width of the field, its background color, or other formatting. If so:
    1) Be sure Design Mode is on and Wizards are off.
    2) Double-click on the Name field to open the Properties: Text Box dialog (Figure 7).
    3) On the General tab, scroll down (or expand the dialog by dragging the bottom edge down) to find the Width and Height properties. Change these as needed.
    4) You can then close the dialog or leave it open while you configure the other controls.

Option buttons
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Gender option buttons need to be configured to allow only one of the three to be selected. You can do this in two ways: using individual option buttons as described here, or using a Group Box (see page 14).
    1) Be sure Design Mode is ON and Wizards are OFF.
    2) If the Properties dialog is open, click once on the first option button to change the dialog to Properties: Option Button. If the dialog is not open, double-click the first option button. In the Properties dialog (Figure 8), on the General tab, type Male in the Label field and Gender in the Group name field.
    3) Repeat for the other two options, using Female and Other, respectively, for the Label and Gender for the Group name. (Grouping allows only one option to be selected at a time.)

If the option buttons are too far apart, click on each in turn and drag it to the left or right.
If the option buttons are not lined up neatly, do this:
    1) Click the Select button on the Form Controls toolbar and draw a box around the three option button controls with the mouse to select all of them (Figure 9).
    2) Right-click and choose Align > Top in the context menu. Figure 10 shows the result.

List box
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To add the list of choices to the list box, do this:
    1) Be sure Design Mode is ON and Wizards are OFF. Double-click the List Box control to open the control’s Properties dialog (Figure 11). Select the General tab.
    2) Scroll down to find the List Entries text input box. Type the names of the shapes (Circle, Triangle, Square, Pentagon) one at a time. After each, press Shift+Enter, as shown in Figure 11.

       When you click away from the List entries box in the dialog, you should see a line saying "Circle";"Triangle";"Square";"Pentagon" (Figure 12).

Check boxes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To give the check boxes names:
    1) Be sure Design Mode is ON and Wizards are OFF. Double-click the first Check Box control.
    2) In the Properties: Check Box dialog (Figure 13), change the text in the Label field to Circle and press Enter. The cursor moves to the next line, and the label on the check box in the document changes immediately.

    3) Click each of the other three check boxes in turn. Change the text in the Label text input box in the Properties dialog to Triangle, Square, and Pentagon in turn.
    4) Close the Properties dialog.
    5) Turn Design Mode off.
You have now completed the form, which should look something like Figure 4 on page 10.

Group box
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As an alternative to creating individual option buttons for Gender (described on page 12), you can use a Group Box to insert a group of option buttons. Group boxes stack the selections one under the other (as shown in Figure 17 on page 16); individual buttons can be moved into any arrangement you prefer (we arranged them horizontally on page 12).
To use a Group Box instead of individual Option Buttons:
    1) Be sure both Design Mode and Wizards are ON. Click the Group Box icon and draw a box next to the Gender: label. The Group Element Wizard (Figure 14) opens automatically.
    2) Type Male in the box on the left. Click the >> button to move it to the Option fields box on the right.
    3) Repeat for Female and Other. The Wizard should now look like Figure 15. Click Next >.
    4) On the next page of the Wizard (Figure 16), choose No, one particular field is not going to be selected as a default. Click Next >.
    5) On the next page, make no changes. Click Next >.
    6) On the next page, delete the words “Group Box” from the caption area. If we did not have a Gender: label already in the form, you might want to type Gender as the caption.
    7) Click Finish. The survey form should look like Figure 17.

Finishing touches
----------------------------------------------------------------------

The form is complete, but you may wish to make further changes to the document. If you plan to send this out to other people to complete, you probably want to make the document read-only so that users would be able to fill in the form but not make any other changes to the document.
To make the document read-only, select File > Properties, select the Security tab and enable Open file read-only.
    • Note
If the document is read-only, anyone filling in the form will need to use File > Save as to save the document.

Accessing data sources
======================================================================

The most common use for a form is to input information into a database. For example, you can design a form that others can use to enter information into a contacts database. Because it is part of a Writer document, the form can contain graphics, formatting, tables, and other elements to make it look just the way you want. Modifying the form is as simple as editing a document.
LibreOffice can access numerous data sources. These include ODBC, MySQL, Oracle JDBC, spreadsheets and text files. As a general rule, databases can be accessed for reading and writing; other data sources (such as spreadsheets) are read-only.
    • Tip
To see the list of supported data source types for your operating system, choose File > New > Database. On the first page of the Database Wizard, select Connect to an existing database and then open the drop-down list.
For the purpose of this chapter, we assume you have previously created a database or other data source and registered it for use with Writer. Chapter 14, Mail Merge, describes how to create and register a database.

Creating a form for data entry
----------------------------------------------------------------------

Once a database is registered with LibreOffice, follow these steps to link a form to the data source:
    1) Create a new document in Writer (File > New > Text Document).
    2) Design your form, without putting in the actual fields (you can always change it later).
    3) Show the Form Controls and Form Design toolbars.
    4) Click the Design Mode icon to put the document into design mode.
    5) Click the Text Box icon. Click in the document and drag to create a text box for the first form field.
    6) Additional fields, of any type, can be added in the same way (click and drag).
So far you have followed the same steps used before when creating your first form. To link the form with the data source you registered:
    1) Click the Form Properties icon on the Form Design toolbar, or right-click any of the fields you inserted and select Form Properties, to open the Form Properties dialog (Figure 18).

    2) In the Form Properties dialog, choose the Data tab.
    • Set Data Source to be the data source you registered.
    • Set Content Type to be Table.
    • Set Content to be the name of the table you want to access.
    • Close the dialog.
    3) For each form control in turn, click the control to select it (small green boxes appear around it), then launch the Properties dialog: either right-click and select Control Properties or click the Control Properties icon on the Form Controls toolbar.
    4) In the Properties dialog, click the Data tab (Figure 19). If you set up the form correctly, the Data Field option will contain a list of the different fields in the data source (for example, Name, Address and Telephone). Select the field you want.

    5) Repeat for each control in turn until every control that should be assigned to a field has been assigned.
    • Caution
If you created a database in LibreOffice Base and your Primary Key field had AutoValue set to Yes, that field does not need to be part of the form. If AutoValue was set to No, you will have to include it and users will need to enter a unique value into that field whenever they make a new entry—not something that is recommended.

Entering data into a form
----------------------------------------------------------------------

Once you have created a form and tied it to a database, use it to enter data into the database or modify data already there:
    1) Make sure that the form is not in design mode. (On the Form Controls toolbar, click the Design Mode icon. When design mode is off, most of the buttons on the toolbar will be grayed out.)
    2) Make sure that the Form Navigation toolbar is on (View > Toolbars > Form Navigation). This toolbar normally appears at the bottom of the workspace.

    3) If there is existing data in the data source, use the control buttons on the Form Navigation toolbar to look at different records. To amend data in a record, edit the values in the form. To submit the changes, press Enter with the cursor in the last field. The record is saved and the next record is displayed.
    4) If there is no data in the form, enter information by typing into the fields of the form. To submit the new record, press Enter with the cursor in the last field.
    5) Other functions can be performed from the Form Navigation toolbar, including deleting a record and adding a new record.
    • Note
If a user tries to fill in the form and receives the error “Attempt to insert null into a non-nullable column”, then the form designer should go back to the database and confirm that the Primary Key field has the Auto Value set to Yes. This error will prevent the form user from saving the records.

Advanced form customization
======================================================================

Linking a macro to a form control
----------------------------------------------------------------------

You can set any form control (for example, text box or button) to perform an action when triggered by some event.
To assign a macro to an event:
    1) Create the macro. See Chapter 13, Getting Started with Macros, in the Getting Started Guide.
    2) Be sure the form is in design mode. Right-click the form control, select Control Properties in the context menu, and click the Events tab (Figure 21).

    3) Click the browse icon by any event to open the Assign Action dialog (Figure 22).
    4) Click the Macro button and select the macro from the list in the Macro Selector dialog (not shown). You return to the Assign action dialog. Repeat as needed, then click OK to close the dialog.
Macros can also be assigned to events relating to the form as a whole. To do this, right-click a form control in the document, select Form Properties, and click the Events tab.

Fine-tuning database access permissions
----------------------------------------------------------------------

By default, when a database is accessed from a form, any changes can be made to it: records can be added, deleted, and amended. You may not want that behavior. For example, you may want users to be able only to add new records or to be prohibited from deleting existing records.
In design mode, right-click a form control and select Form Properties in the context menu. On the Data tab of the Form Properties dialog (Figure 23), set each of these options to Yes or No to control the access users have to the data source: Allow additions, Allow deletions, Allow modifications, and Add data only.
Individual fields can also be protected. This might be useful if you wanted a user to be able to modify some parts of a record but only view others, such as a stock list where item descriptions are fixed and quantities can be modified.
To make an individual field read-only, in design mode, right-click the form control within the document and select Control from the context menu. Select the General tab and set Read-only to Yes.

Form control formatting options
----------------------------------------------------------------------

You can customize the way form controls look and behave in a number of ways. These are all accessed in design mode. Right-click the form control, select Control Properties in the context menu and select the General tab in the Properties dialog.
    • Set a label for the control in the Label box (not to be confused with the box called Label Field). Some form controls, such as push buttons and option buttons, have visible labels that can be set. Others, such as text boxes, do not.
    • Set whether the form control will print out if the document is printed with the Print option.
    • Use the Font setting to set the font, typeface, and size for a field’s label or for text typed into a field. This setting does not affect the size of check boxes or option buttons.
    • For a text box, you can set the maximum text length. This is very useful when adding records into a database. Every database text field has a maximum length and, if the data entered is too long, LibreOffice displays an error message. By setting the maximum text length of the form control to be the same as that of the database field, this error can be avoided.
    • You can set the default option for a form control. By default, a control is blank, or has every option unselected. You can set the control to start with a particular option or list item selected.
    • For controls where a password is being entered, setting the Password character (for example to *) displays only that character, but saves what the user really types.
    • You can add additional information and help text for a form control.
    • You can use other formatting controls such as background color, 3-D look, text formatting, scroll bars, and borders to further define how the control appears.

Using content controls
======================================================================

Content controls are placeholders. You can add and customize content controls for use in templates, forms, and documents. Content controls can provide instructions on their use. Some are similar to the controls described earlier in this chapter, but can be easier to work with and format. However, unlike some fields, content controls do not connect to any data in a database.
Rich Text
Contains custom formatted text or other items, such as tables, pictures, or other content controls.
Plain Text
Limited to plain text in a single or multiple paragraphs. Unlike rich text, it cannot contain other items, such as tables, pictures, or other content controls.
Picture
Contains a single image anchored as-character. Clicking on the content control opens the file open dialog to select an image to replace the placeholder.
Check Box
Contains a single check box character to interact with. Clicking on the content control toggles the checked state of the check box.
Combo Box
Contains a drop-down selection of list entries that you can select and text box that you can edit directly.
Drop-down List
Contains a drop-down button control with a list of display-text and value pairs. Unlike a combo box, the drop-down list does not let users enter custom input.
Date
Contains a calendar control. Limits text to a single paragraph.
To insert a content control into a document, template, or form:
    1) Place the cursor where you want the control to appear.
    2) Choose Form > Content Controls > Insert [Required Control] on the Menu bar.
    3) Choose Form > Content Controls > Content Control Properties on the Menu bar. This is not available for a Picture conrol.
    4) On the Content Control Properties dialog (Figure 24), optionally select Content is placeholder text, type a title and a tag. The properties vary for each control. For details, please see the Help.
