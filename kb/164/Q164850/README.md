---
layout: page
title: "Q164850: XFOR: Message Loop between Exchange and Microsoft Mail"
permalink: /kb/164/Q164850/
---

## Q164850: XFOR: Message Loop between Exchange and Microsoft Mail

{% raw %}

	Article: Q164850
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbinterop kbusage exc4 exc5 exc55
	Last Modified: 19-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	You may experience a problem in which a message loops back and forth between
	Microsoft Mail for PC Networks and Microsoft Exchange Server. Three things must
	hold true for this to occur:
	
	- A Macintosh Distribution List (DL) is created that contains an Exchange
	  Server DL (which was imported by means of the Exchange Server Connection
	  Directory Exchange Requestor [DER] or by means of a manual Import).
	
	- The Exchange Server DL contains a Macintosh User (or an Exchange Server user
	  who has been configured to have an Alternate Recipient that is a Macintosh
	  user).
	
	- A Macintosh user submits a message to the Macintosh DL.
	
	RESOLUTION
	==========
	
	To prevent the loop, you must create a Custom Recipient on the Exchange Server
	computer for the Macintosh DL. To do this, follow these steps:
	
	1. If the Macintosh DL is called MAC DL@MACSERVER, create a Custom Recipient of
	  the e-mail address type: MacMail Address.
	
	2. In the MacMail Address properties page, enter the Distribution List Name in
	  the User Name field and the Macintosh server name in the Server Name field.
	
	  Display Name:MAC DL@MACSERVER (Or whatever you like)
	  User Name:MAC DL
	  Server Name:MACSERVER
	
	3. To completely remove all cases of message loops, the DER should be used to
	  fully import all Microsoft Mail addresses into Exchange Server (or else do a
	  manual import of all addresses).
	
	MORE INFORMATION
	================
	
	In this situation, the message is delivered to all recipients listed in the
	Macintosh DL. Because it contains a foreign mail address (the Exchange Server
	DL), the message is submitted to the Exchange Server Connection gateway, which
	in turn moves the message over to the Exchange Connector postoffice (in the
	Mactopc directory).
	
	On Exchange Server, the message is picked up by the Microsoft Mail Connector
	(AppleTalk) message transfer agent (MTA) and it moves it from the Mactopc
	directory to the Exchange Connector postoffice.
	
	The MS Mail Connector Interchange (MSMI) takes the message and sends it to the
	Exchange Server computer. The server expands the DL and delivers the message to
	each recipient. When the Macintosh user is encountered in the DL, the message is
	sent back to the MS Mail Connector (AppleTalk) in the reverse path.
	
	The MS Mail Connector (AppleTalk) takes the message, and moves it to the location
	in the Exchange Connector postoffice (the Pctomac directory) where the Microsoft
	Exchange Connection gateway is expecting new messages. During this activity, the
	MS Mail Connector (AppleTalk) assumes responsibility for submitting any address
	found in the message that is an AppleTalk address type (MS Mail [AppleTalk]),
	including the original Macintosh DL that the Macintosh user originally submitted
	the message for.
	
	When the message is finally received again by the Microsoft Mail for AppleTalk
	Networks server, it resubmits the message to the Macintosh DL, which causes the
	loop.
	
	Correcting the Message Loop
	---------------------------
	
	When an AppleTalk address (MS Mail [AppleTalk]) is received by Exchange Server
	from the MSMI, the address is compared to all the custom recipient (CR)
	addresses.
	
	If a match is found, the directory name for the matching CR is used for routing
	purposes while in Exchange Server. On its way back out of the MSMI, it will be
	sent to the custom recipient's Microsoft-type address (changed to CSI address
	types when handled by the MS Mail Connector [AppleTalk]).
	
	For instance, a Macintosh user who has an address of (as viewed by the MS Mail
	Connector [AppleTalk])
	
	  TYPE: MSMAIL (MSA)
	  USER: MACUSER@MACSERVER
	
	and a CR in Exchange Server, the address would be converted on its way back out
	the MSMI to
	
	  TYPE: CSI
	  USER: NET/PO/MACUSER
	
	When the MS Mail Connector (AppleTalk) looks at a message to be handled, it will
	not assume responsibility for this address because it only assumes
	responsibility for MS Mail-type addresses.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
