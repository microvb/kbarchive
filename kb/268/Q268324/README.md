---
layout: page
title: "Q268324: XCLN: Corrupted Offline Address Books from Changes to PDN List"
permalink: /kb/268/Q268324/
---

## Q268324: XCLN: Corrupted Offline Address Books from Changes to PDN List

{% raw %}

	Article: Q268324
	Product(s): Microsoft Exchange
	Version(s): 
	Operating System(s): 
	Keyword(s): kbExchange550preSP4fix kbOffice2000preSR2fix kbExchange550sp4Fix kbExchange2000SP1Fix
	Last Modified: 13-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook 98 
	- Microsoft Outlook 2000 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	Outlook 98 for Microsoft Windows NT or Outlook 2000 for Microsoft Windows NT
	users who use the offline Address Book may not be able to send an e-mail message
	to a user in the offline Address Book. After the user sends the e-mail message,
	the user may receive non-delivery report (NDR) error messages that are similar
	to the following:
	
	  
	
	  Your message did not reach some or all of the intended recipients. 
	
	     Subject:  Subject of the Message 
	     Sent:     6/18/00 2:00 PM 
	
	  The following recipient(s) could not be reached: 
	
	     Andersen, Amy on 6/18/00 2:00 PM 
	           The message was undelivered because the specified recipient postal address was incorrect 
	           MSEXCH:MSExchangeIS:SITENAME:SERVERNAME
	
	  -or-
	
	  Your message did not reach some or all of the intended recipients. 
	
	     Subject:  Subject of the Message 
	     Sent:     6/27/00 2:51 PM 
	
	  The following recipient(s) could not be reached: 
	
	     's/cn=DirectoryName' on 6/27/00 2:51 PM 
	           No transport provider was available for delivery to this recipent.
	
	This issue occurs when users perform incremental offline Address Book downloads
	rather than full offline Address Book downloads.
	
	CAUSE
	=====
	
	This issue can occur if the parent distinguished name (PDN) list changes on the
	server.
	
	RESOLUTION
	==========
	
	To resolve this problem:
	
	1. Obtain the latest service pack for Exchange Server 5.5.
	
	2. For Outlook 2000 clients, obtain SP 2 for Office 2000.
	
	NOTE: For Outlook 98 clients, contact Microsoft Product Support Services to
	obtain a fix. Visit the following Microsoft Web site at:
	
	  http://support.microsoft.com/directory/default.asp
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Outlook 98
	
	+----------------------------+
	| File name    | Version     | 
	+----------------------------+
	| Emsabp32.dll | 5.5.2654.5  | 
	+----------------------------+
	| Emsmdb32.dll | 5.5.2652.94 | 
	+----------------------------+
	| Emsui32.dll  | 5.5.2651.80 | 
	+----------------------------+
	| Mspst32.dll  | 5.5.2651.85 | 
	+----------------------------+
	
	Component: Outlook 2000
	
	+---------------------------+
	| File name    | Version    | 
	+---------------------------+
	| Emsabp32.dll | 5.5.3142.0 | 
	+---------------------------+
	| Emsui32.dll  | 5.5.3141.0 | 
	+---------------------------+
	| Mspst32.dll  | 5.5.3138.0 | 
	+---------------------------+
	| Exsec32.dll  | 5.5.3137.0 | 
	+---------------------------+
	| Contab32.dll | 9.0.0.4221 | 
	+---------------------------+
	| Pstprx32.dll | 9.0.3929.0 | 
	+---------------------------+
	| Bjablr32.dll | 1.0.3.26   | 
	+---------------------------+
	| Bjlogb32.dll | 3.2.0.26   | 
	+---------------------------+
	| Bjsrch32.dll | 1.0.3.26   | 
	+---------------------------+
	| Emablt32.dll | 1.0.3.26   | 
	+---------------------------+
	
	
	
	WORKAROUND
	==========
	
	To work around this issue, perform a full offline Address Book download.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Outlook 98 and
	Microsoft Outlook 2000. This problem was first corrected in Exchange Server 5.5
	Service Pack 4.
	
	MORE INFORMATION
	================
	
	There is an architectural limitation in the offline Address Book differential
	download mechanism. This section describes how the offline Address Book works
	and how this limitation is manifested.
	
	On the server, the Exchange Server system attendant creates an offline Address
	Book and places that offline Address Book in a public folder. To do this, the
	system attendant calls the Oabgen.dll file. This file contains all of the
	functions to create and update an offline Address Book. On the server, the
	offline Address Book is completely contained in an e-mail message as
	attachments. This e-mail message is placed in a public folder so that all
	clients can retrieve this e-mail message. To create the offline Address Book,
	the Oabgen.dll file scans all the entries in the global address list and builds
	the list from the global address list. In the offline Address Book, a PDN block
	is created that has all of the container names that have e-mail objects in the
	global address list. The following is an example of a PDN:
	
	  /o=Organization/ou=Site/cn=Recipients
	
	An offline Address Book also contains relative distinguished names (RDNs). This
	is the user's directory name in the Exchange Server Administrator program. The
	following is an example of an RDN:
	
	  /cn=TestUser
	
	The offline Address Book organizes a user by joining the RDN with the PDN, so
	that the user is actually the following:
	
	  /o=Organization/ou=Site/cn=Recipients/cn=TestUser
	
	To put the two pieces together, there are pointers in the records that indicate
	that the address Test User is composed of the RDN at offset x, which is
	/cn=TestUser, and the PDN at offset y, which contains
	/o=Organization/ou=Site/cn=Recipients.
	
	When an offline Address Book generation is run, two messages are created in a
	public folder: a message that contains a full download and a message that
	contains the changes after the last full download message was created. If there
	are new containers in the global address list after the last full download
	message was created, the PDN block is updated alphabetically with the new entry,
	and the new RDN to the changes message is included. When this new RDN is added
	to the changes message, a pointer to the PDN block offset is included.
	
	If a user requests a differential download at this point, Outlook locates the
	changes message, and incorporates the changes into the current offline Address
	Book that is on the client. It is at this point that the limitation of the
	offline Address Book is manifested. Because the client only retrieves the
	changes message, and not the full download message, the client has an out of
	date PDN block. The PDN block that the client now has may not have a PDN for the
	new RDNs that were just merged, or if a container was removed, the PDN on the
	client still may contain that container.
	
	If a new user was just merged, the user's offline Address Book may point to a PDN
	block that does not exist. This incorrect pointer can cause NDRs if the user
	tries to send a message to that user. The only way to make the user's PDN block
	match the server's PDN block is to perform a full download. The full download
	uses the full download message from the public folder, and therefore obtains the
	correct PDN list. This enables future differential downloads to work with the
	updated PDN block. This offline Address Book works correctly until the container
	structure changes.
	
	Offline Address Book corruption can appear somewhat random because the PDN block
	is sorted alphabetically. If an entry is added to the PDN block, old pointers in
	the user's offline Address Book point to a totally incorrect place in the PDN
	block. Similarly, if an entry is removed from the PDN list, the pointers are
	incorrect.
	
	What the Fix Does
	-----------------
	
	Microsoft has developed a resolution for the preceding issue. In this fix, both
	the server and the client have been modified. This section describes how this
	fix addresses this issue.
	
	On the Server:
	
	On the server, the Oabgen.dll file has been modified so that if the PDN list must
	be modified, the Oabgen.dll file does not post a changes message. This choice
	leverages behavior that the client exhibits if the changes message is absent,
	which is explained in the following section.
	
	On the Client:
	
	On the client, the Emsabp32.dll file has been modified to locate one of the
	following registry keys:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft\Exchange\Exchange Provider
	  Value: Allow Full OAB Prompt
	  Type: REG_DWORD
	  Data: 0 is disabled, 1 or nonzero is enabled
	
	  HKEY_CURRENT_USER\Software\Microsoft\Exchange\Exchange Provider
	  Value: Allow Full OAB Prompt
	  Type: REG_DWORD
	  Data: 0 is disabled, 1 or nonzero is enabled
	
	NOTE: The HKEY_CURRENT_USER value overrides the HKEY_LOCAL_MACHINE value if both
	values are present.
	
	If either of the preceding registry keys are enabled, a user requests a
	differential download, and the client cannot find the changes message in the
	public folder, a dialog box is displayed that contains the following text:
	
	  Outlook is about to download a full version of the offline Address Book.
	  Would you like to continue?
	
	The user can click Yes or No in this dialog box. If the user clicks No, nothing
	is downloaded, and the user can continue to use the current offline Address
	Book. This behavior is necessary to ensure that if users are connected over a
	slow link, those users can stop a full download from occurring. This way, a user
	can schedule a full download when a full download is convenient.
	If the Emsabp32.dll file does not find the registry keys, or the registry values
	are set to zero, Outlook reverts to the default behavior of the Emsabp32.dll
	file, which downloads the full offline Address Book if the changes message is
	not found. Also, there is no indication to the user that a full download is in
	progress. In some cases, a full offline Address Book download can take several
	hours.
	
	If the user clicks Yes in the dialog box, a full offline Address Book is
	downloaded. This keeps the user's PDN list up to date with the server's PDN
	list.
	
	
	Additional query words: OAB GAL
	
	======================================================================
	Keywords          : kbExchange550preSP4fix kbOffice2000preSR2fix kbExchange550sp4Fix kbExchange2000SP1Fix 
	Technology        : kbOutlookSearch kbOutlook2000Search kbOutlook98Search kbZNotKeyword3
	Version           : :
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
