---
layout: page
title: "Q150478: Julia Child: Manual Installation For Windows 95"
permalink: /kb/150/Q150478/
---

## Q150478: Julia Child: Manual Installation For Windows 95

{% raw %}

	Article: Q150478
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:1.0,95
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Julia Child: Home Cooking with Master Chefs for Windows, version 1.0 
	- the operating system: Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides instructions to manually install Julia Child on computers
	running Microsoft Windows 95.
	
	MORE INFORMATION
	================
	
	These instructions assume:
	
	- Your hard drive is drive C:
	
	- Your Windows folder is C:\Windows
	
	- Your CD-ROM drive is drive D
	
	- Your Destination folder is C:\Msjulia
	
	If your hard disk drive, destination folder (directory), Windows folder, or
	CD-ROM drive letters are different, replace the drive letters and folder names
	throughout this article with the drive letters and folder names on your
	computer.
	
	NOTE: The following instructions discuss copying, editing, and modifying folders
	and files. For more information about how to accomplish these tasks in Windows,
	see your Windows printed documentation or online Help.
	
	1. Create a folder named Msjulia on your C: drive. For example, type the
	  following at the MS-DOS command prompt and press ENTER:
	
	  "md c:\msjulia" (without the quotation marks)
	
	2. Copy the following files to the Msjulia folder:
	
	  D:\Msjulia\Msjulia.exe
	  D:\Msjulia\Msjuliaa.dll
	  D:\Msjulia\Msjuliab.dll
	  D:\Readme.wri
	  D:\Aamsstp\Msstp\Pidholdr.dll
	  D:\Aamsstp\Misc\Deco.dll
	
	  For example, type the following at an MS-DOS command prompt, pressing ENTER at
	  the end of each line:
	
	  "copy d:\msjulia\msjulia.exe c:\msjulia" (without the quotation marks)
	
	3. Copy the following files to C:\Windows\System:
	
	  D:\AAMSSTP\MV13\mvbk13w.DLL
	  D:\AAMSSTP\MV13\mvcl13w.DLL
	  D:\AAMSSTP\MV13\mvfs13w.DLL
	  D:\AAMSSTP\MV13\mvmg13w.DLL
	  D:\AAMSSTP\MV13\mvsr13w.DLL
	  D:\AAMSSTP\MV13\mvtl13w.DLL
	
	4. Copy the following files from D:\Aamsstp\Fonts to C:\Windows\Fonts:
	
	  Arial.ttf
	  Arialbd.ttf
	  Msref2.ttf
	  Times.ttf
	  Timesbd.ttf
	  Timesbi.ttf
	  Timesi.ttf
	
	5. Delete the following file, if it exists:
	
	  C:\Windows\System\Dcisvga.drv
	
	6. Use a text editor, such as Microsoft Notepad, to make the following changes
	  to the Msjulia.ini file, which is located in the Windows folder.
	
	  NOTE: If the Msjulia.ini file does not already exist, create one in the
	  Windows folder with these same entries:
	
	        [Options]
	        BookDirectory=D:\msjulia\ 
	        CodeDirectory=C:\Msjulia\ 
	        DataDirectory=C:\Msjulia\ 
	        MediaDirectory=D:\msjulia\video\ 
	
	7. Make sure Windows 95 Audio and Video Compression is installed:
	  a. Click Start, point to Settings, and click Control Panel
	
	  b. Double-click Add/Remove Programs.
	
	  c. On the Windows Setup tab, double-click Multimedia.
	
	  d. If either Audio Compression or Video Compression is not selected, click
	     the box to put a check mark in it.
	
	  e. Click OK.
	
	  f. Click OK to close Add/Remove Programs. Follow the screen instructions, if
	     prompted.
	
	8. Add the program icons or Start Menu shortcuts. As a guide, use the steps
	  listed in the appropriate section below.
	
	Creating Start Menu Shortcuts
	-----------------------------
	
	Add Julia Child to the Start Menu by following these instructions:
	
	1. Click the Start button, point to Settings, and then click Taskbar.
	
	2. On the Start Menu Programs tab, click Add.
	
	3. Type the following in the Command Line box, and then click Next:
	
	  "c:\msjulia\msjulia.exe d:\msjulia\msjulia.m13" (without the quotation marks)
	
	4. In the Select Program Folder dialog box, click the Microsoft Multimedia
	  folder, and then click Next.
	
	  If Microsoft Multimedia is not listed, do the following to create it:
	  a. On the File Menu, click New Folder
	
	  b. Type the following, and then click Next:
	
	  "Microsoft Multimedia" (without the quotation marks)
	
	5. In the Select A Title For The Program dialog box, type the following, and
	  then click Finish:
	
	  "Julia Child" (without the quotation marks)
	
	6. Repeat steps 3-6 to create the following shortcut:
	
	     Command Line:        c:\msjulia\readme.wri
	     Select A Title:      Julia Child Read Me
	
	Creating Program Manager Icons
	------------------------------
	
	If you are using Program Manager, use the following instructions to create the
	program icons:
	
	1. Open the Microsoft Multimedia group. If this group does not already exist,
	  create it as follows:
	  a. On the File menu, click New.
	
	  b. Click Program Group, and then click OK.
	
	  c. In the Description box, type the following, and then click OK:
	
	  "Microsoft Multimedia" (without the quotation marks)
	
	2. On the File menu, click New.
	
	3. Click Program Item, and then click OK.
	
	4. Type the following Description and Command Line information, and then click
	  OK:
	
	     Description:       Julia Child
	     Command Line:      c:\msjulia\msjulia.exe d:\msjulia\msjulia.m13
	
	5. Repeat steps 2-4 for the following item:
	
	     Description:       Julia Child Read Me
	     Command Line:      C:\msjulia\readme.wri
	
	Additional query words: multi media multimedia multi-media mmtitles kbmm
	
	======================================================================
	Keywords          :  
	Technology        : kbOSWin95 kbOSWinSearch kbHomeProdSearch kbZNotKeyword kbJuliaChild
	Version           : WINDOWS:1.0,95
	
	=============================================================================
	

{% endraw %}
