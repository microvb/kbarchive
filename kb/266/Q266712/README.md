---
layout: page
title: "Q266712: SMS: Security Based on Global Groups Fails in Win 2000 Domains"
permalink: /kb/266/Q266712/
---

## Q266712: SMS: Security Based on Global Groups Fails in Win 2000 Domains

{% raw %}

	Article: Q266712
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbsms200 kbsms120 kbsms120bug kbsms200preSP4fix
	Last Modified: 09-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After granting Windows 2000 global groups permission within the Systems
	Management Server Administrator console, users of these groups may not inherit
	class or instance rights that are defined for the group. Users will be able to
	connect, and see the various nodes (such as collections), but will not be able
	to view any objects (such as All Systems).
	
	At the same time, users who are explicitly defined within Systems Management
	Server security, who do not rely on groups for access, inherit permissions as
	expected.
	
	NOTE: This may occur in either Windows 2000 Mixed, or Native Mode domains.
	
	NOTE: No errors are being generated, not even in the SMSProv log.
	
	CAUSE
	=====
	
	The problem occurs when the SMS Provider uses an anonymous connection to
	retrieve the logged user's group membership from the PDC emulator.
	
	There are currently three known scenarios in which this problem occurs:
	
	- The Everyone group is not a member of the Pre-Windows 2000 Compatible Access
	  group. This could be caused if the "Permissions compatible with only Windows
	  2000 Servers" is selected during the Dcpromo process described in the
	  following article in the Microsoft Knowledge Base:
	
	  Q257988 Description of Dcpromo Permissions Choices
	
	- The Default Domain Policy under Computer Configuration|Windows Settings|Local
	  Policies|Security Options|Additional restrictions for anonymous connections
	  is configured to "No access without explicit anonymous permissions".
	
	- The Pre-Windows 2000 Compatible Access group does not have the requisite
	  directory access permissions.
	
	WORKAROUND
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, please see the following article
	in the Microsoft Knowledge Base:
	
	  Q288239 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	MORE INFORMATION
	================
	
	The Systems Management Server Provider makes an anonymous connection to a domain
	controller in the domain to determine a users group membership. By default,
	Windows 2000 permits all authenticated users and members of the Pre-Windows 2000
	Compatible Access group to view group membership. Because the Everyone group is
	a member of the Pre-Windows 2000 Compatible Access group by default, anonymous
	access can be used to retrieve group membership.
	
	
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms120 kbsms120bug kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
