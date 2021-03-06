---
layout: page
title: "Q242944: XCON: MTA Generates a Large Number of Event ID 2125s"
permalink: /kb/242/Q242944/
---

## Q242944: XCON: MTA Generates a Large Number of Event ID 2125s

{% raw %}

	Article: Q242944
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The message transfer agent (MTA) may generate a large number of event ID 2125s
	that are similar to the following, even though mail flow is not affected:
	
	  Source: MSExchange MTA
	  Type: Warning
	  Category: Resource
	  Event ID: 2125
	
	  Description: Statistics for DBI call (DB Server) : file writes DISP:FANOUT,
	  reads 11, cache hits 124, misses %5. Attribute %6, value number %7, Object
	  ID: %8 (00000000 => N/A). Caller %12 [%9 %10 %11] (8)
	
	CAUSE
	=====
	
	This issue can occur if the MTA does not write to the .cfg files correctly when
	the MTA processes new messages. This issue occurs most often when one of the
	Info*.cfg files is an incorrect version or is corrupted.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following procedures, as applicable:
	
	- If the object ID is referenced in the event ID description as shown in the
	  following example
	
	  Event ID: 2125
	  Type: Information
	  Category: Field Engineering
	  Description: Statistics for DBI call (19): file writes 0, read 0, cache hits
	  1, misses 1. Attribute 84, value number 3, Object ID: 0600003A (00000000
	  => N/A). Caller 117 (DB Server DISP:ROUTER 11)(8)
	
	  perform the following steps:
	
	  1. Note the object ID that is included in event 2125 (0600003A in this
	     example).
	
	  2. Remove the .dat file that has a file name that is composed of the last six
	     digits of the object ID from the Mtadata folder (the Db00003a.dat file in
	     this example).
	
	  3. Run the following command:
	
	  <exchsrvr>\BIN\mtacheck
	
	  4. Restart the MTA.
	
	  5. Reapply the relevant Exchange Server service packs and any post-service
	     pack fixes.
	
	- If no object ID is included in the event ID description, apply the latest
	  Exchange Server service pack, so that all of the files are the correct
	  version.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
