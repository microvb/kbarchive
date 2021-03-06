---
layout: page
title: "Q163803: BUG: Cannot Set ImageList Property of Treeview Visually"
permalink: /kb/163/Q163803/
---

## Q163803: BUG: Cannot Set ImageList Property of Treeview Visually

{% raw %}

	Article: Q163803
	Product(s): Microsoft FoxPro
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbvfpkbbuglist
	Last Modified: 04-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A form containing the Treeview control suddenly loses the images shown in the
	Treeview. This happens after any property of the Treeview control was modified
	in the Form Designer.
	
	CAUSE
	=====
	
	Right-clicking on the Treeview control in the Form Designer reveals a context
	menu. The bottom bar of that menu opens the TreeCtrl Properties dialog box. That
	dialog box holds a PageFrame with three pages. Page 1 has the caption "General."
	It holds a stack of nine ComboBox controls, plus other objects. The fifth
	ComboBox from the top is labeled "ImageList" (without the quotes).
	
	Comctl32.ocx contains both the ImageList control and the Treeview control.
	
	With the version of Comctl32.ocx that originally came with Visual FoxPro 5.0 the
	ImageList to be used with the Treeview control could be selected from that
	ComboBox on the General page of the TreeCtrl Properties dialog box. The
	developer could drop the ComboBox down and see all of the ImageList controls on
	the current form. Typically that would be one, but the application design might
	require multiple ImageLists. A Treeview can be associated with any one of those,
	but only one.
	
	Several Microsoft developer products that have been released since the release of
	Visual FoxPro version 5.0 install a revised Comctl32.ocx.
	
	In the Form Designer of Visual FoxPro 5.0, the new version of Treeview no longer
	lists, in the TreeCtrl properties general page, the ImageLists that reside on
	the current form. It shows the expression <none>.
	
	Clicking the "Apply" button at the bottom of the page sets all of the properties
	to the settings shown, so the new ImageList property is "none."
	
	RESOLUTION
	==========
	
	The ImageList must be specified in code. For example, if the form has an
	ImageList in OLE container control "OleControl1," then in the Init event method
	for the OLE container control that holds the Treeview, add a command similar to
	the following:
	
	  
	
	     This.Object.Imagelist = Thisform.Olecontrol1.Object
	
	The above is only a suggestion. The specifics of the application determines where
	to make the modification and the appropriate syntax to use.
	
	NOTE: The symptoms listed in this article also apply to the ListView control. The
	code for a workaround using the ListView control follows:
	
	  
	
	     This.object.icon = thisform.olecontrol1.object
	     This.object.smallicon = thisform.olecontrol2.object
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	Use the following steps in Microsoft Visual FoxPro 5.0 for Windows:
	
	1. Modify a form that contains a TreeCtrl control.
	
	2. Modify any property of the Treeview within the TreeCtrl properties dialog box
	
	3. Click Apply, then OK. The value "<none>" is now saved as the ImageList
	  property. Consequently no ImageList is specified for the Treeview
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbbuglist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500
	Version           : 5.0
	
	=============================================================================
	

{% endraw %}
