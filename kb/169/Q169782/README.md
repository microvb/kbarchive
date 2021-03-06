---
layout: page
title: "Q169782: XFOR: POP3 and IMAP4 Clients That Work with Exchange Server"
permalink: /kb/169/Q169782/
---

## Q169782: XFOR: POP3 and IMAP4 Clients That Work with Exchange Server

{% raw %}

	Article: Q169782
	Product(s): Microsoft Exchange
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 12-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following POP3 clients were tested against Microsoft Exchange Server 5.0:
	
	  Microsoft MAPI POP provider (Win16/Win32)
	  Internet Explorer (Win16/Win32)
	  Eudora 2.0 / 3.0 (Win16/Win32/Macintosh)
	  Netscape 2.0 / 3.0 (Win16/Win32/Macintosh)
	  Pegasus (Freeware) (Win16/Win32)
	
	Many other, lesser known, clients were tested against the Exchange Server beta
	release.
	
	MORE INFORMATION
	================
	
	The Outlook Express Client can work as a POP3 client or as an IMAP client. You
	can select the type of the OE client during the setup process. OE is installed
	with Internet Explorer 4.0.
	
	Internet Message Access Protocol, version 4 rev. 1 (IMAP4), has more features
	than the POP3 protocol. With IMAP4, your mail is stored on the server, you can
	download the headers of a message (such as From, Subject, To)and you can decide
	to open only a few messages. With POP3, you must download the entire bodies of
	email in your Inbox.
	
	And unlike POP3, with IMAP you can access all of your mailbox folders. The IMAP4
	protocol was specified in RFC 2060, and is supported by Exchange Server 5.5 and
	above.
	
	POP and IMAP are both for receiving mail only. The SMTP protocol is used for
	sending email.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbZNotKeyword2
	Version           : :5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
