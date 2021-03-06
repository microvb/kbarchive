---
layout: page
title: "Q197286: Third-Party Services May Fail to Start After Upgrade to NT SP4"
permalink: /kb/197/Q197286/
---

## Q197286: Third-Party Services May Fail to Start After Upgrade to NT SP4

{% raw %}

	Article: Q197286
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	After installing Windows NT 4.0 Service Pack 4, some third-party services may
	fail to start.
	
	CAUSE
	=====
	
	This problem occurs because Windows NT 4.0 Service Pack 4 changes the Services
	startup order.
	
	RESOLUTION
	==========
	
	To correct this problem, contact the third-party software vendor for help in
	determining which Windows NT services need to be started before the specific
	third-party service must be started. After these services have been identified,
	proceed with the following registry modifications.
	
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
	
	1. Run Registry Editor (Regedt32.exe).
	
	2. From the HKEY_LOCAL_MACHINE hive, go to the following key:
	
	     \SYSTEM\CurrentControlSet\Services\<third-party service>
	
	3. From the Edit menu, select Add Value.
	
	4. Add the following:
	
	     Value Name: DependOnService
	     Data Type:  REG_MULTI_SZ
	     Data:       <svc_name>
	
	  NOTE: <svc_name> Indicates the NT service that is needed to have already
	  been started for this service to start.
	
	5. Click OK and quit Registry Editor.
	
	6. Shut down and restart Windows NT.
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
