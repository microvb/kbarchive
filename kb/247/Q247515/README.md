---
layout: page
title: "Q247515: Program Is Not Listed in Add/Remove Programs After Installation"
permalink: /kb/247/Q247515/
---

## Q247515: Program Is Not Listed in Add/Remove Programs After Installation

{% raw %}

	Article: Q247515
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After you install a program on your computer, the program is not listed in the
	Add/Remove Programs tool in Control Panel. Also, other programs that are
	installed on your computer and that were previously listed in Add/Remove
	Programs may no longer be listed.
	
	CAUSE
	=====
	
	This problem can occur if the program you installed creates a registry key name
	that is longer than 60 characters in length. Add/Remove Programs only lists
	program names it locates up to the point it encounters this situation.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	To work around this problem, use one of the following methods:
	
	Uninstall the Program
	---------------------
	
	The installation program may detect that this program is already installed on
	your computer and provide an option to uninstall it. When this program is
	removed, the other missing programs in Add/Remove Programs are listed again.
	
	Run the Uninstall Program Included in the Uninstall Folder
	----------------------------------------------------------
	
	Some programs create a folder under the Winnt folder that contains a "$"
	character at the start and end of the folder name. This folder may contain an
	uninstall program that you can run to remove the program you previously
	installed on your computer. Note that these folders are usually hidden, and that
	you may need to configure Windows Explorer to view hidden files and folders. To
	do so, right-click Start, click Explore, click Options on the View menu, and
	then click "Show all files".
	
	
	Use the Uninstall Command Displayed in the Registry
	---------------------------------------------------
	
	1. Use Registry Editor (Regedit.exe) to view the following registry key:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
	
	2. Double-click the UninstallString registry value, copy the contents of the
	  Value Data box by selecting the contents and pressing CTRL+C, and then quit
	  Registry Editor.
	
	3. Click Start, click Run, press CTRL+V to paste the uninstall command, and then
	  click OK.
	
	Shorten the Registry Key Name
	-----------------------------
	
	Run Regedit.exe to view the following registry key:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
	
	Click the registry key for the program you installed, click Rename on the Edit
	menu, and then use a name with less than 60 characters. Note that if the
	DisplayName value is longer than 32 characters, it is not displayed. To rename
	it, double-click DisplayName and use a name up to 32 characters in length.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Programs are sorted alphabetically within the Uninstall registry key, and any
	keys listed after the long key name are ignored.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch
	Version           : winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
