---
layout: page
title: "Q129474: Encarta 94: MindMaze Doesn't Work with 95 ENCARAPI.DLL"
permalink: /kb/129/Q129474/
---

## Q129474: Encarta 94: MindMaze Doesn't Work with 95 ENCARAPI.DLL

{% raw %}

	Article: Q129474
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1994 editions
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 26-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta 1994 The Complete Multimedia Encyclopedia 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you select the Ref button in Encarta 1994's MindMaze game, the system
	freezes. After pressing any key, a general protection (GP) fault in module
	GAMEUTIL occurs.
	
	RESOLUTION
	==========
	
	This can be caused by the Microsoft Encarta for Windows, 1995 edition or
	Microsoft Encarta Encyclopedia for Windows, 1996 edition Encarapi.dll file. Copy
	the 1994 version of this file from the CD to the Encarta 1994 directory on your
	hard drive.
	
	MORE INFORMATION
	================
	
	Both Encarta 1995 and Encarta 96 use a file called Encarapi.dll. This is a
	shared file, used by several programs, so it is copied to the Windows System
	folder. Unfortunately it is not compatible with the Encarta 1994 MindMaze game.
	After copying the 1994 version of Encarapi.dll into the Encarta 1994 working
	directory, Encarta 1994 will always uses the earlier version. Other programs,
	such as Encarta 1995 or Multimedia Works for Windows, will continue to use the
	new version in the System folder.
	
	If Encarta 1995 or 1996 are no longer on the system, delete Encarapi.dll and then
	reinstall Encarta 1994.
	
	If more than one version of Encarta is being used, follow the steps below to
	direct Encarta 1994 to use the appropriate copy of Encarapi.dll.
	
	NOTE: All versions of Encarta need to be installed in separate directories.
	
	Steps For Windows 95
	--------------------
	
	Alter the Encarta 1994 shortcut settings as follows:
	
	1. Click the Start button, point to Settings, and then click Taskbar.
	
	2. Click the Start Menu Programs tab.
	
	3. Click the Advanced button.
	
	4. Double-click the Programs folder, and then double-click the Microsoft
	  Multimedia folder. Note: If your Encarta 1994 shortcut is in a different
	  folder, open that folder instead.
	
	5. With the right mouse button, click the Encarta 1994 shortcut, and then click
	  Properties.
	
	6. Click the Shortcut tab, and note the Start In entry.
	
	7. If Start In refers to your CD-ROM drive (slow installation), change the Start
	  In entry to D:\ENCARTA\ENCARAPI, where drive D is your CD-ROM drive and click
	  OK. Note: if your CD-ROM drive is a different drive letter, replace "D" above
	  with the letter of your CD-ROM drive.
	
	8. If the Start In refers to your hard drive, cancel the Properties sheet,
	  insert the Encarta 1994 CD, and type the following command at the MS-DOS
	  prompt:
	
	  "COPY D:\ENCARTA\ENCARAPI\ENCARAPI.DLL C:\ENC94" (without the quotation
	  marks)
	
	  where D is the letter of your CD-ROM drive, and C:\Enc94 is your Encarta 1994
	  folder. (If your CD-ROM drive is a different drive letter, replace "D" above
	  with the letter of your CD-ROM drive.)
	
	Steps When Using Program Manager
	--------------------------------
	
	1. From Program Manager, select the Encarta 1994 icon by single-clicking it.
	
	2. On the File menu, click Properties.
	
	3. Make note of the Working Directory entry.
	
	4. If Working Directory refers to your CD-ROM drive (slow installation), change
	  the Working Directory to D:\ENCARTA\ENCARAPI, where drive D is your CD-ROM
	  drive and click OK. (If your CD-ROM drive is a different drive letter,
	  replace "D" above with the letter of your CD-ROM drive.)
	
	5. If the Working Directory is on your hard drive, insert the Encarta 1994 CD,
	  and type the following command at the MS-DOS prompt
	
	  "COPY D:\ENCARTA\ENCARAPI\ENCARAPI.DLL C:\ENC94" (without the quotation
	  marks)
	
	  where D is the letter of your CD-ROM drive, and C:\Enc94 is your Encarta 1994
	  folder (directory).
	
	Additional query words: 1994 1995 1996 multi media multimedia multi-media mmtitles
	
	======================================================================
	Keywords          : win31 
	Technology        : kbHomeProdSearch kbEncartaSearch kbEncartaEncycSearch kbEncartaEnCyc1994
	Version           : :1994 editions
	
	=============================================================================
	

{% endraw %}
