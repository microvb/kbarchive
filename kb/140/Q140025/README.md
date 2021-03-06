---
layout: page
title: "Q140025: HOWTO: Add an Outline Control to a Form and Populate It"
permalink: /kb/140/Q140025/
---

## Q140025: HOWTO: Add an Outline Control to a Form and Populate It

{% raw %}

	Article: Q140025
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): kbDesigner kbvfp300 kbvfp500 kbvfp600
	Last Modified: 14-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Professional Edition of Visual FoxPro includes the Microsoft Outline control
	(Msoutl32.ocx). The outline control can be used to display information in a
	graphical hierarchical format, such as in file open dialog boxes. This article
	describes how to use the outline control in the Forms Designer to perform some
	common tasks.
	
	MORE INFORMATION
	================
	
	Adding an Outline to your Form
	------------------------------
	
	1. Create a new form.
	
	2. Add an OLE Container control to your form. In the OLE Container control
	  dialog box, click the Insert Control option, and select the Outline control
	  from the list of available controls. Click OK.
	
	3. Change the Name property of the control to oleOutline.
	
	Populating the Outline
	----------------------
	
	To add items to the outline, use the outline's AddItem method. The AddItem method
	takes two parameters -- the text you want to show in the outline and the list
	index of the item. The second parameter is optional.
	
	For example, the following line of code adds an item named Apples to the bottom
	of the outline:
	
	     Thisform.oleOutline.AddItem("Apples")
	
	The following line of code adds an item named Bananas to the second position in
	the list:
	
	     Thisform.oleOutline.AddItem("Bananas",2)
	
	How the ListIndex Property Affects the Items in Your Outline
	------------------------------------------------------------
	
	As each individual item is added to the outline, it is assigned a list index. The
	list index may be assigned manually by you when the item is added, or it may be
	automatically assigned by the Msoutl.ocx.
	
	The list index property affects the relative positioning of items within the
	outline. If you add an item and specify a listindex property, any items below
	the inserted item are moved down, and their respective listindex properties are
	changed. The following table shows initial list index properties, and how they
	are affected by inserting an item prior to the current list index:
	
	               Original      Insert List    Insert List
	Item Name       List Index    Index of 2     Index of 6
	---------------------------------------------------------
	Fruit           1                 1             1
	Vegetables      5                 6             7
	Meats           10                11            12
	
	The table indicates that the ListIndex property will change as items are added to
	the outline. This means that if you insert items, you may be inserting them at a
	different place than intended. This causes problems if you want to build a list
	of headings, and then insert items at the appropriate location under each
	heading.
	
	Because this property is volatile, you may want to build your outline in
	sequential order, and allow the Msoutl32.ocx to assign a list index
	automatically to each item as you add it to the outline. With this technique, as
	you add topics, you need to add all the subitems for that outline item before
	adding an item at the same hierarchical level.
	
	Indenting Items Appropriately in the Outline
	--------------------------------------------
	
	Each outline item has an associated Indent property. The Indent property can be
	set to a minimum value of 0. The maximum value will depend on the number of
	hierarchical levels in the current branch of the outline.
	
	- A value of zero (0) indicates that the item should be invisible. This is the
	  default value assigned by the AddItem method. You must set this to a value of
	  1 or higher to see the outline item. The first item in the outline is
	  considered the "root item" of the outline, and it must have an indentation
	  level of 0.
	
	- A value of 1 indicates that the item is displayed at the highest level of the
	  outline.
	
	- A value of 2 or higher indicates that the item is a subitem of the next
	  higher indentation level. You can use an indent level higher than 2, however,
	  the indent can only be set to a maximum of one higher than the indentation of
	  the item directly preceding it in the outline. If you try to set an indent
	  level greater than one more of the prior item, you will receive an error.
	
	The following line of code illustrates setting the Indent property of the second
	item in the outline to an indent level of 3:
	
	     thisform.oleOutline.indent(2) = 3
	
	NOTE: The indent level of an item can be at most 1 greater than the indent level
	of the item preceeding it.
	
	The HASSUBITEMS() function allows you to determine programmatically if a
	particular item has subitems associated with it.
	
	Changing the Display of the Pictures in the Outline
	---------------------------------------------------
	
	You can change the picture associated with the outline by setting one of the
	following properties. These properties determine the picture displayed when an
	outline item is expanded, closed, or is a subitem:
	
	  PictureOpen
	  PictureClosed
	  PictureLeaf
	
	You can also specify a picture to be substituted for a particular item that has
	subordinate items by setting the following properties:
	
	  PictureMinus PicturePlus
	
	The picture can be any small bitmap (.bmp file). You must set the picture for the
	entire outline. You can also use the Style property to determine which items are
	displayed with a particular item in the outline. Each outline item has an
	individual style property. You may decide to change the style property, for
	example, depending on whether an individual outline item has subitems associated
	with it:
	
	Setting   Description
	----------------------------------------
	  0      Text only.
	  1      Picture and text.
	  2      (Default) Plus/minus and text.
	  3      Plus/minus, picture, and text.
	  4      Tree lines and text.
	  5      Tree lines, picture, and text.
	
	Gaining Access to a Particular Outline Item
	-------------------------------------------
	
	Because the outline is a container object, it contains a control array property
	to allow you to gain access to particular items within the outline.
	
	The ListCount property of the outline returns the number of items in the
	outline.
	
	The List property allows you to gain access to an item in the outline by display
	order, regardless of the list index property setting for that item. The
	following line of code sets the text of the third outline item to Oranges:
	
	     ThisForm.oleOutline.list(3) = "Oranges"
	
	You may also want to use the ItemData property of the outline control. This
	property contains an array of all items currently in the outline.
	
	Obtaining the Text Associated with a Particular Outline Item
	------------------------------------------------------------
	
	Occasionally, you may want to determine the text associated with the item
	currently selected from the outline. You can do this by using the Text property
	as follows:
	
	     ThisForm.oleOutline.Text
	
	This property is read-only. You must use the LIST() function to change the text
	programmatically.
	
	Expanding and Collapsing Outline Sections
	-----------------------------------------
	
	The code to expand and collapse the outline is built into the functionality of
	the control. You do not need to write code to handle expansion and collapsing.
	However, you can affect a single item by setting its Expand property to true
	(.T.) or false (.F.) appropriately.
	
	Obtaining More Information on the Outline Control
	-------------------------------------------------
	
	This article is not a comprehensive list of all the methods and properties
	associated with the Msoutl32.ocx. To obtain more information, query using
	"outline control" in the Visual FoxPro Help file.
	
	To view a sample form containing an outline control, open the
	Vfp\Samples\Ole\Outline1.scx file supplied with Visual FoxPro.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDesigner kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
