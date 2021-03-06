---
layout: page
title: "Q315494: No NMVT for Printer DDDLUs After Connection Outage"
permalink: /kb/315/Q315494/
---

## Q315494: No NMVT for Printer DDDLUs After Connection Outage

{% raw %}

	Article: Q315494
	Product(s): Microsoft SNA Server
	Version(s): 4.0 SP4
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 09-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 4.0 SP4 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After a connection outage, SNA Server and Host Integration Server 2000 may not
	re-activate any printer Dynamically Defined Dependent Logical Units (DDDLUs).
	Display DDDLUs and LUA DDDLUs do not exhibit this same problem.
	
	CAUSE
	=====
	
	After the connection outage, the SNA Server service does not send a Network
	Management Vector Transport (NMVT) command for the printer DDDLUs to solicit an
	Activate Logical Unit (ACTLU) command from the remote computer.
	
	RESOLUTION
	==========
	
	SNA Server 4.0
	--------------
	
	As of May 2002, a fix is available for this problem in SNA Server 4.0 is not
	available.
	
	
	Host Integration Server 2000
	----------------------------
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Host Integration Server 2000 that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date       Time   File name
	  ------------------------------
	  12-Jan-02  14:45  Snaservr.exe
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	STATUS
	======
	
	SNA Server 4.0
	--------------
	
	Microsoft has confirmed this to be a problem in SNA Server version 4.0 Service
	Pack 4.
	
	Host Integration Server 2000
	----------------------------
	
	Microsoft has confirmed this to be a problem in Host Integration Server 2000.
	
	MORE INFORMATION
	================
	
	For additional information about SNA Server, Host Integration Server 2000, and
	DDDLUs, click the article numbers below to view the articles in the Microsoft
	Knowledge Base:
	
	  Q161492 INFO: LU Session Activation Using Dynamically Defined Dependent LUs
	
	  Q164592 Dynamically Defined Dependent LU Support for LUA LUs
	
	  Q276453 Dynamically Defined Dependent LU Support for Printer LUs
	
	  Q276481 SNA Server Does Not Send LU Name in NMVT for DDDLU
	
	  Q276196 NMVT Power Off Now Supported in SNA Server
	
	Additional query words: his
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400SP4
	Version           : :4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
