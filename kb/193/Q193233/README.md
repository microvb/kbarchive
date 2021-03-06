---
layout: page
title: "Q193233: Rpcss.exe Consumes 100% CPU Due to RPC Spoofing Attack"
permalink: /kb/193/Q193233/
---

## Q193233: Rpcss.exe Consumes 100% CPU Due to RPC Spoofing Attack

{% raw %}

	Article: Q193233
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
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
	
	System and network performance could degrade and the Rpcss.exe process could
	consume 100 percent of CPU time. Analyzing the network with a protocol analyzer
	shows multiple RPC REJECT packets (addressed to UDP port 135) between two or
	more systems because of an RPC spoofing attack.
	
	CAUSE
	=====
	
	This problem is caused by a malicious attack on the remote procedure call (RPC)
	components in Windows NT.
	
	A UDP packet with a destination port of 135 can be spoofed so that it appears as
	if one datagram RPC server sent bad data to another datagram RPC server. The
	second server returns a REJECT packet. The first server replies with another
	REJECT packet creating a loop that is not broken until a packet is dropped. If
	this spoofed UDP packet is sent to multiple computers, an infinite loop may be
	created, consuming processor resources and network bandwidth.
	
	RESOLUTION
	==========
	
	Windows NT 4.0
	--------------
	
	To resolve this problem, obtain the latest service pack for Windows NT version
	4.0. For more information, please see the following article in the Microsoft
	Knowledge Base.
	
	  Q152734 How To Obtain the Latest Windows NT 4.0 Service Pack
	
	
	This hotfix has been posted as Snk-fixi.exe and Snk-fixa.exe. For your
	convenience, the English version of this post-SP3 hotfix has been posted to the
	following Internet location. However, Microsoft recommends that you install
	Windows NT 4.0 Service Pack 4 to correct this problem.
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40/hotfixes-postSP3/Snk-fix/
	
	Windows NT 4.0, Terminal Server Edition
	---------------------------------------
	
	To resolve this problem, obtain the latest service pack for Windows NT Server
	4.0, Terminal Server Edition. For additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	This hotfix has been posted to the following Internet location as Snk-fixi.exe
	and Snk-fixa.exe:
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40TSE/hotfixes-postSP3/Snk-fix/
	
	
	STATUS
	======
	
	Microsoft has confirmed this problem could result in some degree of security
	vulnerability in Windows NT version 4.0 and Windows NT 4.0, Terminal Server
	Edition. This problem was first corrected in Windows NT 4.0 Service Pack 4.0 and
	Windows NT Server 4.0, Terminal Server Edition Service Pack 4.
	
	MORE INFORMATION
	================
	
	For more information, please see the following Microsoft Security Bulletin:
	
	  http://www.microsoft.com/security/bulletins/ms98-014.asp
	
	Additional query words: denial of service attack snork tse wts
	
	======================================================================
	Keywords          : kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : WinNT:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
