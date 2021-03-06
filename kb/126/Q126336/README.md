---
layout: page
title: "Q126336: Works 3.0: Problems Printing to HP DeskJet Drivers 4.x and 5.x"
permalink: /kb/126/Q126336/
---

## Q126336: Works 3.0: Problems Printing to HP DeskJet Drivers 4.x and 5.x

{% raw %}

	Article: Q126336
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0,1994 edition,1995 edition,3.0,3.1,3.11
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 09-NOV-2001
	
	WINDOWS
	kb3rdparty kbprint kbmm kbfaq
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Bookshelf for Windows versions 1994 edition, 1995 edition 
	- Microsoft Bookshelf 1996-97 for Windows 
	- Microsoft Encarta for Windows versions 1994 edition, 1995 edition 
	- Microsoft Encarta 97 Encyclopedia for Windows 
	- Microsoft Encarta Encyclopedia 97 Deluxe for Windows 
	- Microsoft Money, version 3.0 
	- Microsoft Musical Instruments for Windows, version 1.0 
	- Microsoft Works, version 3.0 
	- Microsoft Windows versions 3.1, 3.11 
	- Microsoft Windows for Workgroups 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you print to a Hewlett-Packard (HP) DeskJet printer, you may encounter the
	following problems:
	
	- missing characters or parts of images.
	- graphic images print as smeared colors or a black square.
	
	You also may receive the following error message
	
	  <application> caused a general protection fault in module Deskjetc.drv
	  at <address>
	
	where <application> is the program you are using and <address> is the
	path
	
	
	RESOLUTION
	==========
	
	Try one of the following resolutions.
	
	Resolution 1
	------------
	
	Obtain Hewlett-Packard (HP) DeskJet printer driver version 6.1D from
	Hewlett-Packard.
	
	Resolution 2
	------------
	
	Do not use the DeskJet Automatic printing mode. Other settings, such as Color
	Graphics or Black Text give more consistent results.
	
	To change the DeskJet printing mode, do the following:
	
	1. Exit and restart Windows.
	
	2. In the application from which you are printing, choose Print or Printer
	  Setup.
	
	3. Select the DeskJet printer. Choose Setup.
	
	4. Select Color Graphics (recommended for color printers) or Grayscale (for
	  black-and-white printers). The Black Text setting also may work for some
	  problems.
	
	5. Choose OK. Print your document.
	
	MORE INFORMATION
	================
	
	When you print to HP DeskJet (C) printers, you may get poor results when
	printing text or graphics.
	
	This problem can occur with HP DeskJet driver versions 4.0, 4.1, and 5.0.
	Previous DeskJet drivers, such as version 3.0 and 3.1, do not have this problem.
	Affected printers include: the DeskJet 500, 500c, 550, 550c, 560c, 540, or 520
	printers.
	
	Some applications that print DIB graphic images, such as Microsoft Musical
	Instruments, cannot print using the DeskJet driver version 5.0. To print these
	applications, try using an earlier driver version such as 4.0.
	
	If the method in the Resolution section of this article does not fix the general
	protection fault error, the problem could be related to your video driver.
	Install the standard VGA driver included with Windows and test your printer. If
	the GP fault continues, contact Hewlett-Packard for an updated printer driver.
	
	The products discussed here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these products' performance
	or reliability.
	
	
	Additional query words: mmtitles kbmm w_works chart charts charting pie bar block
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbAudDeveloper kbHomeProdSearch kbWin3xSearch kbWorksSearch _IKkbbogus kbHomeMMsearch kbEncartaSearch kbZNotKeyword kbMoneySearch kbBookshelfSearch kbEncartaEncycSearch kbWFWSearch kbMoney300 kbZNotKeyword3 kbWin310 kbWin311 kbWorks300 kbBookShelf1994 kbBookShelf1995 kbBookShelf1996 kbBookShelf1997 kbMusicalInst kbEncarta1994 kbEncarta1995 kbEncartaEnCyc1997 kbEncartaEnCyc1997Del
	Version           : :1.0,1994 edition,1995 edition,3.0,3.1,3.11
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
