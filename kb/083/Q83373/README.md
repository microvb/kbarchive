---
layout: page
title: "Q83373: Installation and Usage of MicroSpeed PC-Trackball for Windows"
permalink: /kb/083/Q83373/
---

## Q83373: Installation and Usage of MicroSpeed PC-Trackball for Windows

{% raw %}

	Article: Q83373
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains how to install MicroSpeed PC-Trackball pointing devices
	for use with Windows 3.0.
	
	These devices can be operated properly when the "Microsoft or IBM PS/2 mouse
	driver" option is selected while setting up Windows.
	
	MORE INFORMATION
	================
	
	The MicroSpeed PC-Trackball has four interfaces:
	
	- Serial
	
	- PS/2 mouse port
	
	- Microsoft InPort mouse port
	
	- Bus card
	
	Of the four interfaces, the bus card interface is the only one not currently
	recommended for use with Windows 3.0.
	
	Installing the PC-Trackball with Bus Card Interface
	---------------------------------------------------
	
	If you use the MicroSpeed PC-Trackball with the bus card interface, you cannot
	use Windows 3.0 standard or 386 enhanced mode. If you start Windows 3.0 in
	standard or 386 enhanced mode with this device, the logo screen will briefly
	appear and then Windows will return to the MS-DOS command prompt. Windows runs
	correctly in real mode with this bus card.
	
	To work around this problem, connect the PC-Trackball to one of the serial ports
	and select "Microsoft or IBM PS/2 mouse driver" as the pointing device during
	Windows setup.
	
	MicroSpeed is aware of this problem and is working on a new driver.
	
	Installing the PC-Trackball Serial, InPort, and PS/2 Mouse Port
	---------------------------------------------------------------
	
	1. Connect the PC-Trackball to the proper port. Do not install any MicroSpeed
	  mouse drivers. If these drivers have been installed, edit the CONFIG.SYS and
	  AUTOEXEC.BAT files. Look for the names PPR.SYS, PPR.COM, and POINTER.BAT and
	  remove them.
	
	2. If the PC-Trackball is replacing a Microsoft or PS/2 mouse, install for a
	  Microsoft or PS/2 mouse.
	
	3. If Windows 3.0 is not installed, run the Windows 3.0 Setup program and follow
	  the instructions for installing Windows for use with a Microsoft or PS/2
	  mouse.
	
	4. If you are planning to use the PC-Trackball with non-Windows applications,
	  install the Microsoft mouse driver version 7.04 or later in either the
	  CONFIG.SYS or AUTOEXEC.BAT file. The Windows 3.0 Setup program may do this.
	  If it does not, use the Windows EXPAND.EXE utility located on Disk 2 of the
	  Microsoft Windows 3.0 disk to decompress the MOUSE.SY$ file into the root
	  directory as MOUSE.SYS and then edit the CONFIG.SYS file and add the
	  following line:
	
	  device=c:\mouse.sys /y
	
	Note: MicroSpeed's KEYMAP.COM program should not be used when running Windows
	3.0.
	
	For additional information about MicroSpeed pointing devices, call MicroSpeed
	Technical Support at (510) 490-1403.
	
	The PC-Trackball is manufactured by a vendor independent of Microsoft; we make no
	warranty, implied or otherwise, regarding this product's performance or
	reliability.
	
	Additional query words: 3.00 3.00a
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a
	Version           : WINDOWS:3.0,3.0a
	
	=============================================================================
	

{% endraw %}
