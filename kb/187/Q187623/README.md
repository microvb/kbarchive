---
layout: page
title: "Q187623: How to Change Terminal Server's Listening Port"
permalink: /kb/187/Q187623/
---

## Q187623: How to Change Terminal Server's Listening Port

{% raw %}

	Article: Q187623
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Professional 
	- Microsoft Windows 2000 Server 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	By default Terminal Server and Windows 2000 Terminal Services uses TCP port 3389
	for client connections. Microsoft does not recommend that this value be changed.
	However, if it becomes necessary to change this port, follow these instructions.
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To change the default port for all new connections created on the Terminal
	Server:
	
	1. Run Regedt32 and go to this key:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Terminal
	  Server\WinStations\RDP-Tcp
	
	NOTE: The above registry key is one path; it has been wrapped for readability.
	
	2. Find the "PortNumber" subkey and notice the value of 00000D3D, hex for
	  (3389). Modify the port number in Hex and save the new value.
	
	  To change the port for a specific connection on the Terminal Server:
	
	   - Run Regedt32 and go to this key:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Terminal
	  Server\WinStations\<connection>
	
	     NOTE: The above registry key is one path; it has been wrapped for
	     readability.
	
	3. Find the "PortNumber" subkey and notice the value of 00000D3D, hex for
	  (3389). Modify the port number in Hex and save the new value.
	
	  NOTE: Because the use of alternate ports has not been fully implemented for
	  Terminal Server 4.0, support will be provided as "reasonable effort" only,
	  and Microsoft may require you to set the port back to 3389, if any problems
	  occur.
	
	To Alter the Port on the Client Side
	------------------------------------
	
	1. Open Client Connection Manager.
	
	2. On the File menu, click New Connection, and then create the new connection.
	  After running the wizard, you should have a new connection listed there.
	
	3. Making sure that the new connection is highlighted, on the File menu, click
	  Export. Save it as <name>.cns.
	
	4. Edit the .cns file using Notepad changing "Server Port=3389" to "Server
	  Port=<xxxx>" where <xxxx> is the new port that you specified on
	  Terminal Server.
	
	5. Now import the file back into Client Connection Manager. You may be prompted
	  to overwrite the current one, if it has the same name. Go ahead and overwrite
	  it. You now have a client that has the correct port settings to match your
	  change Terminal Server settings.
	
	NOTE: The Terminal Server ActiveX client listens on TCP port 3389 and this cannot
	be changed. The Remote Desktop Protocol (RDP) client that is available in
	Microsoft Windows XP and Windows .NET (version 5.1 and later) has this ability.
	
	
	NOTE: You must restart the Terminal Server before the new listening port becomes
	active, or recreate the RDP listener via Terminal Services configuration.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbNTTermServ400 kbNTTermServSearch kbWinAdvServSearch
	Version           : :2000,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
