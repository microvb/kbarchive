---
layout: page
title: "Q182781: Client Connections to Multihomed Server Not Load Balanced"
permalink: /kb/182/Q182781/
---

## Q182781: Client Connections to Multihomed Server Not Load Balanced

{% raw %}

	Article: Q182781
	Product(s): Microsoft Windows NT
	Version(s): WinNT;4.0
	Operating System(s): 
	Keyword(s): kbWinNT400sp4fix
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	You have a number of clients that are using TCP/IP to connect to a multihomed
	server that has no IP addresses on the same subnet as the client and the clients
	are always connecting to the same address on the server, even though the paths
	to more than one of the addresses are equal.
	
	CAUSE
	=====
	
	When the client's NetBT layer attempts to resolve the NetBIOS name to an IP
	address, it queries the WINS server for the address of a multihomed server and
	receives a list of addresses that are always in the same order. NetBT then takes
	that list and sorts it, putting addresses on the same subnet (if any) at the
	top, followed by addresses in the same network class, and then any remaining
	addresses. It then starts at the top of this list and pings the first address to
	make sure it is valid. If it does not get a reply, it will go on to the next
	address; if it does get a reply, it will use the first address.
	
	The problem is that, within these three categories, the order of addresses is
	left unchanged from the list provided by the WINS server. This means that, as
	long as the first address in the list is online, it will be the one that is
	always used by every client, which does not provide for load balancing.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q161425
	  TITLE : WinNT 4.0 SP2 Multi-Homed Computer Connection Enhancement
	
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
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : WinNT;4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
