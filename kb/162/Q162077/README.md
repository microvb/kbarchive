---
layout: page
title: "Q162077: Stop: 0x0000000A when Selecting NDS Map Objects"
permalink: /kb/162/Q162077/
---

## Q162077: Stop: 0x0000000A when Selecting NDS Map Objects

{% raw %}

	Article: Q162077
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetworkkbbuglist kbfixlist
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	A computer running Windows NT 4.0 Workstation or Server may display a Blue
	Screen STOP message of STOP: 0x0000000A after selecting NDS Map Objects in
	Windows Explorer Network Neighborhood.
	
	MORE INFORMATION
	================
	
	Steps to reproduce the problem
	------------------------------
	
	1. Log on to the NetWare 4 server network.
	
	2. Start Windows NT Explorer.
	
	3. Go to Network Neighborhood (map objects will be seen at the bottom of the
	  list).
	
	4. Double-click one of these objects, and a Blue Screen STOP message appears.
	
	CAUSE
	=====
	
	When this operation starts, an open lock should be acquired, but it is not.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0. This
	problem was corrected in the latest Microsoft Windows NT 4.0 U.S. Service Pack.
	For information on obtaining the service pack, query on the following word in
	the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words: prodnt 0xa nwrdr
	
	======================================================================
	Keywords          : kbnetwork kbbuglist kbfixlist
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
