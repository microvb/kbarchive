---
layout: page
title: "Q180495: BUG: Pages of PageFrame Created with AddObject Method Invisible"
permalink: /kb/180/Q180495/
---

## Q180495: BUG: Pages of PageFrame Created with AddObject Method Invisible

{% raw %}

	Article: Q180495
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b; WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbHWMAC kbvfp
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using a multirow pageframe object, the currently selected page, pages on
	the same row, and controls contained on the selected page are not visible. This
	behavior only occurs when the TabStretch property of a pageframe is set to 0 -
	Multiple Rows.
	
	CAUSE
	=====
	
	When you add pages to a pageframe object using the AddObject method, Visual
	FoxPro may not correctly determine how the pages should display.
	
	RESOLUTION
	==========
	
	When you add pages to a pageframe object using the AddObject method, force
	recalculation of the page display by setting the TabStretch property of the
	pageframe to the existing TabStretch property value as shown below:
	
	     pageform.pageframe1.TabStretch=pageform.pageframe1.TabStretch
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a form called pageform.
	
	2. Add a pageframe object and set the following properties:
	
	     TabStretch : 0 - Multiple Rows - in Visual FoxPro version 5.x.
	     TabStretch : 0 - Stack         - in Visual FoxPro version 3.x.
	     Height     : 135
	     Width      : 330
	
	3. Create a program called Pageform.prg using the following code:
	
	        PUBLIC pageform
	        DO FORM pageform
	        DO WHILE pageform.pageframe1.PAGECOUNT < 12
	          lcpagename = "Page" + ALLTRIM(STR(pageform.pageframe1.PAGECOUNT+1))
	          pageform.pageframe1.ADDOBJECT(lcpagename,"Page")
	          pageform.pageframe1.ACTIVEPAGE=pageform.pageframe1.PAGECOUNT
	          lcpageadd="PageForm.PageFrame1."+lcpagename+ ;
	             ".AddObject('TextBox1','TextBoxa')"
	          &lcpageadd
	          pageform.REFRESH
	        ENDDO
	        RETURN
	
	        DEFINE CLASS textboxa AS TEXTBOX
	           TOP=25
	           LEFT=10
	           HEIGHT=20
	           WIDTH=100
	           VISIBLE=.T.
	        ENDDEFINE
	
	REFERENCES
	==========
	
	(c) Microsoft Corporation 1998, All Rights Reserved.
	Contributions by John Desch, Microsoft Corporation
	
	
	Additional query words: kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600
	
	======================================================================
	Keywords          : kbHWMAC kbvfp 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : MACINTOSH:3.0b; WINDOWS:3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
