---
layout: page
title: "Q316616: &quot;Event ID 4018&quot; Error Message When You Try to Send E-Mail"
permalink: /kb/316/Q316616/
---

## Q316616: &quot;Event ID 4018&quot; Error Message When You Try to Send E-Mail

{% raw %}

	Article: Q316616
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): kberrmsg ocsso
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to send e-mail messages through Exchange Server 5.5, your
	messages may not be delivered. Additionally, you may not receive mail as
	expected. In the list of services under Computer Management (click Start, point
	to Programs, point to Administrative Tools, and then click Computer Management),
	it appears that Internet Mail Service is not running. When you attempt to
	manually start Internet Mail Service, the service does not start and the
	following events are displayed in the Event Viewer:
	
	  Event ID: 4018
	  Type: Error
	  Source: MSExchangeIMC
	  Description: Unable to start the Internet Mail Connector service because MAPI
	  could not be initialized.
	
	-and-
	
	  Event ID: 4116
	  Type: Error
	  Source: MSExchangeIMC
	  Description: An error was returned from the messaging software, the Internet
	  Mail Service uses, to process messages on the Microsoft Exchange Server. It
	  is possible that the piece of mail being processed at the time will not be
	  delivered. The message that was being processed has been moved to the "BAD"
	  folder. Use the appropriate utilities found in the SUPPORT directory of your
	  Exchange CD to view and manipulate these messages.
	
	CAUSE
	=====
	
	This behavior can occur if the version of the Mapi32.dll file that is installed
	on your computer is not compatible with the installed Exchange Server service
	pack.
	
	RESOLUTION
	==========
	
	To resolve this issue, verify that the Mapi32.dll file on your system is the
	correct version for the currently installed Exchange Server service pack. If the
	version installed on your system is incorrect, replace Mapi32.dll with the
	correct version.
	
	To determine the version of the Mapi32.dll file on your computer, follow these
	steps:
	
	1. Navigate to the <drive>:\winnt\system32 folder.
	
	2. Right-click Mapi32.dll, and then click Properties.
	
	3. In the Properties dialog box, click the Version tab. Note the version number
	  that is displayed at the top of this window.
	
	4. Ensure that the version number matches the service pack that is installed on
	  your computer. To do this, consult the following table.
	
	  Service pack version         Mapi32.dll version number
	  ------------------------------------------------------
	  No service pack installed        5.5.1960
	  Service Pack 1                   5.5.2232
	  Service Pack 2                   5.5.2448
	  Service Pack 3                   5.5.2650
	
	To replace the Mapi32.dll file on your computer, follow these steps:
	
	1. In Windows Explorer, right-click the Mapi32.dll file that you located in step
	  2 in the first set of steps in the "Resolution" section of this article, and
	  then click Rename.
	
	2. Type "Mapi32.dll.old" (without the quotation marks), and then press ENTER.
	
	3. Insert the Exchange Server 5.5 CD-ROM into your computer's CD-ROM or DVD-ROM
	  drive, and then navigate to the
	  <drive>:\server\enterprise\setup\i386\exchange folder.
	
	4. Right-click the Mapi32.dll file, and then click Copy.
	
	5. In Windows Explorer, navigate to the <drive>:\winnt\system32 folder.
	
	6. On the Edit menu, click Paste.
	
	7. Restart your computer.
	
	NOTE: You must reinstall any Exchange Server service packs that were previously
	installed on your computer.
	
	MORE INFORMATION
	================
	
	For additional information about Exchange Server service packs, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q301378 How to Obtain the Latest Exchange 2000 Server Service Pack
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg ocsso 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
