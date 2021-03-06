---
layout: page
title: "Q161561: SMS: Upgrade May Fail with SQL Integrated or Mixed Security"
permalink: /kb/161/Q161561/
---

## Q161561: SMS: Upgrade May Fail with SQL Integrated or Mixed Security

{% raw %}

	Article: Q161561
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbinterop kbsetup smssetupkbfixlist
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you attempt to upgrade Systems Management Server with a new version or
	service pack, it may stop responding at the "Preparing for Service Installation"
	message.
	
	The Smssetup.log file that is located in the root of drive C has the following
	information at the end of the log:
	
	     <11-22-1996 13:42:14> Executing upgrade script
	     SITE.SRV\X86.BIN\SP_SITE.SQL
	     <11-22-1996 13:42:18> Script execution returns code 0
	     <11-22-1996 13:42:18> Executing upgrade script
	     SITE.SRV\X86.BIN\UPGRD12.SQL
	     SMS SETUP Log > Beginning DBCNV12.SQL - Creating SNMP Traps tables.
	
	CAUSE
	=====
	
	This problem occurs when Microsoft SQL server is set for mixed or integrated
	security and the SQL Server logon ID for the Systems Management Server database
	is blank. During the upgrade, Setup calls a Systems Management Server utility
	that requires the SQL Server logon ID not to be null.
	
	WORKAROUND
	==========
	
	To work around this problem, change the SQL Server logon ID to SA (or another
	"dummy" logon ID) when using integrated security, and enter the correct
	password. Do this by going to Operations in Systems Management Server Setup, and
	then selecting Systems Management Server Database.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in System Management Server version
	1.2. This problem was corrected in the latest Microsoft Systems Management
	Server version 1.2 U.S. Service Pack. For information on obtaining the service
	pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	Using PViewer or something similar (with Windows NT Server 3.51) or Task Manager
	(with Windows NT Server 4.0) will likely show a process called Dbcnv12a.exe
	running when Setup stops responding. Setup waits for this process to complete
	before continuing. To start the upgrade again, you must stop Dbcnv12a.exe.
	
	Although Systems Management Server does not use the SQL Server logon ID when
	using SQL Server integrated security, the ID must not be blank. Use the method
	described in the WORKAROUND section of this article to change the SQL Server
	logon ID to a value that Systems Management Server requires. This can be a dummy
	value. Because SQL Server integrated security uses the currently logged on user
	ID for authentication, you will need to log on as the current Systems Management
	Server database owner (DBO) or a systems administrator (SA) equivalent.
	
	Additional query words: prodsms fail
	
	======================================================================
	Keywords          : kbinterop kbsetup smssetup kbfixlist
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
