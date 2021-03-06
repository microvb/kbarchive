---
layout: page
title: "Q163017: Cannot Run Applications after Making File Association"
permalink: /kb/163/Q163017/
---

## Q163017: Cannot Run Applications after Making File Association

{% raw %}

	Article: Q163017
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	By default, exe and .exe file extensions cannot be used in Windows NT 4.0
	because they are reserved for running programs. However, the extension *.exe can
	be used as a valid file extension when creating a new application association.
	If you create an association with the *.exe extension, you will no longer be
	able to run applications or programs.
	
	CAUSE
	=====
	
	The Add New File Type dialog box in Windows NT 4.0 allows for longer file
	extensions than Windows NT 3.51, which only allowed 4 characters.
	
	RESOLUTION
	==========
	
	If the *.exe association has been made and/or removed, you can add the default
	.exe file type back by using Registry Editor. You can also use the Emergency
	Repair Disk to recover the registry information.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	1. Start Registry Editor (Regedt32.exe), and select the following key:
	
	  HKEY_CLASSES_ROOT on Local Machine
	
	2. From the Edit menu, click Add Key.
	
	3. In the Key Name box, type ".exe" (without the quotation marks) and then click
	  OK.
	
	4. Select the new .exe key.
	
	5. From the Edit menu, click Add Value.
	
	6. In the Value Name box, type "Content Type" (without the quotation marks).
	  Select REG_SZ for Data Type, and then click OK.
	
	7. In the String box, type "application/x-msdownload" (without the quotation
	  marks) and then click OK.
	
	8. From the Edit menu, click Add Value.
	
	9. Leave the Value Name box blank. Select REG_SZ for Data Type, and then click
	  OK.
	
	10. In the String box, type "exefile" (without the quotation marks) and then
	  click OK.
	
	11. Exit Registry Editor.
	
	All application and program functionality should now be restored to its original
	state.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	Additional query words: apps blue screen
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
