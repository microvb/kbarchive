---
layout: page
title: "Q167029: Resource and Master Domain DCs Do Not Load-Balance Validation"
permalink: /kb/167/Q167029/
---

## Q167029: Resource and Master Domain DCs Do Not Load-Balance Validation

{% raw %}

	Article: Q167029
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Generally, the first signs that the resource and master domain-domain
	controllers (DCs) do not load-balance validation are user complaints of slowness
	during logon, slow resource authentication, or logon scripts taking a long time
	to run. You may also discover the situation by monitoring the secure channel
	with the NLTEST utility from the Windows NT Resource Kit.
	
	CAUSE
	=====
	
	The SC_client uses standard protocol behavior to determine the possible DCs with
	which to set up the secure channel. It then requests a secure channel to these
	DCs and will establish one with whichever answers back first. This usually
	results in a secure channel with the DC physically closest, or over the fastest
	link.
	
	The process described above presents two possible problem scenarios:
	
	- If the local DCs are too busy, or environmental conditions on the network
	  delay the response from the local DCs, a remote DC, or one on a
	  less-than-optimal link could be the first to respond and set up the secure
	  channel.
	
	- A very responsive DC could end up with an uneven share of the secure channels
	  and hence, the authentication load.
	
	MORE INFORMATION
	================
	
	Windows NT uses secure channels for account validation and authentication
	between domain participants. The channel is set up at startup between the
	computer running Windows NT client (Workstation or member server) and one of its
	domain controllers, or between a domain controller from a trusting domain and a
	domain controller from the trusted domain.
	
	NOTE: Both the Windows NT client and the trusting domain controller (DC) will be
	referred to as SC_clients for the remainder of this article.
	
	This channel will remain in effect until the link goes down, one of the computers
	go down, or the DC is too busy to service the request(s) from the SC_client.
	
	RESOLUTION
	==========
	
	A new utility, Setprfdc.exe, and new functionality added to NETLOGON, allow you
	to direct the SC_client to a preferred DC for the secure channel.
	
	Setprfdc.exe is a command-line utility. It may be run in batch or with the AT
	Scheduler. The format of the command is:
	
	  SETPRFDC <TrustedDomain> <ListOfDcsInTrustedDomain> (DC1, DC2,
	  and so on.)
	
	SETPRFDC handles each DC in its list in order. As it processes the list, it
	checks to see if the secure channel is already with DC1. If it is, it does
	nothing, if it is not, it will try to establish a secure channel with DC1. If it
	can establish the secure channel with the preferred DC1 it does so and stops. If
	it cannot establish with DC1 it will check to see if the currently secured
	channel is with DC2. If it is not with DC2, it will try to establish with DC2,
	and so on, until it exhausts all DCs in the command list. If it is unable to
	establish a secure channel with any of the preferred DCs in the list, it will
	leave the current secure channel intact until the next time you run SETPRFDC.
	
	To address scenario one described above, run the utility on the affected
	SC_clients, listing the DCs in order of preference, usually starting with the
	closest or best link. This will allow you to direct them to the DC of choice.
	
	To address scenario 2 described above, run the utility on all SC_clients, listing
	the DCs in an order that would accomplish load distribution for authentication
	requests.
	
	Obtain the following fix or wait for the next Windows NT service pack.
	
	This fix should have the following file details:
	
	  05/30/97  09:13 PM               10,000 Setprfdc.exe (Intel)
	  05/30/97  08:13 PM               15,632 Setprfdc.exe (Alpha)
	
	NOTE: Service Pack 3 must be applied to Windows NT 4.0 SC_client prior to
	applying this fix.
	
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Article ID: Q165202
	  Title : WinNT Client Logon in Resource and Master Domain Environment
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0.
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
