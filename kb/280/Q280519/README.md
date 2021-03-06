---
layout: page
title: "Q280519: Error &quot;The Specified Service Is Disabled&quot; When You Start WWW Ser"
permalink: /kb/280/Q280519/
---

## Q280519: Error &quot;The Specified Service Is Disabled&quot; When You Start WWW Ser

{% raw %}

	Article: Q280519
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbDSupport kbiis400
	Last Modified: 21-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to start the World Wide Web (WWW) Publishing Service, you may
	receive the following error message:
	
	  Could not start the World Wide Web Publishing Service service on
	  \\WEBSERVERNAME.
	
	  Error 1058. The specified service is disabled and cannot be started.
	
	As a result, the WWW Service fails to start. There are no corresponding event
	viewer errors for this error.
	
	This problem also occurs with File Transfer Protocol (FTP), Network News Transfer
	Protocol (NNTP), or Simple Mail Transfer Protocol (SMTP) services.
	
	CAUSE
	=====
	
	The WWW, FTP, NNTP, or SMTP service has been disabled and cannot be started
	until the service is reset to Automatic, Manual, or Enabled. When you install a
	third-party application that conflicts with one of these services, the
	third-party application's installer disables the service.
	
	RESOLUTION
	==========
	
	In Microsoft Windows NT and Internet Information Server (IIS), a service can be
	disabled either in the Startup settings (which is most common) or the Hardware
	Profile settings.
	
	NOTE: If one of these settings is changed, the other setting also changes to
	correspond with the first. Therefore, if the Startup setting is changed to
	Disabled, the Hardware Profile setting also reflects this change.
	
	Startup Settings:
	
	To correct this problem in the Startup settings, follow these steps:
	
	1. In Control Panel, double-click Services.
	
	2. Click to highlight the service that is failing, and then click Startup.
	
	3. In the Startup type drop-down list, click Automatic or Manual.
	
	4. Close the Startup screen, and click to start the service.
	
	Hardware Profile Settings:
	
	This setting is designed to assist those computers that have multiple
	configurations. Third-party applications often disable the service in this area
	to ensure that these services do not disrupt their product. To check and correct
	problems in Hardware Profile, follow these steps:
	
	1. In Control Panel, double-click Services.
	
	2. Click to highlight the service that is failing, and then click Hardware
	  Profiles.
	
	3. Verify that the setting for the original configuration is enabled. If not,
	  double-click to change the setting.
	
	MORE INFORMATION
	================
	
	For additional information about other causes of error 1058, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q181835 Unable to Start the Server Service
	
	  Q182989 XCON: Attempt to Start MTA Fails with Error 1058
	
	Additional query words: iis4 iis5 unable start 1058 www ftp smtp nntp
	
	======================================================================
	Keywords          : kbDSupport kbiis400 
	Technology        : kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
