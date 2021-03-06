---
layout: page
title: "Q260141: PRB:OpenMsgStore and HrMailboxLogon Fail with Too Many Mailboxes"
permalink: /kb/260/Q260141/
---

## Q260141: PRB:OpenMsgStore and HrMailboxLogon Fail with Too Many Mailboxes

{% raw %}

	Article: Q260141
	Product(s): Microsoft Exchange
	Version(s): 1.0,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,5.0,5.5
	Operating System(s): 
	Keyword(s): kbEDK kbExchange kbMsg kbMAPI100 kbGrpDSMsg kbDSupport
	Last Modified: 12-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 5.0, 5.5 
	- Extended Messaging Application Programming Interface (MAPI), version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you attempt to open more than 255 mailboxes in a single process, you may
	receive an error.
	
	With the Messaging Application Programming Interface (MAPI), you can open
	mailboxes by using the OpenMsgStore method or the HrMailboxLogon function. When
	you try to open too many mailboxes, the OpenMsgStore method returns the
	MAPI_E_FAILONEPROVIDER error, and the HrMailboxLogon function returns the
	MAPI_E_CALL_FAILED error.
	
	NOTE: On success, OpenMsgStore and HRMailboxLogon both return S_OK and a valid
	IMsgStore interface.
	
	CAUSE
	=====
	
	This behavior occurs because MAPI communicates between a client program and the
	Microsoft Exchange Server through the Emsmdb32.dll transport provider. This
	provider uses Microsoft Remote Procedure Calls (RPC) to communicate with the
	server. A single byte holds the index of the logon object, which limits the
	number of logons in a single session and process to 255. In fact, the actual
	limit may be lower because some of the index values are reserved.
	
	
	RESOLUTION
	==========
	
	There are two ways to work around this behavior:
	
	- Structure your program so that the number of mailboxes open at one time never
	  exceeds the limit. If possible, log on to one mailbox at a time, and release
	  its interface when you are done. Once a mailbox is released, its index value
	  can be reused. (See the "More Information" section for more details.) You can
	  also structure the program to spawn subprocesses that each handle a portion
	  of the mailboxes. The subprocesses do not exceed the limit individually, and
	  the program as a whole can have access to all mailboxes simultaneously.
	
	- Create a special profile specifically for use by your program. On this
	  profile, set PR_PROFILE_CONNECT_FLAGS to include the flag
	  CONNECT_USE_SEPARATE_CONNECTION (0x4). This profile instructs MAPI to use a
	  separate RPC connection for each logon. This approach is inefficient,
	  however, and is not recommended.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Even if you structure your MAPI program to loop through mailboxes, releasing
	each message store interface after use, you may still encounter the limit. A
	message store connection cannot be released if any outstanding objects are open
	on the store. The most commonly leaked interfaces are IMAPITable, IMAPIFolder,
	and IMessage. Note that if you do loop through mailboxes on a server, you must
	release all interfaces in the reverse order from which they were obtained.
	
	Under extreme circumstances, if you cannot locate the source of leaked
	interfaces, you can call the MAPIUninitialize function to cause MAPI to
	invalidate and recover all outstanding interfaces and memory.
	
	REFERENCES
	==========
	
	For additional information on opening mailboxes, click the article number below
	to view the article in the Microsoft Knowledge Base:
	
	  Q194627 HOWTO: Open Mailboxes with Privileged Access
	
	For additional information about how to loop through mailboxes, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q200160 HOWTO: Loop Through Mailboxes on Exchange Using GetMailboxTable
	
	Additional query words:
	
	======================================================================
	Keywords          : kbEDK kbExchange kbMsg kbMAPI100 kbGrpDSMsg kbDSupport 
	Technology        : kbAudDeveloper kbMAPISearch kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword kbZNotKeyword2 kbExchange400SP1 kbExchange400SP2 kbExchange400SP3 kbExchange400SP4 kbExchange400SP5 kbMAPIExt
	Version           : :1.0,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
