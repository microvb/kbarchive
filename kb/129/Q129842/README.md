---
layout: page
title: "Q129842: Maximum Number of Send and Receive Packets Used By NBF"
permalink: /kb/129/Q129842/
---

## Q129842: Maximum Number of Send and Receive Packets Used By NBF

{% raw %}

	Article: Q129842
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.5 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 4.0 
	- Microsoft Windows NT Server versions 3.5, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The NBF (NetBEUI) transport uses SendPacketPoolSize and ReceivePacketPoolSize
	parameters to limit the maximum number of send and receive packets it
	dynamically allocates. If send and receive packet exhausted errors occur
	frequently, you may need to increment the values of these parameters.
	
	MORE INFORMATION
	================
	
	Receive packets are used by NBF to handle the incoming frames. Send packets are
	used for connection oriented data. SendPacketPoolSize and ReceivePacketPoolSize
	control the maximum number of send and receive packets NBF can allocate at one
	time. The default value of SendPacketPoolSize is 100 and the default value of
	ReceivePacketPoolSize is 30.
	
	Under normal load, these parameters do not need to be changed. In some cases,
	these parameters need to be adjusted. For example, too many reads and writes are
	carried out by client workstations, and you need to optimize network throughput.
	You may also want to change these parameters if a workstation cannot connect to
	a server when the network is under heavy load.
	
	To see if the values of these two parameters need to be modified:
	
	1. Run Performance Monitor.
	
	2. Choose NetBEUI Resource.
	
	  The followig three counters are available in the Counter list box:
	
	     Times Exhausted
	     Used Average
	     Used Maximum
	
	  The Instance list box shows counters for each net board installed.
	
	3. To see the number of times ReceivePackets exhausted, select Times exhausted
	  in the Counter list box and \Device\NbfAdopter ==>Receive Packet (23).
	
	To add or modify the SendPacketPoolSize or ReceivePacketPoolSize parameters:
	
	The following details steps to take to add /modify the WARNING: Using Registry
	Editor incorrectly can cause serious, system-wide problems that may require you
	to reinstall Windows NT to correct them. Microsoft cannot guarantee that any
	problems resulting from the use of Registry Editor can be solved. Use this tool
	at your own risk.
	
	1. Run Registry Editor (REGEDT32.EXE).
	
	2. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	     \Services\NBF\Parameters 
	
	3. If the SendPacketPoolSize or ReceivePacketPoolSize key exists, choose Edit
	  Value from the Edit menu and change the value as needed.
	
	4. If the SendPacketPoolSize or ReceivePacketPoolSize key does not exist, choose
	  Add Key from the Edit menu and add the following information:
	
	     Value Name: SendPacketPoolSize
	     Data Type:  REG_DWORD
	     Value:      Insert the desired value
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.1 3.5 4.0
	
	=============================================================================
	

{% endraw %}
