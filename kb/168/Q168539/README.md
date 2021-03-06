---
layout: page
title: "Q168539: XFOR: How to Delete Exchange Dirsync Server"
permalink: /kb/168/Q168539/
---

## Q168539: XFOR: How to Delete Exchange Dirsync Server

{% raw %}

	Article: Q168539
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage exc4 exc5 exc55
	Last Modified: 19-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about using Registry Editor.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	When you delete the Microsoft Mail Connector (MSMC) and then try to delete the
	dirsync server object, the following error message appears :
	
	  THE ATTRIBUTE DOES NOT EXIST
	  Microsoft Exchange dir: ID NO: DS_E_NO_SUCH_ATTRIBUTE_OR_VALUE
	
	RESOLUTION
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" online Help topic in Registry Editor (Regedit.exe) or the "Add and
	Delete Information in the Registry" and "Edit Registry Data" online Help topics
	in Regedt32.exe. Note that you should back up the registry before you edit it.
	
	WARNING: Using the raw mode of the Exchange Server Administrator program (admin
	/r) incorrectly can cause serious problems that may require you to reinstall
	Microsoft Windows NT Server and/or Microsoft Exchange Server. Microsoft cannot
	guarantee that problems resulting from the incorrect use of raw mode can be
	solved. Use raw mode at your own risk.
	
	To resolve this problem:
	
	1. Verify that there is no requestor object under this dirsync server object.
	
	2. Verify that the Exchange Directory Synchronization service is not running by
	  inspecting Control Panel Services.
	
	3. Start Registry Editor. Go to the following key
	
	     HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services
	
	  and confirm that the MSExchangeDX service does not exist.
	
	4. Start the Exchange Server Administrator program in raw mode by typing the
	  following at a command prompt:
	
	  admin /r
	
	5. Select the Dirsync Server to highlight it. On the Edit menu, click Delete Raw
	  Object
	
	6. Click OK in response to the following warning message:
	
	  A raw delete should not be performed without prior consultation with
	  Microsoft Product Support Services. Do not proceed unless you
	  completely understand the potential adverse effects that incorrect
	  usage of this feature could have on an entire site.
	
	Additional query words: dss msmi
	
	======================================================================
	Keywords          : kbusage exc4 exc5 exc55 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
