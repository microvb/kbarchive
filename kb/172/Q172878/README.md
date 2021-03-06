---
layout: page
title: "Q172878: Resource Kit Timeserv.exe Utility Causes 100% CPU Utilization"
permalink: /kb/172/Q172878/
---

## Q172878: Resource Kit Timeserv.exe Utility Causes 100% CPU Utilization

{% raw %}

	Article: Q172878
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbenv kbnetwork
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Your Windows NT 4.0 computer that is running the Windows NT 4.0 Resource Kit
	utility Timeserv.exe may slow down in its performance, even stop responding at
	times. If you check Performance Monitor or Task Manager, you may notice the
	Timeserv utility displays the CPU Utilization at 100%.
	
	CAUSE
	=====
	
	One of the time servers on the Internet that the Timeserv utility contacts has
	sent no data in its return TCP packet.
	
	RESOLUTION
	==========
	
	To resolve this issue, use either of the following methods:
	
	Method 1
	--------
	
	Obtain the updated Timeserv.exe file from the following Microsoft FTP sites:
	
	- Intel:
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/reskit/nt40/i386
	
	- Alpha:
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/reskit/nt40/alpha
	
	Method 2
	--------
	
	Edit the Timeserv.ini file. To do so, follow these steps:
	
	1. Click Start, point to Settings, click Control Panel, and then double- click
	  Services.
	
	2. Click Time Service, and then click Stop.
	
	3. Using a text editor (such as Notepad.exe or Edit.com), open the Timeserv.ini
	  file that exists in your %SystemRoot% folder.
	
	4. Below the section heading [TimeServ], add the following line:
	
	     USNOServer=192.5.41.41
	
	5. Save the file and close the text editor.
	
	6. From a command prompt, type "timeserv -update" (without the quotation marks).
	
	7. Click Start, point to Settings, click Control Panel, and then double- click
	  the Services icon.
	
	8. Click Time Service, and then click Restart.
	
	MORE INFORMATION
	================
	
	This issue may occur when the Windows NT server computer running Time Service
	receives no data in the TCP packet from the Internet server when Internet type
	is selected in the Timeserv.ini file.
	
	When Internet type is selected, your Windows NT server computer will attempt to
	connect to one of the two time servers on the Internet provided by the United
	States Naval Observatory (USNO). These time servers provide an accurate time
	that is used by Windows NT to synchronize its time. The time servers are:
	
	  tick.usno.navy.mil   192.5.41.40
	  tock.usno.navy.mil   192.5.41.41
	
	Occasionally, the server at IP address 192.5.41.40 might not accept time requests
	sent to the TCP port daytime(13) and sends a TCP RST in return. This will prompt
	your Windows NT server to try the alternate server, 192.5.41.41, and continues
	with time synchronization. Alternately, the first server may accept a TCP
	connection request but does not send any data in the reply message packet. This
	causes CPU Utilization to go to 100% on the Windows NT Server.
	
	NOTE: The above USNO servers also provide Network Time Protocol (NTP) service.
	NTP uses UDP port 123. In order to use NTP service, enable NTP in the
	Timeserv.ini file by adding the following line before updating Time Service:
	
	  NTPServer=192.5.41.41
	
	For more information regarding Time Service, please refer to the "Windows NT 4.0
	Resource Kit."
	======================================================================
	Keywords          : kbenv kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
