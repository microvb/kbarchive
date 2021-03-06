---
layout: page
title: "Q223279: XADM: Extension DSAVUADM Could Not Be Loaded Accessing a Mailbox"
permalink: /kb/223/Q223279/
---

## Q223279: XADM: Extension DSAVUADM Could Not Be Loaded Accessing a Mailbox

{% raw %}

	Article: Q223279
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 16-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you use the Exchange Server Administrator program to view the properties of a
	mailbox, you may receive the following error message:
	
	  Extension DSAVUADM could not be loaded.
	  The extension for MS Exchange Administrator CPU type c1031667 could not be
	  loaded.
	
	After you click OK, a window appears with Abort, Retry, Ignore. If you click
	Ignore, you can access the mailbox.
	
	The following event may be logged on the server.
	
	  Event ID 2037
	  Source: System Attendant
	  Description: The file version \\Add-ins\Dsavuad\I386\Dsavuadm.dll installed by
	  the local server is not current. Unable to locate the current version on any
	  server in the site.
	
	CAUSE
	=====
	
	This behavior may be caused by the installation and removal of GroupShield
	Exchange on Exchange Server computers. When you open a mailbox object and all of
	its associated properties, including the Anti-virus tab that GroupShield
	creates, the Exchange Server Administrator program looks for the Dsavuadm.dll
	file to display the properties of the Anti-virus tab.
	
	When you install GroupShield, it creates a public folder called Quarantine to
	place infected messages in.
	
	Dsavuadm.dll is a Network Associates GroupShield extension.
	
	RESOLUTION
	==========
	
	Please contact the software vendor Network Associates (formally McAfee) about
	completely removing GroupShield Exchange from your Exchange Server computer, so
	that it does not affect other servers in the organization.
	
	For information about how to contact Network Associates, click the appropriate
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	WORKAROUND
	==========
	
	Contact Network Associates, or upgrade GroupShield Exchange to version 4.0.4 or
	later.
	
	
	Additional query words: removal upgrade site join joining
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
