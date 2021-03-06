---
layout: page
title: "Q129572: How to Find Out Which FoxPro Version Created an .SCX File"
permalink: /kb/129/Q129572/
---

## Q129572: How to Find Out Which FoxPro Version Created an .SCX File

{% raw %}

	Article: Q129572
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c,2.6a; MS-DOS:2.0,2.5,2.5a,2.5b,2.6,2.6a; UNIX:2.6; WINDOWS:2.5,2.5a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c, 2.6a 
	- Microsoft FoxPro for UNIX, version 2.6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides a way to verify the version of FoxPro that was used to
	create a Screen or a Form (.SCX file).
	
	MORE INFORMATION
	================
	
	Files with an .SCX extension were introduced in FoxPro version 2.0 for MS- DOS.
	They are FoxPro tables that record information about screens (versions 2.x) or
	forms (Visual FoxPro version 3.0).
	
	Screens created in FoxPro version 2.x do not contain information about the
	version of FoxPro used to create them. However, because the structure of an .SCX
	file is different depending on the version of FoxPro, you can use the FCOUNT()
	function to count the number of fields in an .SCX file and derive the FoxPro
	version used to create the file. The following lists the number of fields that
	an SCX contains for each version of FoxPro. This assumes that no structural
	change was made to the SCX:
	
	FoxPro Versions                 Number of Fields
	------------------------------------------------
	FoxPro version 2.0              57 fields
	FoxPro versions 2.5x and 2.6x   79 fields
	Visual FoxPro version 3.0       23 fields
	
	Visual FoxPro forms now include version information. The Reserved1 field of a
	Visual FoxPro form contains the version tag VERSION= 3.00. This information is
	recorded in the record of the form where the PLATFORM field is equal to COMMENTS
	(the first record in the form).
	
	Additional query words: VFoxWin 3.00 2.00 2.50 2.50a 2.50b 2.50c 2.60 2.60a
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro260aMac kbFoxPro250cMac kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260UNIX kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbFoxPro260a kbVFP300
	Version           : MACINTOSH:2.5b,2.5c,2.6a; MS-DOS:2.0,2.5,2.5a,2.5b,2.6,2.6a; UNIX:2.6; WINDOWS:2.5,2.5a,2.5b,2.6,2.6a,3.0
	
	=============================================================================
	

{% endraw %}
