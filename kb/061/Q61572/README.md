---
layout: page
title: "Q61572: PRB: SYS2070 Issued When Running PWB.EXE for the First Time"
permalink: /kb/061/Q61572/
---

## Q61572: PRB: SYS2070 Issued When Running PWB.EXE for the First Time

{% raw %}

	Article: Q61572
	Product(s): Microsoft Programming Utilities
	Version(s): OS/2:1.0,1.1
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 31-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Programmer's Workbench for OS/2, versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When running the Programmer's WorkBench (PWB) for the first time, the following
	OS/2 system error may be issued:
	
	  Session Title:
	  PWBED.EXE
	
	  SYS2070: The system could not demand load the application's segment. MSHELP
	  HELPSHRINK is in error. For additional detailed information also see message
	  SYS0127
	
	CAUSE
	=====
	
	This problem is usually caused as a result of the Setup program not being able
	to copy its version of MSHELP.DLL over the old version of MSHELP.DLL. If another
	process (most likely a detached session of QH.EXE) was accessing this file
	during the execution of Setup, the Setup program will issue a message similar to
	the following:
	
	  ERROR: Could not create file C:\OS2\DLL\mshelp.dll ERROR: File copy failed:
	  A:\the PWB\mshelp.dll to C:\OS2\dll\mshelp.dll
	
	RESOLUTION
	==========
	
	To solve this problem, take the following steps:
	
	1. Disable QH as a keyboard monitor:
	
	  a. Press ALT+Q (to invoke QH).
	
	  b. Press O (for the Options menu).
	
	  c. Press T (to terminate the monitor).
	
	2. Copy the up-to-date version of MSHELP.DLL from the distribution disk:
	
	  a. Insert the Setup/Compiler 1 disk into drive A.
	
	  b. Change the default drive A.
	
	  c. Run Setup with the /copy option by typing the following:
	
	  " setup /copy" (without the quotation marks)
	
	  d. Press ENTER
	
	  e. Press ENTER again (unless the setup files are in a drive other than A).
	
	  f. At the prompt asking for the name of the file to copy, type MSHELP.DLL and
	     press ENTER.
	
	  g. At the prompt asking for the name of the directory to which to copy this
	     file, type the directory in which the old MSHELP.DLL is located (most
	     likely C:\OS2\DLL).
	
	  h. Setup should then ask for the Programmer's WorkBench/Utilities for OS/2
	     disk to be inserted into the setup drive.
	
	  i. When Setup is finished copying the file, press ENTER at the next prompt.
	
	The PWB should now start up correctly.
	
	NOTE: SQL Server's Setup program also installs its own version of MSHELP.DLL onto
	the system. The SQL Server Setup places its copy of this DLL into a directory
	called \SQL\DLL. If this directory is in the LIBPATH before the directory into
	which the latest MSHELP.DLL was placed, this same problem can arise.
	
	Additional query words: 1.00 1.10 PWBIss
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbPWBSearch kbZNotKeyword3 kbPWB100OS2 kbPWB110OS2
	Version           : OS/2:1.0,1.1
	
	=============================================================================
	

{% endraw %}
