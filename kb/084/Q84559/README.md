---
layout: page
title: "Q84559: HP DeskJet Scalable Font Driver Setup and TrueType"
permalink: /kb/084/Q84559/
---

## Q84559: HP DeskJet Scalable Font Driver Setup and TrueType

{% raw %}

	Article: Q84559
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Hewlett-Packard (HP) provides a scalable printer driver for use with the DeskJet
	500 and DeskJet 500C printers and Microsoft Windows version 3.0. This driver is
	not updated during the upgrade from Microsoft Windows operating system version
	3.0 to version 3.1.
	
	This HP printer driver is not compatible with the TrueType font technology that
	is included with Microsoft Windows operating system version 3.1. However, the HP
	driver does include the scalable fonts CG Times, Courier, and Univers. These
	fonts are not available if the Microsoft supplied driver that is included with
	Microsoft Windows version 3.1 is used.
	
	MORE INFORMATION
	================
	
	When upgrading from the Microsoft Windows operating system version 3.0 to
	version 3.1, the HP DeskJet 500 scalable font printer driver is not updated. The
	earlier driver is left installed because the Microsoft provided DeskJet 500
	printer driver does not directly support some of the HP scalable soft fonts
	included with the earlier printer driver.
	
	The DeskJet printer driver included with Windows 3.1 supports TrueType fonts,
	unlike the HP version. The new driver supplied with Microsoft Windows 3.1 has
	compatible fonts to the HP scalable fonts.
	
	TrueType fonts will not be available to Windows applications if the HP supplied
	scalable driver is used.
	
	The Microsoft supplied driver includes the following TrueType fonts that are
	compatible with the HP scalable fonts.
	
	Hewlett-Packard Scalable Font   Microsoft TrueType Scalable Font
	-----------------------------   --------------------------------
	
	CG Times                        Times New Roman
	Courier                         Courier New
	Univers                         Arial
	
	Do the following to add the new Microsoft Windows 3.1 DeskJet 500 printer
	driver:
	
	1. Run Control Panel.
	
	2. Choose the Printers icon.
	
	3. Choose Add.
	
	4. Choose the appropriate driver (DeskJet 500, or DeskJet 500C).
	
	5. Choose Install.
	
	After installing the new DeskJet 500 printer driver, the HP Scalable driver may
	be left installed in conjunction with the current driver, or may be removed.
	
	Most Windows-based applications allow switching between printer drivers from the
	File menu. Often this selection is available as Print Setup or Printer Setup.
	This feature allows you to switch between the earlier HP scalable driver and the
	later Microsoft driver that supports TrueType. This feature will only be
	available if both drivers are installed.
	
	While the HP scalable driver may be left in tact for compatibility reasons, the
	newer TrueType driver provides compatible fonts and should be suited for most
	applications. For most users, the HP scalable driver can be removed.
	
	Notes
	-----
	
	Saved documents that include CG Times, Courier, and Univers fonts will be
	automatically updated to use the TrueType counterparts when the Microsoft 3.1
	driver is installed.
	
	The Microsoft Windows 3.1 printer drivers for the HP DeskJet family can be
	identified by the following descriptions:
	
	  HP DeskJet
	  HP DeskJet Plus
	  HP DeskJet 500
	  HP DeskJet 500C
	
	The HP-supplied scalable printer drivers for Microsoft Windows 3.0 can be
	identified by the following descriptions:
	
	  HP DeskJet 500 Scalable Driver
	  HP DeskJet Series V2.00
	  HP DeskJet Series V2.1
	
	Additional query words: 3.10 3.11 older newer true type tt ttf soft font
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310 kbWin311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
