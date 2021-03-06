---
layout: page
title: "Q58143: MS-DOS PRINT Command and Windows"
permalink: /kb/058/Q58143/
---

## Q58143: MS-DOS PRINT Command and Windows

{% raw %}

	Article: Q58143
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:2.x,3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 2.03, 2.1, 2.11, 3.0, 3.0a, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The MS-DOS Print utility is designed to allow printing from MS-DOS while the
	computer is processing other MS-DOS commands, including running MS-DOS- based
	applications. This printing is done in the background while the MS-DOS
	application runs in the foreground. Thus, Print is a terminate-and-
	stay-resident (TSR) print spooling program.
	
	Like any memory-resident application, Print may cause problems when running with
	Windows (for example, slower printing, or slower or erratic operation in
	general). If you are having problems printing, it may a good idea to remove the
	Print command from the AUTOEXEC.BAT file.
	
	MORE INFORMATION
	================
	
	Print allows you to print multiple files. For example, the following command
	
	  print *.bat
	
	places all BAT files that are in the current subdirectory into the print queue to
	be printed, and begins printing in the background.
	
	Print has the following switches:
	
	  Switch          Explanation
	  ------          -----------
	
	  /D:<printer>    Where <printer> is a device such as LPT1 or COM1
	
	  /Q:<size>       Where <size> is the number of print files that can
	                  be in the queue at once
	
	  /B:<size>       Where <size> is the size of the print buffer
	
	  /S:<slice>      Where <slice> is the number of times per second
	                  PRINT.COM is allowed to take control of the
	                  computer. When PRINT.COM has control of the
	                  computer, execution of other applications is
	                  suspended.
	
	  /M:<max>        Where <max> is the length of each time slice. The
	                  higher the number, the more processor time
	                  PRINT.COM gets.
	
	  /U:<wait>       Where <wait> is the amount of timer ticks PRINT.COM
	                  waits if the printer is busy
	
	  /T              Terminates printing all files in the print queue
	
	  /C              Suspends printing all files in the print queue.
	
	  /P              Turns on print mode.
	
	Some switches can only be used during the initial loading of Print; see your
	MS-DOS manual for more information. The switches can be combined on a single
	line. For example, the command
	
	  print autoexec.bat /c config.sys /p
	
	removes AUTOEXEC.BAT from the print queue and adds CONFIG.SYS to the print queue.
	If the command Print is entered with no parameters or filenames, the contents of
	the print queue are displayed.
	
	Additional query words: PRINT.EXE memory 3.1 3.10 3.11 excel winword winprint msdos
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin203 kbWin210 kbWin211 kbWin300 kbWin300a kbWin310 kbWin311
	Version           : WINDOWS:2.x,3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
