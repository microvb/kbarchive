---
layout: page
title: "Q154059: PRB: Commands Fail in Makefile if Directory Over 66 Characters"
permalink: /kb/154/Q154059/
---

## Q154059: PRB: Commands Fail in Makefile if Directory Over 66 Characters

{% raw %}

	Article: Q154059
	Product(s): Microsoft C Compiler
	Version(s): 1.5 1.51 1.52 2.0 4.0 4.1 5.0 6.0
	Operating System(s): 
	Keyword(s): kbVC100 kbVC150 kbVC151 kbVC152 kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC420 kbVC500
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Program Maintenance Utility (NMAKE.EXE), included with:
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5, 1.52, 1.52b, 1.52c 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 2.1, 2.2, 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When running on Windows 95, commands in the makefile echo out to the screen but
	they do not execute. For example, the sample makefile shown below echoes the
	following commands:
	
	  dir *.*
	  md test
	
	but neither command is executed.
	
	CAUSE
	=====
	
	The directory in which you are running nmake is over 66 characters long. When
	running in MS-DOS mode on Windows 95, the MS-DOS limitation of 66 characters,
	including the drive and colon, still applies. Long filenames are counted as 8
	characters when determining the total length of a directory.
	
	RESOLUTION
	==========
	
	If you need to run NMAKE from the Command prompt, the fully qualified directory
	length cannot exceed 66 characters.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Sample Makefile
	---------------
	
	ALL:
	   dir *.*
	   md test
	
	Additional query words: 1.40 1.60.570 1.61.6038 Win95
	
	======================================================================
	Keywords          : kbVC100 kbVC150 kbVC151 kbVC152 kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC420 kbVC500 kbVC600 
	Technology        : kbAudDeveloper kbNMAKESearch
	Version           : 1.5 1.51 1.52 2.0 4.0 4.1 5.0 6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
