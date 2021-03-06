---
layout: page
title: "Q130273: NetBT Domain 0x1C Name Fails to Add All #DOM IP Addresses"
permalink: /kb/130/Q130273/
---

## Q130273: NetBT Domain 0x1C Name Fails to Add All #DOM IP Addresses

{% raw %}

	Article: Q130273
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When Netlogon sends discovery mailslots to find a domain controller in a trusted
	domain, it fails to send directed mailslots to all the domain controllers
	defined in the LMHOSTS file with the trusted domain name.
	
	You can see the results in the following sample LMHOSTS file and trace. Even
	though TTOWN5 is defined as an AMERICA Domain Controller, it is never sent a
	directed mailslot for Netlogon, therefore it may never be used for
	authentication by a trusting domain.
	
	LMHOSTS file contents:
	
	  144.249.168.234 CIMCON       #DOM:AMERICA        #PRE
	  144.249.168.104 TTOWN1       #DOM:AMERICA        #PRE
	  144.249.13.207  TTOWN2       #DOM:AMERICA        #PRE
	  144.249.168.105 TTOWN3       #DOM:AMERICA        #PRE
	  144.249.169.16  TTOWN4       #DOM:AMERICA        #PRE
	  144.249.157.21  TTOWN5       #DOM:AMERICA        #PRE
	
	Trace results:
	
	  EVERST *BROADCAST    NETLOGON SAM LOGON request from client
	  EVERST *NETBIOS Mult NETLOGON SAM LOGON request from client
	  EVERST CIMCON        NETLOGON SAM LOGON request from client
	  EVERST TTOWN1        NETLOGON SAM LOGON request from client
	  EVERST TTOWN2        NETLOGON SAM LOGON request from client
	  EVERST TTOWN3        NETLOGON SAM LOGON request from client
	  EVERST TTOWN4        NETLOGON SAM LOGON request from client
	
	CAUSE
	=====
	
	The LMHOSTS parser code in NetBT incorrectly stores IP Addresses when building
	the <Domain Name 0x1c> Group Name.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.5. A fix to
	this problem is in development, but has not been regression-tested and may be
	destabilizing in production environments. Microsoft does not recommend
	implementing this fix at this time. Contact Microsoft Product Support Services
	for more information on the availability of this fix.
	
	
	Additional query words: 3.50 prodnt
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search
	Version           : winnt:3.5
	
	=============================================================================
	

{% endraw %}
