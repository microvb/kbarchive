---
layout: page
title: "Q182123: FP: No Access to Form Properties by Right-Clicking Form Field"
permalink: /kb/182/Q182123/
---

## Q182123: FP: No Access to Form Properties by Right-Clicking Form Field

{% raw %}

	Article: Q182123
	Product(s): Word Front Page
	Version(s): MACINTOSH:1.0; WINDOWS:1.1,97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 04-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows 1.1 
	- Microsoft FrontPage for the Macintosh, version 1.0 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2000 version of this article, see Q197735.
	
	For a Microsoft FrontPage 98 version of this article, see Q193959.
	
	SYMPTOMS
	========
	
	In FrontPage Editor, you cannot access a form's properties when you do one of
	the following:
	
	- Right-click a form field. The Form Properties command does not appear on the
	  shortcut menu.
	
	  -or-
	
	- Right-click a push button, click Form Field Properties, and then click the
	  Form button. In this case nothing happens.
	
	CAUSE
	=====
	
	This behavior occurs when your form field is not within a form. A dashed line
	that surrounds one or more form fields denotes a form.
	
	RESOLUTION
	==========
	
	To access the form properties, your form field must be inside the dashed line
	that denotes the form. Use one of the following methods to resolve this behavior
	so that you can access the form's properties.
	
	Method 1: If You Have a Form on the Page
	----------------------------------------
	
	1. Select the form field.
	
	2. On the Edit menu, click Cut.
	
	3. Click anywhere inside the form (the dashed lines).
	
	4. On the Edit menu, click Paste.
	
	5. Right-click the form field and click Form Properties on the menu that
	  appears.
	
	Method 2: If You Do Not Have a Form on the Page
	-----------------------------------------------
	
	1. Select the form field.
	
	2. On the Insert menu, point to Form Field, and then click the form field option
	  you want.
	
	3. Right-click the form field and click Form Properties on the menu that
	  appears.
	
	
	Additional query words: 97
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbHWMAC kbOSMAC kbFrontPageSearch kbZNotKeyword8 kbFrontPage1xSearch kbFrontPage97Search kbFrontPageMac kbZNotKeyword3 kbFrontPage110
	Version           : MACINTOSH:1.0; WINDOWS:1.1,97
	Hardware          : MAC x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
