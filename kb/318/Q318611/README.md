---
layout: page
title: "Q318611: How to Associate 3270 Display LUs with 3270 Printer LUs"
permalink: /kb/318/Q318611/
---

## Q318611: How to Associate 3270 Display LUs with 3270 Printer LUs

{% raw %}

	Article: Q318611
	Product(s): Microsoft SNA Server
	Version(s): 3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains how to associate 3270 display logical units (LUs) with
	3270 printer LUs.
	
	MORE INFORMATION
	================
	
	From Server Manager
	-------------------
	
	1. Add one or more 3270 display LUs and corresponding 3270 printer LUs to a
	  connection.
	
	2. Select a display LU.
	
	3. On the View menu, click Properties.
	
	4. On the Associated Printers tab, select a printer LU from the Associated
	  Printer LU list box.
	
	5. Repeat steps 2 through 4 for each display LU that you want to associate with
	  a printer LU.
	
	6. On the Action menu, click Save configuration.
	
	NOTE: Microsoft recommends that you assign the display LUs to a pool and then
	configure the pool with the appropriate users or groups. On the Pool properties
	page, make sure that you select the option "Pool Contains Display LUs with
	Associated Printers".
	
	From the Client Computer That Runs the Third-party Emulator
	-----------------------------------------------------------
	
	1. Configure a display session as you do normally.
	
	2. Configure a printer session. ASSOCPRT now appears in the drop-down list box
	  of available resources.
	
	3. Select ASSOCPRT as the LU, and then connect.
	
	This feature is designed to support specialized host applications that have
	hard-coded associations between display LUs and printer LUs. When a 3270 display
	LU is configured to have an associated printer, and is later assigned to a user
	or group, users can see both the display LU and a special printer LU named
	ASSOCPRT. When users connect to the display LU, they can open the ASSOCPRT LU,
	which SNA Server maps to the defined associated printer LU.
	
	When you assign multiple display LUs to users, the order in which the resources
	are opened is critical. If all of the display LUs have associated printers, the
	user should alternate opening displays and ASSOCPRTs. If some of the display LUs
	do not have associated printers, use a naming convention to help the user
	distinguish the display LUs that have associated printers from the display LUs
	that do not have associated printers.
	
	REFERENCES
	==========
	
	For additional information about TN3270 Associated Printers, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q318612 How to Associate TN3270 Display LUs with TN3270 Printer LUs
	
	For more information, see the "Associate 3270 Printer LUs with 3270 Display LUs"
	topic in the Host Integration Server online Help documentation, which is located
	in the <SNA 4.0 Server CD>Docs\Admin.pdf file.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ400SP4 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : :3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
