---
layout: page
title: "Q195971: XADM: Deadlock in STORE Due to a Stack Overflow"
permalink: /kb/195/Q195971/
---

## Q195971: XADM: Deadlock in STORE Due to a Stack Overflow

{% raw %}

	Article: Q195971
	Product(s): Microsoft Exchange
	Version(s): 5.0,5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix exc5 exc55
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 5.5, 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange information store may stop responding (hang) because of a
	stack overflow when processing a corrupted message. After this happens, the
	client cannot log on to the Exchange Server computer and cannot send or receive
	a message.
	
	CAUSE
	=====
	
	This happens because the message contains a corrupted attachment, in this case,
	there is no "END" section for the encoded attachment. When the information store
	encounters an incomplete sequence at the end of the encoded line, it keeps
	appending more data, but makes no progress with decoding.
	
	RESOLUTION
	==========
	
	Exchange Server 5.5
	-------------------
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Information Store
	
	+-------------------------+
	| File Name  | Version    | 
	+-------------------------+
	| Gapi32.dll | 5.5.2446.0 | 
	+-------------------------+
	| Mdbmsg.dll | 5.5.2446.0 | 
	+-------------------------+
	| Store.exe  | 5.5.2446.0 | 
	+-------------------------+
	
	
	Exchange Server 5.0
	-------------------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next version of Exchange Server 5.0 that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Information Store
	
	+--------------------------+
	| File Name  | Version     | 
	+--------------------------+
	| Mdbmsg.dll | 5.0.1461.91 | 
	+--------------------------+
	| Store.exe  | 5.0.1461.91 | 
	+--------------------------+
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	versions 5.0 and 5.5.
	
	Additional query words: QFE UUENCODE
	
	======================================================================
	Keywords          : exc55sp2fix exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbZNotKeyword2
	Version           : :5.0,5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
