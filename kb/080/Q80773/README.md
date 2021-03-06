---
layout: page
title: "Q80773: File Manager Window Not Visible"
permalink: /kb/080/Q80773/
---

## Q80773: File Manager Window Not Visible

{% raw %}

	Article: Q80773
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 05-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You start the Windows version 3.1 File Manager, but it doesn't appear on the
	screen. Selecting File Manager from your Task Lisk has no effect.
	
	CAUSE
	=====
	
	There may be a problem with the settings in the WINFILE.INI file.
	
	WORKAROUND
	==========
	
	To make File Manager visible, do the following:
	
	1. Minimize all applications currently running, including Program Manager.
	
	2. Start Task Manager by double-clicking on the wallpaper, or using CTRL+ESC.
	
	3. Select File Manager from the Task List, and select Tile. File Manager will
	  now be visible.
	
	4. From the Options menu in File Manager, make sure Save Settings On Exit is
	  chosen. This will prevent the problem from occurring again.
	
	MORE INFORMATION
	================
	
	This problem is caused by an invalid entry in WINFILE.INI. WINFILE.INI can be
	found in the WINDOWS directory and can be edited with Notepad. Near the top of
	the file there will be a Window= line in the [Settings] section. For example:
	
	     [Settings]
	     Window=0,0,800,600, , ,1
	
	     First Number: X offset of upper left hand corner
	     Second Number: Y offset of upper left hand corner
	     Third Number: Width of window
	     Fourth Number: Height of window
	
	If the first number is negative, and its absolute value is greater than the third
	number, or if the second number is negative, and its absolute value is greater
	than the fourth number, the File Manager window will be off-screen and not
	visible. This could happen if a virtual desktop utility is being used like the
	Inner Media's Wide Angle, or shareware program BIGDESK.
	
	EXAMPLE: If the following line is in the WINFILE.INI
	
	       Window=-500,0,480,600, , ,1
	
	File Manager starts up without an error, but is not visible. File Manager shows
	up in the Task List, but selecting it does not make it appear.
	
	NOTE: This problem does not occur in the Windows 3.0 File Manager, as it does not
	use or recognize the "Window=" setting.
	
	KBCategory: kbtool
	KBSubcategory: win31
	
	Additional query words: 3.10 3.11 invisible disappear win31
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
