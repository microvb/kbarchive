---
layout: page
title: "Q195541: Large Number of Mounts/Dismounts on NTFS Causes Memory Leak"
permalink: /kb/195/Q195541/
---

## Q195541: Large Number of Mounts/Dismounts on NTFS Causes Memory Leak

{% raw %}

	Article: Q195541
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): winnt
	Keyword(s): kbbug4.00 kbfix4.00
	Last Modified: 10-NOV-1998
	
	--------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0
	- Microsoft Windows NT Server version 4.0
	- Microsoft Windows NT Server, Enterprise Edition version 4.0
	--------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A system may leak nonpageable memory when a large amount of mounts and
	dismounts are done on an NTFS partition.
	
	CAUSE
	=====
	
	The driver Ntfs.sys does not keep track of a VPB structure if a dismount
	request is followed by an unlock request. The memory leak is small, so the
	problem will usually appear after a period of days. POOLMON can be used to
	check this problem. Look for the NtfV tag taking up a lot of the
	nonpageable memory. Performance Monitor can also be used to monitor
	nonpageable memory use.
	
	RESOLUTION
	==========
	
	A supported fix that corrects this problem is now available from Microsoft,
	but has not been fully regression tested and should be applied only to
	systems experiencing this specific problem. If you are not severely
	affected by this specific problem, Microsoft recommends that you wait for
	the next Windows NT service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support
	Services to obtain the fix. For a complete list of Microsoft Product
	Support Services phone numbers and information on support costs, please go
	to the following address on the World Wide Web:
	
	  http://support.microsoft.com/support/supportnet/default.asp
	
	The English version of this fix should have the following file attributes
	or later:
	
	  Date      Time                 Size    File Name     Platform
	  -------------------------------------------------------------
	  11/05/98  05:46p             262,512   Ntfs.sys      (x86)
	  11/05/98  05:46p             558,576   Ntfs.sys      (Alpha)
	
	NOTE: If you contact Microsoft to obtain this fix, a fee may be charged.
	This fee is refundable if it is determined that you only require the fix
	you requested. However, this fee is non-refundable if you request
	additional technical support.
	
	For more information about eligibility for no-charge technical support, see
	the following article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q154871
	  TITLE     : Determining If Your Product Is Eligible for No-Charge
	              Technical Support
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	Additional query words: 4.00
	======================================================================
	Keywords          : kbbug4.00 kbfix4.00
	Version           : WinNT:4.0
	Platform          : winnt
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
