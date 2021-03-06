---
layout: page
title: "Q142190: How to Create Mover List Boxes in Visual FoxPro"
permalink: /kb/142/Q142190/
---

## Q142190: How to Create Mover List Boxes in Visual FoxPro

{% raw %}

	Article: Q142190
	Product(s): Microsoft FoxPro
	Version(s): 3.00 3.00b
	Operating System(s): 
	Keyword(s): kbcode kbvfp300 kbvfp300b kbvfp600
	Last Modified: 25-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Moverlist boxes are designed to allow for easy point selection of a value that
	will display in a parallel list box enabling the user to create a list of items
	before proceeding. The code involved to make these list boxes work properly is
	very extensive in the Microsoft Visual FoxPro product. In the
	Vfp\Samples\Controls\Samples.vcx directory, you'll find a Mover Class that you
	can use to quickly create moverlist boxes with very little additional code. The
	example given in this article works for most, if not all, users.
	
	MORE INFORMATION
	================
	
	Step-by-Step Example
	--------------------
	
	1. Start a Visual FoxPro session.
	
	2. On the Tools menu, click Options, and then click the Controls tab.
	
	3. Make sure the Visual Class Libraries option is selected, and then click Add,
	  and select the following library:
	
	     Vfp\Samples\Controls\Samples.vcx
	
	  Samples should appear in the Selected box of the Options Dialog Box,
	
	4. Click Set As Default, then click OK.
	
	5. On the system's File menu, click New, click Form, and click New File. A blank
	  form will appear.
	
	6. Click the View Classes Button on the Forms Control Tool Bar, and select
	  Samples. The Forms Control Tool Bar has now changed.
	
	7. Click the Moverlists Button, click in the form, and the moverlists will
	  appear.
	
	8. Place the table that you intend to get the list value(s) from in the Data
	  Environment of the form.
	
	9. Place the following code in the Init event of the form:
	
	      SELECT <TABLENAME>
	      SCAN
	         THIS.MOVERLISTS1.LSTSOURCE.ADDLISTITEM(<FIELDNAME>)
	      ENDSCAN
	
	At this point, you can add any additional buttons, controls, or code depending on
	what the user would like the list boxes to do.
	
	Steps to Add Selected Items to a Database
	-----------------------------------------
	
	If you want to add the selected values to a .dbf file, follow these steps:
	
	1. Add the .dbf table to Data Environment of the form.
	
	2. Add a Command Button, and place the following code in its Click Event:
	
	     SELECT <NEWTABLENAME>
	     FOR I = 1 TO THIS.PARENT.MOVERLISTS1.LSTSELECTED.LISTCOUNT
	        APPEND BLANK
	        REPLACE <FIELDNAME> WITH ;
	           THIS.PARENT.MOVERLISTS1.LSTSELECTED.LISTITEM(I)
	     ENDFOR
	
	  The records that were selected have now been written to the table of your
	  choice.
	
	3. To immediately see the results of the APPEND command, add:
	
	     BROWSE
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbcode kbvfp300 kbvfp300b kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP600
	Version           : 3.00 3.00b
	
	=============================================================================
	

{% endraw %}
