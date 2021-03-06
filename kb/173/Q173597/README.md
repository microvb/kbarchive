---
layout: page
title: "Q173597: XCLN: Migrating PAB Entries From Microsoft"
permalink: /kb/173/Q173597/
---

## Q173597: XCLN: Migrating PAB Entries From Microsoft

{% raw %}

	Article: Q173597
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:5.0,5.5; :8.0,8.01,8.02,8.03
	Operating System(s): 
	Keyword(s): 
	Last Modified: 24-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, versions 5.0, 5.5 
	- Microsoft Exchange Windows 95/98 client, versions 5.0, 5.5 
	- Microsoft Exchange Windows NT client, versions 5.0, 5.5 
	- Microsoft Outlook 97, versions 8.0, 8.01, 8.02, 8.03 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If any entries are migrated from a personal address book (PAB) when you migrate
	from Microsoft Mail to Microsoft Exchange using the Microsoft Exchange Server
	Migration Wizard, then you will receive a message from the Exchange Server
	computer with instructions on how to import these entries into the Microsoft
	Exchange Client. This article contains instructions on how to import PAB entries
	into the Microsoft Outlook Client.
	
	MORE INFORMATION
	================
	
	Clients attach to the Exchange Server information store using MAPI. Because the
	Microsoft Exchange Server computer does not know what type of client is attached
	to it, the Exchange Server computer does not produce a message for all the
	variations of clients available.
	
	To import PAB entries into the Microsoft Outlook Client, follow these steps:
	
	1. From the File menu in Microsoft Outlook, select Save Attachments.
	
	2. Click the Save button to save the .pab file.
	
	3. From the File menu, select Import and Export to activate the Import and
	  Export Wizard.
	
	4. In the the Import and Export Wizard, select Import from a Microsoft Mail file
	  (.mmf), and click Next.
	
	5. Select the .pab file and click the Open button.
	
	6. Click the OK button when you are asked to confirm the personal address book
	  you have selected.
	
	7. An Import Mail Data completion message box will appear detailing the imported
	  messages and PAB entries.
	
	Additional query words: migrate migration PAB personal address book mail outlook import
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbExchangeSearch kbExchange500 kbExchangeClientSearch kbZNotKeyword kbOutlook97 kbZNotKeyword2 kbOutlook97Search kbZNotKeyword3 kbOutlook801 kbOutlook802 kbOutlook803 kbExchange500NT kbExchange500Win95
	Version           : WINDOWS:5.0,5.5; :8.0,8.01,8.02,8.03
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
