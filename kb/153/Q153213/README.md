---
layout: page
title: "Q153213: XCLN: Can't Change Windows NT 3.51 Password w/ AppleTalk"
permalink: /kb/153/Q153213/
---

## Q153213: XCLN: Can't Change Windows NT 3.51 Password w/ AppleTalk

{% raw %}

	Article: Q153213
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0; winnt:3.51
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 18-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Macintosh client, versions 4.0, 5.0 
	- the operating system: Microsoft Windows NT 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You cannot change the Windows NT account information from within the Microsoft
	Exchange client for Macintosh when the profile is configured to use AppleTalk
	and the Microsoft Exchange Server is running under Microsoft Windows NT version
	3.51.
	
	Note: If the primary domain controller (PDC) is running Windows NT 4.0, please
	see the following articles in the Microsoft Knowledge Base:
	
	  Q127943 Mac Client Can't Log On Because Password Has Expired
	
	  Q140641 Updated Samsrv.dll Supports AppleTalk and Banyan Vines Clients
	
	
	WORKAROUND
	==========
	
	There are two ways you can work around this problem:
	
	Workaround 1
	------------
	
	1. Open the Chooser and click AppleShare.
	
	2. Select the AppleTalk Zone where the Microsoft Exchange Server is located.
	
	3. Select the appropriate file server name.
	
	4. Click Set Password and follow the prompts.
	
	Workaround 2
	------------
	
	1. Make sure MacTCP 2.0.6 or higher, OpenTransport TCP/IP, is configured. This
	  can be tested by using MacTCP ping, to make sure the Microsoft Exchange
	  Server name can be resolved. Use Ping exchsrvr1.
	
	2. Use TCP/IP in the profile instead of AppleTalk. To do this:
	
	  a. Open the Microsoft Exchange Settings tool.
	
	  b. Click Show Profiles, Add, and Next, and type a name.
	
	  c. Make sure TCP/IP is selected.
	
	  d. Enter the appropriate account and Microsoft Exchange Server name.
	
	  e. Finish creating the profile and make it the profile to be used when
	     starting the Microsoft Exchange client.
	
	  f. Close the Microsoft Exchange Settings tool.
	
	3. Start the Microsoft Exchange client.
	
	4. To change the Windows NT password, on the Tools menu, click Options, and
	  click Microsoft Exchange Server.
	
	NOTE: This workaround will only work if the PDC is Windows NT version 3.51 or
	higher. The Microsoft Exchange Server must also be at Service Pack 2 or later.
	
	Workaround 3
	------------
	
	1. Upgrade the Microsoft Exchange Server computer to Windows NT 4.0.
	
	2. Upgrade to Microsoft Exchange Service Pack 2. For information on obtaining
	  this Service Pack, query on the following word in the Microsoft Knowledge
	  Base (without the spaces):
	
	  S E R V P A C K
	
	3. See Q156182 for complete list of steps, including adding registry entries to
	  Windows NT PDC.
	
	MORE INFORMATION
	================
	
	If the primary domain controller (PDC) is running Windows NT 4.0, please see the
	following articles in the Microsoft Knowledge Base:
	
	  Q127943 Mac Client Can't Log On Because Password Has Expired
	
	  Q140641 Updated Samsrv.dll Supports AppleTalk and Banyan Vines Clients
	
	NOTE: You need the following settings, depending on the transport the you are
	using, on the Primary Domain Controller for this to work. These settings are not
	in the registry by default.
	
	PDC Registry Settings:
	
	  HKEY_LOCAL_MACHINE\system\currentcontrolset\lsa
	
	  NetwareClientSupport REG_DWORD 1
	  TCPIPClientSupport REG_DWORD 1
	  AppletalkClientSupport REG_DWORD 1
	  VinesClientSupport REG_DWORD 1
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbWinNTsearch kbWinNTSsearch kbHWMAC kbOSMAC kbExchangeSearch kbExchange400 kbExchangeClientSearch kbGraph500
	Version           : WINDOWS:4.0,5.0; winnt:3.51
	
	=============================================================================
	

{% endraw %}
