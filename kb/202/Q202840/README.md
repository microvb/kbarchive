---
layout: page
title: "Q202840: Client Connected to Ethernet Switch May Receive Logon Errors"
permalink: /kb/202/Q202840/
---

## Q202840: Client Connected to Ethernet Switch May Receive Logon Errors

{% raw %}

	Article: Q202840
	Product(s): Microsoft Windows NT
	Version(s): 2000,3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Server 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	On a client computer that is connected to an Ethernet switch, you may receive
	several logon-related error messages during Startup.
	
	In the event log, you may receive the following error message:
	
	  5719 - No domain controller available
	
	NOTE: The source of this error may be the NetLogon service and how the NetLogon
	service sets up its secure channel.
	
	Also, if you log on to the console before Startup has completed, you may receive
	one of the following error messages:
	
	   - No domain controller was available to validate your logon.
	
	   - A domain controller for your domain could not be contacted. You have been
	  logged on using cached account information. Changes to your profile since you
	  last logged on may not be available.
	
	You may receive this error message only when you make the initial attempt to log
	on to the computer. When you make subsequent attempts to log on to the computer,
	you may not receive this error message.
	
	CAUSE
	=====
	
	This behavior can occur because some Ethernet switches have a feature that
	checks the ports for a loop condition when the ports become active (the Learning
	mode for the Spanning Tree Algorithm feature). If a loop is found, all traffic
	is blocked from accessing the port. This process of checking for a loop
	condition takes approximately 10 to 15 seconds during which the Windows NT
	Workstation-based computer seems to be on the network, yet no traffic is being
	passed. The NetLogon service packets (along with any other traffic during that
	time) are lost.
	
	If you have a hub at the end of the port, the hub has already brought the port
	up. Your connection is only unsuccessful when your computer is connected
	directly to the switch.
	
	RESOLUTION
	==========
	
	To resolve this behavior, disable the Spanning Tree Algorithm feature of your
	Ethernet switch.
	
	For information about how to disable the Spanning Tree Algorithm feature on a
	switch, contact the switch manufacturer.
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To work around this behavior, on the clients add the following parameter to the
	registry:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Netlogon\Parameters
	
	Value Name: ExpectedDialupDelay
	Data Type: Reg_Dword
	Data Value is in seconds (default = 0)
	Data Range is between 0 and 600 seconds (10 minutes)
	
	This workaround forces the NetLogon service to pause for the specified amount of
	time before the service attempts to establish its secure channel.
	
	NOTE: Unless you reconfigure your switch, you may still experience the symptoms
	described in the following Microsoft Knowledge Base article:
	
	  Q168455 DHCP Renewal Failures on Switched Networks
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbNTTermServ400 kbNTTermServSearch kbWinNTS351search kbWinNTS350search kbWinAdvServSearch
	Version           : :2000,3.5,3.51,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
