---
layout: page
title: "Q159981: Adding LUs to TN3270 Admin Leads to Server Performance Problems"
permalink: /kb/159/Q159981/
---

## Q159981: Adding LUs to TN3270 Admin Leads to Server Performance Problems

{% raw %}

	Article: Q159981
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When using the SNA Server 2.11 (or SP1) TN3270 Server with a large number of LUs
	(over 250), the following problems may occur when running TN3270 Administrator
	program to add new LUs to the configuration:
	
	- Windows NT may become very slow or unresponsive.
	
	- Performance Monitor will show the CPU utilization at 100 percent.
	
	- Existing TN3270 users who are connecting through the TN3270 Server may stop
	  receiving responses from the host, or may lose their TN session.
	
	NOTE: In addition, if SNA Server 2.11 is being used, the TN3270 service fails to
	start when using a large TN3270 configuration file. This particular problem was
	fixed in SNA Server 2.11 Service Pack 1.
	
	CAUSE
	=====
	
	The TN3270 Admin program does not efficiently handle configurations which
	involve a large number of LUA LUs.
	
	
	RESOLUTION
	==========
	
	Under SNA Server 2.11 or SP1, the TN3270 Server configuration file size could be
	reduced to work around the problem. This can be accomplished by assigning users
	to pools of LUA LUs, rather than configuring a large number of unique LUA LUs.
	To create pools of LUA Lus:
	
	1. Use the SNA Server Administrator program LU Pools window to group LUA LUs
	  together.
	
	2. Assign instances of the LUA pools to TCP/IP users within the TN3270
	  Administrator program.
	
	If specific LUs must be assigned, requiring a large number of LUA LUs to be
	defined, the only workaround is to make TN3270 Server configuration changes
	after hours. Otherwise, there is no resolution using SNA Server 2.11 or SP1
	except to upgrade to SNA Server 3.0. Under SNA Server 3.0, the TN3270 Server
	administration is integrated with the new SNA Server Manager interface, so the
	TN3270 Administrator tool is no longer used.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 2.11 or 2.11
	Service Pack 1. See the Resolution section above for possible workarounds. This
	problem is solved in SNA Server 3.0.
	
	MORE INFORMATION
	================
	
	See the following Microsoft Knowledge Base article for more information on the
	TN3270 service failing to start when using a large TN3270 configuration file
	(this problem occurs only SNA Server 2.11, not Service Pack 1):
	
	  Q137588 TN3270 Service Will Not Start with a Large Config File
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.11,2.11 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
