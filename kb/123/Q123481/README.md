---
layout: page
title: "Q123481: Limit of Two Concurrent Print Queues from Windows NT to LANMan"
permalink: /kb/123/Q123481/
---

## Q123481: Limit of Two Concurrent Print Queues from Windows NT to LANMan

{% raw %}

	Article: Q123481
	Product(s): Microsoft Windows NT
	Version(s): 3.10 | 2.20
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	3.10    | 2.20
	
	WINDOWS | OS/2
	
	kbprint kbnetwork kbbug3.10 kbfix3.10.sp3 kbfix3.50
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft LAN Manager, version 2.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a computer running Windows NT version 3.1 is configured to redirect several
	print queues from a LAN Manager for UNIX 2.2 server, the system reports the
	following in the event log:
	
	  System Error 1220
	  AN ATTEMPT WAS MADE TO ESTABLISH A SESSION TO A LANMANAGER SESSION BUT THERE
	  ARE TOO MANY SESSIONS ALREADY ESTABLISHED.
	
	Print jobs also stack up as they wait their turn to print and the server beeps
	continually.
	
	CAUSE
	=====
	
	This error occurs because of a Windows NT redirector limit of two sessions with
	an OS/2 server.
	
	Some OS/2 and LAN Manager for UNIX servers can only handle two login sessions
	from one client. The Windows NT version 3.1 redirector can't tell whether the
	OS/2 server is one that supports only two logons, or if it supports more, so it
	tries two (even though Microsoft LAN Manager version 2.2 supports more than
	two).
	
	RESOLUTION
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	To resolve this issue:
	
	1. Upgrade to Windows NT version 3.5.
	
	2. Run Registry Editor (REGEDT32.EXE).
	
	3. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  \SYSTEM\CurrentControlSet\Services\Rdr\Parameters
	
	4. From the Edit menu choose Add Value.
	
	5. Add the following:
	
	     Value Name: Os2SessionLimit
	     Data Type:  REG_DWORD
	     Data:       100
	     Radix:      Hex
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.1. This
	problem was corrected in Windows NT 3.5. This problem was corrected in the
	latest U.S. Service Pack for Windows NT 3.1. For information on obtaining this
	update, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	Additional query words: prodnt 3.10 3.50 2.20
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW310 kbWinNTSsearch kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS310search kbAudDeveloper kbWinNT310Search kbWinNTW310Search kbLanManSearch kbLanMan220
	Version           : 3.10 | 2.20
	
	=============================================================================
	

{% endraw %}
