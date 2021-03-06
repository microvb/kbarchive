---
layout: page
title: "Q171589: SMS: SMSRUN16 Seems to Stop When Selecting a Logon Server"
permalink: /kb/171/Q171589/
---

## Q171589: SMS: SMSRUN16 Seems to Stop When Selecting a Logon Server

{% raw %}

	Article: Q171589
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kbnetwork smsgeneral kbArtTypeINF
	Last Modified: 27-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	SMSRUN16 may appear to stop responding during Systems Management Server logon
	server selection when underlying networking problems exist. There is no way to
	stop SMSRUN16's server selection process.
	
	CAUSE
	=====
	
	SMSRUN16 attempts to verify that at least one Systems Management Server logon
	server is accessible to the current logged-on user. In Systems Management Server
	1.2, SMSRUN16 attempts to connect to the server listed as the CurrentLogonServer
	in the Sms.ini file. If this connection is unsuccessful, SMSRUN16 will try each
	listed server in the [Servers] section of the Sms.ini file until it successfully
	connects to a server or exhausts the list.
	
	If networking problems exist or some of the logon servers are unavailable during
	SMSRUN16's server selection process, the connection timeout, in conjunction with
	the number of servers in the [Servers] section, may give the appearance that the
	computer has stopped responding. However, control will be returned to the user
	after SMSRUN16 has completed its server selection process.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	versions 1.0, 1.1, and 1.2. This problem was corrected in the latest Microsoft
	Systems Management Server 1.2 U.S. Service Pack. For information on obtaining
	the service pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	With the hotfix installed, if SMSRUN16's attempt to connect to the
	CurrentLogonServer is not successful, a "Logon server not found" message box
	appears. This message box asks:
	
	  Continue looking for logon servers?
	
	The user can click Yes to continue looking for logon servers or No to stop the
	SMSRUN16 server selection process.
	
	Additional query words: prodsms hang hung machine crash crashed
	
	======================================================================
	Keywords          : kbnetwork smsgeneral kbArtTypeINF 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
