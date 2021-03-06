---
layout: page
title: "Q185816: DNS Server Event Log IDs Incorrect After Applying SP4"
permalink: /kb/185/Q185816/
---

## Q185816: DNS Server Event Log IDs Incorrect After Applying SP4

{% raw %}

	Article: Q185816
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On a Windows NT Server computer running the Domain Name Server (DNS) service,
	you will no longer be able to read DNS events created prior to the application
	of Service Pack 4 (SP4). All DNS messages will look similar to the following:
	
	  A description for Event (*) in Source (DNS) could not be found. It
	  contains the following insertion string(s): *
	
	NOTE: The * would be the Event Identifier and any additional data.
	
	RESOLUTION
	==========
	
	To prevent this problem, stop the DNS server service prior to applying SP4 and
	save the system event log. The event log offset for DNS events has been changed
	as of SP4. To read the saved event logs, perform the following steps:
	
	1. At a command prompt, type:
	
	  Net Stop DNS
	
	2. Change to the %System Root%\System32 Directory and rename the Dns.exe file to
	  Dns.exe.sp4.
	
	3. Change to the $NTUninstall directory and copy the old Dns.exe (pre-SP4)
	  binary into the %System Root%\system32 directory.
	
	4. Open Event Viewer. You can now view the logs on that computer with the old
	  binary.
	
	5. When finished reviewing the log, rename old Dns.exe to Dns.exe.sp3 and rename
	  Dns.exe.sp4 to Dns.exe.
	
	6. At a command prompt, type:
	
	  Net Start DNS
	
	An alternative may be to bring up a new DNS server (pre-SP4) and use it to view
	old DNS events or saved event logs.
	
	Additional query words: dns Event Log Messages
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
