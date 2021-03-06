---
layout: page
title: "Q174642: DCA ISCA SDLC Connections Fail On Pentium Pro Systems"
permalink: /kb/174/Q174642/
---

## Q174642: DCA ISCA SDLC Connections Fail On Pentium Pro Systems

{% raw %}

	Article: Q174642
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	A SNA Server using a DCA Intelligent Synchronous Communications Adapter (ISCA)
	SDLC adapter on a system with a Pentium or Pentium Pro processor (133Mhz or
	faster) and using a 56Kbps SDLC line may experience one or more of the following
	problems:
	
	- The SDLC connection stays in a "Pending" state after it is started.
	
	- The SDLC connection goes to an "Active" state and the 3270 LUs become
	  "Available", but it can take a minute or more before all of the sessions are
	  "Available".
	
	- If the SDLC connection is "Active" and the 3270 LUs are "Available", 3270
	  sessions experience very slow response times. Each screen update may take 30
	  seconds or more to complete.
	
	- The SDLC connection drops after it is "Active" causing a message similar to
	  the following to be logged in the Windows NT Application Event Log:
	
	  
	
	  Event ID: 23
	     Source: DCA SDLC Link Service
	     Description: Connection <connection name> using Link Service DCASDLC1 failed.
	                              Qualifier = 0x'0015'
	
	Another symptom of this problem is that enabling SNA Server traces for the DCA
	SDLC Link Service and restarting the SNA Server service may correct the problems
	that were being experienced before enabling the traces. When tracing is enabled,
	the SDLC connection activates and the response times return to the level
	expected for a 56Kbps SDLC line.
	
	
	CAUSE
	=====
	
	The cause of the problem is unknown.
	
	
	RESOLUTION
	==========
	
	The DCA SDLC Link Service has been updated to correct the problems that have
	been reported when using the DCA ISCA SDLC adapter on systems with Pentium or
	Pentium Pro (133MHz or faster) processors. The updated driver can be used with
	SNA Server 2.11 and 3.0.
	
	The following steps may provide an interim solution until the updated driver can
	be obtained and applied to the SNA Server:
	
	1. Start the SNA Server Trace program (snatrace.exe).
	
	2. Select the DCA SDLC Link service (i.e. DcaSdlc1) as the component to trace.
	
	3. Enable Full Internal Tracing, Data Link Control, and Level 2 Messages as the
	  trace options.
	
	4. Click Apply and close the SNA Server Trace Program.
	
	5. Stop and Restart the SNA Server service.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 2.1, 2.11,
	2.11 SP1, 2.11 SP2, 3.0, and 3.0 SP1. This problem was corrected in the latest
	SNA Server version 3.0 Service Pack. For information on obtaining this Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ211 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP1
	Version           : WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1
	
	=============================================================================
	

{% endraw %}
