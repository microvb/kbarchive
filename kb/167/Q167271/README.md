---
layout: page
title: "Q167271: &quot;Path Not Found&quot; When Using 3Com LANPLEX 2500 Router"
permalink: /kb/167/Q167271/
---

## Q167271: &quot;Path Not Found&quot; When Using 3Com LANPLEX 2500 Router

{% raw %}

	Article: Q167271
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kb3rdparty kbhw kbnetwork kbHardware
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to connect a Windows NT Server or Workstation computer from one
	IPX network across a 3Com LANplex 2500 Router (running 8.115 microcode) to
	another Windows NT Server or Workstation computer located on a remote IPX
	network you will encounter the error:
	
	  Path not found.
	
	A Windows 95 client can connect to a Windows NT Server or Workstation Computer
	across the LANplex router without any difficulties.
	
	RESOLUTION
	==========
	
	Contact 3Com for its latest version of microcode for this router which includes
	a fix for the problem.
	
	MORE INFORMATION
	================
	
	Windows 95 and Windows NT handle netbios over IPX or IPX packet type 20's
	differently. In the following example, the Windows 95 client places it's current
	network number in the Find Name netbios broadcast packet to discover the netbios
	name of the Microsoft networking client (that is 27202.FFFFFFFFFFFF.455). The
	Windows NT Server or Workstation places a zero (0) in front of the broadcast
	packet rather than the network number (0.FFFFFFFFFFFF.455).
	
	The following example came from an actual trace using Netmon:
	
	Windows 95
	----------
	
	IPX: NetBIOS Packet - 27202.00C04FD7ACBC.455 -> 27202.FFFFFFFFFFFF.455 - 0
	Hops
	
	Windows NT 4.0
	--------------
	
	The Windows NT server/client precedes the Find Name netbios packet from the
	client to the network with a zero (0) followed by the broadcast.
	
	IPX: NetBIOS Packet - 2B9659.000000000001.455 -> 0.FFFFFFFFFFFF.455 - 0 Hops
	
	By definition of Novell's IPX routing specification, the router should not care
	whether the netbios broadcast packet is preceded by a network number or a zero.
	This should be true when you set up your router to bridge netbios packets over
	IPX (packet type 20's). Bridging, by definition, should take the packet from one
	network and propagate it on another network.
	
	The 3Com LANplex 2500 router, with microcode version 8.115, kills the Find Name
	netbios broadcast packet from a Windows NT Server or Workstation because the
	packet is preceded by a zero (0) network number. In other words, the 3Com
	LANPlex 2500 router incorrectly handles a netbios packet from a Windows NT
	Server or client.
	
	Here is an excerpt from Novell's IPX routing specification:
	
	  When a Type 20 broadcast packet is received by a router (this is indicated by
	  a Packet Type of 14h in the IPX header,) the following sequence of events
	  should occur:
	
	  * The Transport Control Field of the IPX header is examined; this value
	  indicates the number of routers traversed by the packet so far. This field
	  also indicates how many Network Number fields in the packet have been filled
	  in. If this value is 8 or greater the packet is discarded, otherwise proceed
	  to the next step.
	
	  * The router compares each Network Number entry in the packet to the Network
	  Number of the segment on which the router received the packet. If a match is
	  found, the packet is discarded to prevent multiple traversals of the same
	  network segment; if no match is found, proceed to the next step.
	
	  * The router places the address of the network segment on which the packet
	  arrived into the next available Network Number field. The offset of this
	  field is easily calculated as 4 * n bytes past the end of the IPX header,
	  where n is the value of the Transport Control Field.
	
	  * The router increments the Transport Control Field of the IPX header and
	  broadcasts the packet to all directly connected network segments that are NOT
	  included in the Network Number fields.
	
	Additional query words: Winnt 3Com LANplex NwLnk
	
	======================================================================
	Keywords          : kb3rdparty kbhw kbnetwork kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbWin95search kbZNotKeyword3
	Version           : WinNT:4.0
	
	=============================================================================
	

{% endraw %}
