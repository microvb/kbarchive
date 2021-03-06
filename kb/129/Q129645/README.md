---
layout: page
title: "Q129645: PRB: GETDIR() Doesn't Behave as Expected Under System 7.5"
permalink: /kb/129/Q129645/
---

## Q129645: PRB: GETDIR() Doesn't Behave as Expected Under System 7.5

{% raw %}

	Article: Q129645
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c,2.6a,3.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c, 2.6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The GETDIR() function should display the Select Directory dialog from which a
	directory or folder can be chosen. It takes two arguments <expC1> and
	<expC2>. The first argument <expC1> specifies the folder that is
	initially displayed in the Select Directory dialog. The second argument
	<expC2> is the prompt for the folder in the Select Directory dialog. In
	FoxPro for Macintosh and Visual FoxPro for Macintosh, specifying the folder that
	is displayed initially does not behave as expected if running System 7.5 or
	System 7.5.3.
	
	CAUSE
	=====
	
	This problem occurs on System 7.5 and System 7.5.3.
	
	STATUS
	======
	
	This behavior is by design. It is caused by a setting in the "General Controls"
	Control Panel on System 7.5. "General Controls" contains a section indicating
	where to open and save documents. This setting overrides the SET DEFAULT and
	other specified directories in FoxPro functions.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. From the File menu, choose Open, and notice the currently selected (or
	  default) folder. (The default folder should be Microsoft FoxPro 2.6 or
	  Microsoft Visual FoxPro unless you have specified otherwise in the CONFIG.FPM
	  file.)
	
	2. Click Cancel.
	
	3. In the Command window, issue this command:
	
	     =GETDIR("MAC HD:Microsoft FoxPro 2.6:Tutorial")
	
	  * or any valid Visual Foxpro folder
	
	4. The Select Directory dialog opens. However, the folder displayed is not
	  Tutorial. It is displaying the default or last working folder.
	
	NOTE: Issuing a SET DEFAULT TO <desired folder name> before issuing the
	GETDIR() function does not change the initial folder displayed.
	
	Additional query words: vFoxMac FoxMac
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro250bMac kbFoxPro260aMac kbFoxPro250cMac kbVFP300bMac
	Version           : MACINTOSH:2.5b,2.5c,2.6a,3.0b
	
	=============================================================================
	

{% endraw %}
