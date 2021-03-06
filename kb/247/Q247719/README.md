---
layout: page
title: "Q247719: WLBS Writes Multiple Duplicate Event Log Messages"
permalink: /kb/247/Q247719/
---

## Q247719: WLBS Writes Multiple Duplicate Event Log Messages

{% raw %}

	Article: Q247719
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbinterop kbnetwork kbWinNT400PreSP7Fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If your Windows NT 4.0-based computer is configured to use the Windows Load
	Balancing Service (WLBS) and experiences network communications problems,
	multiple, duplicate messages may be written to the computer's event log. If you
	have auditing enabled, the event log may become filled with these messages and a
	new event may not be logged, even if it is from a critical service. If the event
	log fills to its configured capacity, the computer may stop responding (hang).
	
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
	  10/12/99   07:44p    36,112   Wlbs.exe    x86
	  10/29/99   01:06p    60,208   Wlbs.sys    x86
	  10/12/99   07:43p    51,472   Wlbs.exe    Alpha
	  10/29/99   01:05p   101,104   Wlbs.sys    Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbnetwork kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
