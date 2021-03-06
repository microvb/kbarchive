---
layout: page
title: "Q272714: XFOR: Fax Sent to 1(262)xxx-xxxx Gets Addressed to 1Cxxx-xxxx"
permalink: /kb/272/Q272714/
---

## Q272714: XFOR: Fax Sent to 1(262)xxx-xxxx Gets Addressed to 1Cxxx-xxxx

{% raw %}

	Article: Q272714
	Product(s): Microsoft Exchange
	Version(s): 5.5,5.5 SP1,5.5 SP2,5.5 SP3
	Operating System(s): 
	Keyword(s): exc55 exc55sp1 exc55sp2 exc55sp3
	Last Modified: 02-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.5 SP1, 5.5 SP2, 5.5 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you send a fax message to a 262 area code number and enclose the area code
	parentheses, it arrives at the BISCOM Fax EDK gateway with the (262) changed to
	an upper case C. This causes the fax message to be undeliverable.
	
	CAUSE
	=====
	
	The use of parentheses in the address causes the change. The area code of this
	fax address is incorrectly interpreted as an ASCII character. This behavior
	occurs for any three digits enclosed in parentheses, where the first digit is a
	0, 1, or 2.
	
	Parentheses are used in an X.400 address to portray characters such as the at
	sign (@), the exclamation mark (!), or the percent sign (%) in an address.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Microsoft Exchange version 5.5 service
	pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Store
	
	+---------------------------+
	| File name    | Version    | 
	+---------------------------+
	| Escprint.dll | 5.5.2651.0 | 
	+---------------------------+
	
	This hotfix is included in the following Microsoft Knowledge Base article, which
	contains information store fixes. Refer to Q248838 for details and latest
	version information.
	
	  Q248838 XADM: Exchange Server 5.5 Post-SP3 Information Store Fixes Available
	
	NOTE: When you start this version of the information store, the information store
	databases are automatically upgraded to a new format. After the databases have
	been upgraded, you can restore an earlier version of the Store.exe file on the
	server, but only if it is version 5.5.2651.32 or later. If you restore a
	Store.exe file earlier than version 5.5.2651.32 after the database has been
	upgraded, you are no longer able to start the information store. For additional
	information, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q244976 XADM: Event ID 1197 and 1005 When Starting the Information Store
	
	
	For additional information about recipient addresses corrupted on messages to EDK
	Gateway, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q185592 XCON: Recipient Address Corrupted on Messages to EDK Gateway
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 exc55sp1 exc55sp2 exc55sp3 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2 kbExchange550SP1 kbExchange550SP2 kbExchange550SP3
	Version           : :5.5,5.5 SP1,5.5 SP2,5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
