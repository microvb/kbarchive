---
layout: page
title: "Q243478: STOP 0xA in Netbt.sys Occurs on Domain Master Browser"
permalink: /kb/243/Q243478/
---

## Q243478: STOP 0xA in Netbt.sys Occurs on Domain Master Browser

{% raw %}

	Article: Q243478
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Your domain master browser (generally a primary domain controller) may stop
	responding and you may receive a "Stop OxA in Netbt.sys" error message on a blue
	screen with the following parameters: 0x000000fc, 0x00000002, 0x00000000,
	0xfc7ac47a.
	
	NOTE: The fourth parameter may vary, but the error is in the Netbt.sys driver
	address space.
	
	CAUSE
	=====
	
	This behavior occurs if the master browser receives a broadcast packet with a
	source address of 0.0.0.0. When the master browser attempts to respond to the
	broadcast packet, a structure used by NetBT is not filled out correctly.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date       Time     Size      File name   Platform
	  --------------------------------------------------
	  10/11/99   05:12p   123,152   Netbt.sys   Intel
	  10/11/99   05:11p   222,896   Netbt.sys   Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0.
	
	
	Additional query words: pdc
	
	======================================================================
	Keywords          : kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
