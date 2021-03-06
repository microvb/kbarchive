---
layout: page
title: "Q164633: SNA Server Issues with DBCS 3270 Printing."
permalink: /kb/164/Q164633/
---

## Q164633: SNA Server Issues with DBCS 3270 Printing.

{% raw %}

	Article: Q164633
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbnetworkkbbuglist
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 3.0 
	-------------------------------------------------------------------------------
	
	This article applies to DBCS (double byte character set) code pages only.
	DBCS code pages include:
	
	  
	
	  290 (Japanese (Katakana))
	  930 (Japanese (Extend Katakana))
	  931 (Japanese (English-lower))
	  933 (Korean)
	  935 (Chinese (PRC))
	  937 (Chinese (Taiwan))
	  939 (Japanese (Extend English))
	
	1. DBCS Characters Incorrect and Multiple Sessions Fail.
	
	
	2. Multiple Fixes for DBCS SCS Printing.
	
	
	SYMPTOMS
	========
	
	1. DBCS Characters Incorrect and Multiple Sessions Fail.
	
	  SYMPTOMS
	  DBCS characters are not printing correctly in both LU1 and LU3 data streams
	  and a Dr. Watson log is generated when multiple print sessions are
	  activated.
	
	   - DBCS characters are not printed correctly in LU3. ShiftOut(0x0E) and
	     ShiftIn(0x0F) are not handled correctly. These codes mark the beginning
	     and end of DBCS data. Since these codes are not recognized, DBCS
	     characters between SO(0x0E) and SI(0x0F) are printed as two SBCS
	     characters.
	
	   - Dr.Watson appears on activations of multiple printer sessions. If only one
	     of DBCS code page sessions is activated, the problem does not happen.
	     However, if two or more DBCS code page sessions are activated, a Dr.
	     Watson log results.
	
	   - DBCS characters are not printed correctly in LU1. If DBCS data is sent
	     containing one or more control codes (NL, CR, LF, BS, and so forth), then
	     the DBCS data is printed incorrectly.
	
	  RESOLUTION
	  A fix has been made to correct these problems.
	
	
	2. Multiple Fixes for DBCS SCS Printing.
	
	  SYMPTOMS
	  There were multiple problems found in SCS DBCS printing. The following
	  problems were fixed:
	
	  a. When the margin is set in the Printer Session Properties Printing Tab, the
	     resulting position of the grid line is incorrect.
	
	  b. The grid line is incorrect on some control codes.
	
	  c. The automatic LF (Line Feed) is not performed. This automatic LF is a a
	     special function for the grid handling (for DBCS code page only).
	
	  d. "-R" is not returned on incomplete Set Attribute (SA) data streams.
	
	  Complete SA format:
	  DBCS: 0x'2843xx'
	  Grid: 0x'28C2xx'
	
	  Incomplete SA:
	  The data chain ends with 0x'28' or 0x'2843' or 0x'28C2'.
	
	  e. NewLine (NL) is not performed after maximum presentation position (MPP).
	
	  f. NUL control code is printed.
	
	  RESOLUTION
	
	  a. The printing position of the grid was adjusted for the margin.
	
	  b. The grid handling after some control codes(including NL, CR, LF, BS) was
	     modified.
	
	  c. Corrected the automatic LF process for the grid.
	
	  d. The -R is now set at the end of the data chain, for the incomplete SA
	     format.
	
	  e. The NL process was corrected for MPP.
	
	  f. The NUL character was translated to space.
	
	  An update to SNA Server 3.0 is available to correct this problem.
	
	
	STATUS
	======
	
	Microsoft has confirmed these to be problems in SNA Server 3.0. This problem was
	corrected in the latest Microsoft SNA Server 3.0 U.S. Service Pack. For
	information on obtaining the service pack, query on the following word in the
	Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork kbbuglist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
