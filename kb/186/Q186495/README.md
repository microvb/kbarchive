---
layout: page
title: "Q186495: WOW Leak Launching Many Instances of a 16-Bit Application"
permalink: /kb/186/Q186495/
---

## Q186495: WOW Leak Launching Many Instances of a 16-Bit Application

{% raw %}

	Article: Q186495
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbWinNT400sp4fix
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	In cases where 16-bit applications are launched repeatedly in separate Virtual
	DOS Machines (VDMs), system resources may be depleted because of a WOW memory
	leak. Symptoms of the leak condition will be popup errors messages indicating
	"low virtual memory" and potential system crashes if memory resources are
	severely depleted over a long period of time. The problem can be recognized by
	monitoring MemUsage under Windows NT Task Manager or by running Performance
	Monitor using the following counters:
	
	  Object: Process
	  Counter: Handle count and Private Bytes
	  Instance: csrss
	
	
	CAUSE
	=====
	
	There is a memory leak in Wow32.dll and Winbase.dll.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	======================================================================
	Keywords          : kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : WinNT:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
