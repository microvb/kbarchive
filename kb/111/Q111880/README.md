---
layout: page
title: "Q111880: AWFAX Hangs When Faxing a Microsoft Works for Windows Document"
permalink: /kb/111/Q111880/
---

## Q111880: AWFAX Hangs When Faxing a Microsoft Works for Windows Document

{% raw %}

	Article: Q111880
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 07-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to send a Microsoft Works version 3.0 for Windows document using
	Microsoft At Work PC Fax while Works for Windows is running, the machine stops
	responding (hangs).
	
	CAUSE
	=====
	
	This problem occurs because Microsoft At Work PC Fax calls a ShellExecute
	routine for the Microsoft Works for Windows document while Works for Windows is
	still running. ShellExecute launches a new instance of Works for Windows and
	returns this instance to Microsoft At Work PC Fax. The new instance of Works for
	Windows discovers the previous instance and terminates after requesting that the
	previous instance prints on its behalf. Microsoft At Work PC Fax waits for the
	instance generated by ShellExecute to begin printing; therefore, the machine
	hangs.
	
	WORKAROUND
	==========
	
	To work around this problem, do one of the following:
	
	- If you want to send the document in facsimile format, use the print method
	  (that is, choose Print from the File menu in Works for Windows and select the
	  Microsoft At Work PC Fax printer driver).
	
	  -or-
	
	- If you are attaching a Works for Windows document to a Microsoft Mail
	  message, make sure that Works for Windows is not already running.
	
	Additional query words: appnote 3.11 efax awfax wfw wfwg msworks w_works
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311
	Version           : WINDOWS:3.11
	
	=============================================================================
	

{% endraw %}
