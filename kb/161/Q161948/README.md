---
layout: page
title: "Q161948: XCON: MTA NDRs Messages with Headers in P2 Part of Message"
permalink: /kb/161/Q161948/
---

## Q161948: XCON: MTA NDRs Messages with Headers in P2 Part of Message

{% raw %}

	Article: Q161948
	Product(s): Microsoft Exchange
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 13-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Server Message Transfer Agent (MTA) may not deliver
	incoming mail that includes headers in the P2 part of the message that comply
	with RFC 1327. If this is the case, the Microsoft Exchange Server MTA generates
	a nondelivery report (NDR) to the sender. Incoming mail from Innosoft's PMDF has
	exhibited this behavior.
	
	CAUSE
	=====
	
	The Microsoft Exchange Server MTA does not recognize the RFC 1327 headers, and
	thus rejects the mail message.
	
	WORKAROUND
	==========
	
	To work around this problem, obtain the hotfix mentioned below. With the hotfix,
	the MTA now allows these headers to pass through without generating an NDR.
	However, the MTA neither interprets the RFC 1327 headers, nor acts on them.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server,
	version 4.0. This problem was corrected in the latest Microsoft Exchange 4.0
	U.S. Service Pack. For information on obtaining the service pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	The P2 part of a message is a header that describe the message and how the
	receiving MTA should deal with it. RFC 1327, "Mapping between X.400(1988) / ISO
	10021 and RFC 822," equates headers of like functionality between Internet mail
	and X.400 mail. Internet mail headers primarily come from RFC 822, but there
	have been later RFCs (for example, MIME) that augment the RFC 822 headers.
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : 4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
