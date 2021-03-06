---
layout: page
title: "Q164075: SNA 2.11 Service Pack 2 Readme.txt File"
permalink: /kb/164/Q164075/
---

## Q164075: SNA 2.11 Service Pack 2 Readme.txt File

{% raw %}

	Article: Q164075
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the Readme.txt file included
	in SNA Server Service Pack 2.
	
	MORE INFORMATION
	================
	
	Microsoft SNA Server Version 2.11 Service Pack 2
	Release Notes
	
	February 1997
	
	(c) Copyright Microsoft Corporation, 1997
	
	These materials are provided "as-is," for informational purposes
	only.
	
	Neither Microsoft nor its suppliers makes any warranty, express
	or implied with respect to the content of these materials or the
	accuracy of any information contained herein, including, without
	limitation, the implied warranties of merchantability or fitness
	for a particular purpose. Because some states/jurisdictions do
	not allow exclusions of implied warranties, the above limitation
	may not apply to you.
	
	Neither Microsoft nor its suppliers shall have any liability for
	any damages whatsoever including consequential incidental, direct,
	indirect, special, and loss profits. Because some states/ 
	jurisdictions do not allow exclusions of implied warranties, the
	above limitation may not apply to you. In any event, Microsoft's
	and its suppliers' entire liability in any manner arising out of
	these materials, whether by tort, contract, or otherwise shall
	not exceed the suggested retail price of these materials.
	
	======================================================================
	
	Ordering the SNA Server 2.11 Service Pack 2 CD
	-----------------------------------------------
	
	Microsoft SNA Server 2.11 U.S. Service Pack 2 (SP2) is available
	in CD media format by ordering from Microsoft at (800) 936-3500,
	using the following part number:
	
	 Disk Set #: 211-075-100
	
	2.11 SP2 includes SNA Server 2.11 Service Pack 1 (SP1) as well as
	bug fixes implemented since 2.11 SP1. In addition, the 2.11 SP2
	CD includes updated documentation, collateral, and SDK (software
	development kit files). 2.11 SP2 includes updated SNA Server and
	client software for I386 (Intel) and DEC Alpha platforms.
	
	NOTE: Support for MIPS and Power PC platforms has been discontinued
	and is not included in 2.11 SP2. If you are running SNA Server on
	a MIPS or Power PC system and are experiencing a problem which has
	been fixed in 2.11 SP2, please contact Microsoft support for an
	update.
	
	Downloading SNA Server 2.11 Service Pack 2
	------------------------------------------
	
	Self-extracting executable files containing updated 2.11 SP2 SNA
	Server and client files can be downloaded electronically from
	www.microsoft.com. The following files comprise the updated
	SNA Server and client files for 2.11 SP2:
	
	 211SP2IS.EXE - 2.11 SP2 Server Update (Intel) (NOTE 1)
	 211SP2AS.EXE - 2.11 SP2 Server Update (Alpha) (NOTE 1)
	 211SP2IC.EXE - 2.11 SP2 Windows NT Client Update (Intel)
	 211SP2AC.EXE - 2.11 SP2 Windows NT Client Update (Alpha)
	 211SP2CL.EXE - 2.11 SP2 Win 3.x, MS-DOS, OS/2 Client Update
	 211SP295.EXE - 2.11 SP2 Windows 95 Client Update
	 SNAWIN95.EXE - 2.11 SP2 Windows 95 Client - full client
	 211SP2TN.EXE - 2.11 SP2 TN3270 Server Update (Intel & Alpha)
	 211SP2EI.EXE - 2.11 SP2 Eicon WAN Services Drivers (Intel) (NOTE 1)
	 211SP2EA.EXE - 2.11 SP2 Eicon WAN Services Drivers (Alpha) (NOTE 1)
	
	For information about changes implemented in 2.11 SP1 and SP2,
	see the SNA21SP2.HLP file included in 211SP2IS.EXE and
	211SP2AS.EXE.  SNA21SP2.HLP also contains licensing information,
	the 2.11 SP1 contents, and 2.11 SP2 contents.  The contents for SP1
	and SP2 comprise articles describing the symptoms, causes, and
	solutions to known problems.  The updated documentation, collateral
	and SDK files are only available on the 2.11 SP2 CD and are not
	available for electronic download.
	
	NOTE 1: The electronic download versions of SNA Server SP2 do not
	include updated driver files for Eicon WAN Services.  These must be
	downloaded separately (211SP2EI.EXE or 211SP2EA.EXE, as appropriate).
	Once the 211SP2IS.EXE or 211SP2AS.EXE file has been extracted, the
	Eicon update should be copied to the <server>\system\hwsetup\eicon
	directory and extracted using "211sp2ei.exe -d".  This will restore
	the Eicon driver files to the same location as included on the
	SNA Server 2.11 SP2 CD.
	
	Instructions for Decompressing Files
	------------------------------------
	
	All of the above files are compressed in self-extracting
	archive format, containing SNA Server 2.11 SP2.  To extract
	each file, copy the file to a separate empty directory on your
	hard drive and run the file using the "-d" option.  For
	example:
	
	   211SP2IS.EXE -d <PATH>
	
	Where <PATH> is the destination directory for the service
	pack. If you wish to extract the service pack to the current
	directory, leave <PATH> blank.
	
	After the service pack file has been decompressed, run the
	UPDATE.EXE program to install the updated SNA Server 2.11
	server or client files, as appropriate.
	
	NOTE: The UPDATE program will automatically stop any SNA
	Server services which may be running.
	
	Installing the Service Pack Files
	---------------------------------
	Both the SNA Server and SNA client files have been updated
	in 2.11 SP2. Updates may be applied in any order -- to the
	server and/or to the clients. It is recommended that all
	systems running SNA Server 2.11 (that is, SNA Servers and
	client computers) are updated to SP2. It may not be
	necessary to update the client computers to SP2 unless you
	are experiencing a client problem that has been fixed in SP2.
	
	** TO BE APPLIED TO SNA SERVER 2.11 or 2.11 SP1 ONLY!! **
	
	Additional query words: prodsna
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ211 kbSNAServ211SP1
	Version           : WINDOWS:2.11,2.11 SP1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
