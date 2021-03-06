---
layout: page
title: "Q270330: FILE: Corrupted IIS Index in July 2000 MSDN Library"
permalink: /kb/270/Q270330/
---

## Q270330: FILE: Corrupted IIS Index in July 2000 MSDN Library

{% raw %}

	Article: Q270330
	Product(s): Microsoft Developer Network
	Version(s): WINDOWS:July 2000
	Operating System(s): 
	Keyword(s): kbfile kbHTMLHelp kbMSDN kbDSupport kbGrpDSTools
	Last Modified: 05-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Developer Network (MSDN) July 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following error message appears when you access Internet Information Server
	(IIS) index entries in the July 2000 MSDN Library:
	
	  The page cannot be displayed.
	  Cannot find server or DNS Error.
	
	The IISREF.chi and IISREF.chm files contain errors that cause all index entries
	to fail.
	
	MORE INFORMATION
	================
	
	The IISREF.exe patch provides updates for these two files. Before you install
	the new files, you must find the faulty IISREF.chm file on your hard drive or
	install this file if it is not already there.
	
	This file will exist locally if you performed a full installation of the July
	2000 MSDN Library. It also could be there if you selected to install Platform
	SDK components in a "custom" MSDN Library installation. A "typical" installation
	does not install the .chm files. If you determine that the IISREF.chm file has
	not been installed, follow these steps to move it to the hard drive:
	
	1. In Control Panel, double-click Add-Remove Programs.
	
	2. Select MSDN Library - July 2000, and click Add/Remove.
	
	3. In MSDN Library Setup, click the Add/Remove button.
	
	4. In the Options list, select Platform SDK Documentation.
	
	5. Click the Change Option button.
	
	6. In the next Options list, make sure that Web Services is selected.
	
	7. Click OK, and then click Continue.
	
	The next step is to replace the IISREF.chi and IISREF.chm files with newer
	files:
	
	1. Close any open instances of the MSDN Library.
	
	2. Find the installation folder for the July 2000 MSDN Library. You can do this
	  by searching your computer for IISREF.chm. The default installation folder
	  is:
	
	  .\Program Files\Microsoft Visual Studio\MSDN\2000JUL\1033
	
	3. Delete the IISREF.chi and IISREF.chm files in that folder.
	
	4. Copy the updated IISREF.chi and IISREF.chm files to the same folder.
	
	5. Reopen the MSDN Library and click the Index tab.
	
	At this point, the MSDN Library must recreate the MSDN020.chw file, which
	contains keyword information. This process takes several minutes even on fast
	computers. When the process is finished, the index should appear and the
	Internet Information Services (IIS) keywords should work correctly.
	
	The following file is available for download from the Microsoft Download Center:
	
	  IISREF.exe (
	  http://download.microsoft.com/download/msdnlib/Patch/1.0/WIN98Me/EN-US/IISREF.exe)
	
	Release Date: Aug-7-2000
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	The IISREF.exe file contains the following files:
	
	+----------------------+
	| File name  | Size    | 
	+----------------------+
	| IISREF.CHI | 102 KB  | 
	+----------------------+
	| IISREF.CHM | 1.27 MB | 
	+----------------------+
	
	Additional query words: IISREF
	
	======================================================================
	Keywords          : kbfile kbHTMLHelp kbMSDN kbDSupport kbGrpDSTools 
	Technology        : kbMSDNSearch kbZNotKeyword2
	Version           : WINDOWS:July 2000
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
