---
layout: page
title: "Q221186: Printers May Not Install on Computers Created from Other Image"
permalink: /kb/221/Q221186/
---

## Q221186: Printers May Not Install on Computers Created from Other Image

{% raw %}

	Article: Q221186
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When adding a printer for the first time, the user will receive a pop-up message
	asking if he or she wants to overwrite existing drivers. The user will get this
	message even though the user never had this printer installed before. Even if
	the user answers "Yes" to the question, the driver will not install properly.
	The driver for the printer will not appear in the Spool\Drivers\W32x86\2 folder
	(for x86-based computers).
	
	CAUSE
	=====
	
	The problem is that the image that was used to create the system had this
	printer installed and entries are in the registry for this printer but the
	driver files are not present in the drivers folder.
	
	RESOLUTION
	==========
	
	Before the image is duplicated, use Registry Editor and delete the driver
	entries in the registry or be sure the %SystemRoot%\System32\Spool\Drivers
	folder is copied as part of the image.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To remove the entries in the registry, delete all entries under the following
	registry key:
	
	  HKEY_LOCAL_MACHINE\System\Currentcontrolset\Control
	  \Print\Environments\Windows NT <platform>\Drivers\Version-<x>
	
	For example, in the case of x86, a user would delete all entries under:
	
	  HKEY_LOCAL_MACHINE\System\Currentcontrolset\Control
	  \Print\Environments\Windows NT x86\Drivers\Version-2
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Windows NT version 4.0.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
