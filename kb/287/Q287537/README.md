---
layout: page
title: "Q287537: Using Basic Authentication to Generate Kerberos Tokens"
permalink: /kb/287/Q287537/
---

## Q287537: Using Basic Authentication to Generate Kerberos Tokens

{% raw %}

	Article: Q287537
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you use Basic authentication to connect to a Web site that is hosted by
	Internet Information Services (IIS), you can take advantage of the delegation
	features of Kerberos to authenticate on multiple back-end servers, such as a
	Microsoft SQL Server that is called from Active Server Pages (ASP) running on
	IIS. To generate a Kerberos token, IIS must be a member of a Windows 2000 domain
	and have access to that domain's active directory.
	
	MORE INFORMATION
	================
	
	When IIS authenticates users it does so by calling the LsaLogonUser function,
	which in turn calls an authentication package
	(MICROSOFT_AUTHENTICATION_PACKAGE_V1_0 for Basic authentication). When Basic
	authentication occurs, the following event is written to the security log IIS
	5.0 server, assuming the Audit Logon Events policy is enabled:
	
	  Event Type:	Success Audit
	  Event Source:	Security
	  Event Category:	Logon/Logoff 
	  Event ID:	528
	  Date:		1/5/2001
	  Time:		6:11:04 PM
	  User:		Win2kDomain\rvittal
	  Computer:	IIS5server
	  Description:
	  Successful Logon:
	   	User Name:       	rvittal
	   	Domain:		Win2kDomain
	   	Logon ID:		(0x0,0x148D0AC)
	   	Logon Type:	             2
	   	Logon Process:	IIS     
	   	Authentication Package:	MICROSOFT_AUTHENTICATION_PACKAGE_V1_0
	   	Workstation Name:	IIS5server<BR/>
	
	After a user has logged into IIS with Basic authentication, IIS has that user's
	credentials (username:password), and can use those credentials to generate a
	token that can be used to impersonate the user on other computers. When a user
	requests a Web page that references resources on another Windows 2000 server,
	the IIS server generates a Kerberos security token and an event similar to the
	following is written in the security log on the remote server:
	
	  Event Type:	Success Audit
	  Event Source:	Security
	  Event Category:	Logon/Logoff 
	  Event ID:	540
	  Date:		1/5/2001
	  Time:		1:16:06 PM
	  User:		Win2kDomain\rvittal
	  Computer:	SQLbox
	  Description:
	  Successful Network Logon:
	   	User Name:	             rvittal
	   	Domain:		Win2kDomain
	   	Logon ID:		(0x0,0x13A667F)
	   	Logon Type:	             3
	   	Logon Process:	             Kerberos
	   	Authentication Package: Kerberos
	   	Workstation Name:	
	
	Note that using Kerberos is not limited to Basic authentication. By default, if a
	Windows 2000 client attaches to an IIS5 server that is configured with
	Integrated authentication, Kerberos authentication is used.
	
	REFERENCES
	==========
	
	This article is based on the information provided on page 109 of the following
	book:
	
	Howard, Michael, Richard Waymire, and Marc Levy. Designing Secure Web-Based
	Applications for Microsoft<AE> Windows 2000 (Redmond: Microsoft Press, July 2000),
	p. 109.
	
	For additional information on authentication methods in IIS, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q264921 INFO: How IIS Authenticates Browser Clients
	
	  Q229694 How to Use the IIS Security 'What If' Tool
	
	For more information on Kerberos, see the following articles in the Microsoft
	Knowledge Base:
	
	  Q217098 Basic Overview of Kerberos User Authentication Protocol in Windows
	  2000
	
	  Q266080 Answers to Frequently Asked Kerberos Questions
	
	  Q231789 Local Logon Process for Windows 2000
	
	Additional query words: iis 5
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
