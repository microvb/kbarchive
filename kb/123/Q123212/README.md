---
layout: page
title: "Q123212: How to Set Up SMS to a Remote SQL Server"
permalink: /kb/123/Q123212/
---

## Q123212: How to Set Up SMS to a Remote SQL Server

{% raw %}

	Article: Q123212
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbsetup kbDatabase kbHMan smssetup smsdatabase smshierman
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following procedures will guide you through setting up a primary site server
	on a remote SQL Server.
	
	MORE INFORMATION
	================
	
	Installing SQL Server
	---------------------
	
	1. Install SQL Server on the Windows NT domain server. Follow SQL Server
	  documentation.
	
	  NOTE: All device names and passwords are case-sensitive.
	
	2. Start SQL Administrator to create new devices for the remote Systems
	  Management Server computer.
	
	3. Connect to the SQL Server computer using the correct login name and password.
	
	4. Click the Devices icon.
	
	5. On the Manage menu, click Devices.
	
	6. Click Create.
	
	7. Enter a logical name. SQL Server Administrator will generate a physical name
	  with a .dat extension.
	
	8. Select database for the type and use the size you think is correct for your
	  site. The more computers to be inventoried, the larger the database should
	  be. Use 40 KB to 50 KB per computer.
	
	9. Click OK.
	
	10. Repeat steps 4 through 8 for LOG device creation changing the .dat file
	  extensions to .log. Do not change the device number for either the DB or the
	  LOG device creation.
	
	11. Do not create a new database. The Systems Management Server Setup program
	  creates the Systems Management Server databases dynamically and attaches the
	  devices.
	
	Installing Systems Management Server
	------------------------------------
	
	1. Create a user account for the Systems Management Server Service Account. This
	  account must be a member of either the Administrators local group or the
	  Trusted Domains Administrators group. Ensure that this user can log on as a
	  service.
	
	  If the SQL database is located on a non-trusted domain, ensure that the user
	  account you have created in your domain has the same username and password as
	  the remote SQL Server.
	
	  NOTE: If this procedure is not done properly, the following error message may
	  appear:
	
	  Hierarchy Manager is not responding to instructions.
	
	  Also, if running the SMS setup program and the SQL database is located on a
	  non-trusted domain ensure that the currently logged in user has a duplicate
	  account and same password in the remote domain or you could get the following
	  error dialog when attempting to change the service account, SMS account, or a
	  site reset:
	
	  Error: Cannot start SQL server
	  Cannot change service account (or SQL account)
	
	2. Install Systems Management Server.
	
	3. When prompted about SQL Server, enter the computer name of the remote SQL
	  Server computer.
	
	4. Complete the fields on the screen until you get to the database name, device,
	  and log device. Enter the device names that you chose on the remote SQL
	  Server computer. Systems Management Server Setup creates the database
	  dynamically in order to attach to the manually created devices.
	
	5. Click OK and proceed with the rest of the Systems Management Server
	  installation.
	
	Additional query words: sms prodsms
	
	======================================================================
	Keywords          : kbnetwork kbsetup kbDatabase kbHMan smssetup smsdatabase smshierman 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
