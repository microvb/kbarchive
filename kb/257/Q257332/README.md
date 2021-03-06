---
layout: page
title: "Q257332: Error in W3svc.dll on Secure Connection to Nonexistant IP:PORT"
permalink: /kb/257/Q257332/
---

## Q257332: Error in W3svc.dll on Secure Connection to Nonexistant IP:PORT

{% raw %}

	Article: Q257332
	Product(s): Internet Information Server
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbDSupport kbIIS kbiis500 kbiis500bug kbWin2000PreSP1Fix kbWin2000sp1Fix
	Last Modified: 17-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you send an HTTPS request to a Microsoft Internet Information Services (IIS)
	version 5.0 server that requests a nonexistant IP:Port combination, IIS 5.0 may
	experience an access violation in W3svc.dll.
	
	CAUSE
	=====
	
	IIS 5.0 listens to every Internet Protocol (IP) the computer has associated with
	it. For Secure Socket Layer (SSL) connections, a Web server cannot send back a
	friendly error to the browser, because this error should be encrypted. Each
	encryption requires a certificate that is located by using the IP:PORT look-up
	in a hash-table stored on the server. In this case, the look-up fails, leading
	to an access violation.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows 2000. For
	additional information, click the following article number to view the article
	in the Microsoft Knowledge Base:
	
	  Q260910 How to Obtain the Latest Windows 2000 Service Pack
	
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Internet Information Server
	5.0.
	
	This problem was first corrected in Windows 2000 Service Pack 1.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbIIS kbiis500 kbiis500bug kbWin2000PreSP1Fix kbWin2000sp1Fix 
	Technology        : kbiisSearch kbiis500
	Version           : winnt:5.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
