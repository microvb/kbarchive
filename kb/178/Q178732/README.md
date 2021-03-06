---
layout: page
title: "Q178732: WD97: &quot;Word Cannot Find or Run the Application&quot; with EZ-Photo"
permalink: /kb/178/Q178732/
---

## Q178732: WD97: &quot;Word Cannot Find or Run the Application&quot; with EZ-Photo

{% raw %}

	Article: Q178732
	Product(s): Word 97 for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kb3rdparty kbdta word97
	Last Modified: 22-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	- Microsoft Outlook 98 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	One or more of the following symptoms may occur when you have EZ-Photo installed
	with Microsoft Word:
	
	- Duplicate EZ-Photo toolbar buttons are added to Microsoft Word.
	
	  -or-
	
	- When you click any of the EZ-Photo toolbar buttons that are installed by
	  EZ-Photo, one of the following error messages may appear:
	
	  Microsoft Word Err=1220, "Word cannot find or run the application."
	
	  -or-
	
	  The macro cannot be found or has been disabled because of your Macro security
	  settings.
	
	-or-
	
	- When you attempt to quit Word, you receive a message asking you to save a
	  file called EZPHOTO.
	
	CAUSE
	=====
	
	The Word add-ins installed by EZ-Photo version 2.7 (and possibly earlier
	versions of EZ-Photo) were designed to work with Microsoft Word for Windows 95
	and earlier.
	
	WORKAROUND
	==========
	
	To work around this problem, delete the Ezpwll32.wll, Ezphoto.wll, Ezpwll.wll,
	and Ezpwll16.wll files that are installed by EZ-Photo, and rename the global
	template (Normal.dot). To do this, follow these steps.
	
	NOTE: Deleting these files removes all functionality of EZ-Photo with Microsoft
	Word. However, the default functionality of EZ-Photo as a program is not
	affected.
	
	- For Microsoft Windows 95, Microsoft Windows 98, and Microsoft Windows NT 4.0,
	  follow these steps:
	
	  1. Quit all Windows programs.
	
	  2. Right-click Start, and then click Explore on the shortcut menu that
	     appears.
	
	  3. In the Windows Explorer, click Folder Options on the View menu.
	
	  4. On the View tab, click the "Show all files" option. If the "Show all
	     files" option does not appear, follow these steps:
	
	     a. On the View tab, in the Advanced settings list, double-click Files and
	        Folders.
	
	     b. Double-click Hidden files.
	
	  5. Click OK.
	
	  6. On the Tools menu, point to Find and click Files or Folders.
	
	  7. On the Name & Location tab, type one of the following file names in
	     the Named box:
	
	      - Ezpwll32.wll
	      - Ezphoto.wll
	      - Ezpwll.wll
	      - Ezpwll16.wll
	
	  8. Change the Look in box to the drive where Microsoft Word is installed. For
	     example, change the Look in box to either C:\ or Local Hard Drives
	     (C:,D:).
	
	  9. Select the Include subfolders check box.
	
	     NOTE: The Include subfolders check box is selected by default.
	
	  10. Click Find Now.
	
	  11. Click to select the file you searched for in step 7 that appears in the
	     Find dialog box.
	
	  12. On the File menu, click Delete.
	
	  13. Click Yes to the following message to confirm the file deletion:
	
	  Are you sure you want to send 'filename' to the Recycle Bin?
	
	  14. Repeat steps 7 through 13 for each of the files listed.
	
	  15. In the Named box, type "Normal.dot" (without the quotation marks).
	
	     Please see the NOTES that follow these steps for more information about
	     the Normal.dot file (global template).
	
	  16. Click Find Now.
	
	     NOTE: The Look in box should still display either C:\ or Local Hard Drives
	     (C:,D:) as in step 8, and the Include subfolders check box should still
	     be selected.
	
	  17. Click to select the Normal.dot file that is listed in the Find dialog
	     box.
	
	  18. On the File menu, click Rename.
	
	  19. Type "Normal.old" (without the quotation marks) and press ENTER.
	
	     NOTE: Repeat steps 16 and 17 for each Normal.dot file that is listed in
	     the Find dialog box.
	
	  20. On the File menu, click Close to close the Find dialog box.
	
	  -or-
	
	- For Microsoft Windows Millennium Edition (Me) or Microsoft Windows 2000,
	  follow these steps:
	
	  1. Quit all Windows programs.
	
	  2. Right-click Start, and then click Explore on the shortcut menu that
	     appears.
	
	  3. In the Windows Explorer, on the Tools menu, click Folder Options.
	
	  4. On the View tab, under Advanced settings, click "Show hidden files and
	     folders".
	
	     If "Hidden files and folders" is not displayed, follow these steps first:
	
	     a. On the View tab, under Advanced settings, double-click Files and
	        Folders.
	
	     b. Double-click Hidden files and folders.
	
	  5. Click OK.
	
	  6. On the Standard toolbar, click Search.
	
	  7. Under "Search for files or folders named", type one of the following file
	     names:
	
	      - Ezpwll32.wll
	      - Ezphoto.wll
	      - Ezpwll.wll
	      - Ezpwll16.wll
	
	  8. On the "Look in" list, click the drive where Microsoft Word is installed.
	     For example, click C:\ or Local Harddrives (C:,D:).
	
	  9. Under Search Options, select the Advanced Options check box, and then
	     select the Search Subfolders check box.
	
	  10. Click Search Now.
	
	  11. Click to select the file you searched for in step 7 that appears in the
	     Search Results pane.
	
	  12. On the File menu, click Delete.
	
	  13. Click Yes to the following message to confirm the file deletion:
	
	  Are you sure you want to send 'filename' to the Recycle Bin?
	
	  14. Repeat steps 7 through 13 for each of the files listed.
	
	  15. Under "Search for files or folders named", type "Normal.dot" (without the
	     quotation marks).
	
	     IMPORTANT: Please see the notes that follow these steps for more
	     information about the Normal.dot file (global template).
	
	  16. Click Search Now.
	
	     NOTE: The "Look in" list should still display either C:\ or "Local
	     Harddrives (C:,D:)" as in step 8.
	
	  17. Click to select the Normal.dot file that is listed in the Search Results
	     pane.
	
	  18. On the File menu, click Rename.
	
	  19. Type "Normal.old" (without the quotation marks) and press ENTER.
	
	     NOTE: Repeat steps 16 through 18 for each Normal.dot file that is listed
	     in the Find dialog box.
	
	NOTES:
	
	After you rename the Normal.dot file, Word builds a new global template
	(Normal.dot) the next time you start and quit Microsoft Word. Note that when you
	rename the Normal.dot file, several options in Word may be reset back to their
	default settings or may be lost. These include custom styles, custom toolbars,
	macros, and AutoText entries. For this reason, it is strongly recommended that
	you rename the Normal.dot file rather than delete it.
	
	Certain installations may yield more than one legitimate Normal.dot file. These
	situations include multiple versions of Word running on the same computer or
	several workstation installations on the same computer. In these situations, you
	may not want to rename each of the Normal.dot files that is listed in the Find
	dialog box. You may need to pay special attention so that you rename the correct
	copy of Normal.dot.
	
	Macros, AutoText entries, shortcut key combinations, custom toolbars, toolbar
	settings, and styles are stored in the Normal template. After renaming the
	Normal template, you can copy macros, AutoText entries, shortcut key
	combinations, custom toolbars, toolbar settings, and styles to your new Normal
	template.
	
	Use the following steps to regain lost functionality after you rename the
	Normal.dot file:
	
	1. Start and then quit Microsoft Word. This allows Word to rebuild a new
	  Normal.dot (global template) file.
	
	2. Start Word again.
	
	3. On the Tools menu, click Templates and Add-Ins.
	
	4. In the Templates and Add-ins dialog box, click Organizer.
	
	5. In the Organizer dialog box, click the tab that you want to regain lost
	  functionality.
	
	  For example, if you want to regain your lost styles, click the Styles tab.
	
	6. There are two sides to the Organizer dialog box. One side shows your
	  Normal.dot file in the "Styles available in" box. The other side shows the
	  document you currently have open in Word [for example: "Document1
	  (Document)"] in the other "Styles available in" box.
	
	  To open your renamed Normal.dot file (renamed Normal.old in step 18), follow
	  these steps:
	
	  a. On the side that shows "Document1 (Document)" in the "Styles available in"
	     box, click Close File. The Close File button changes to an Open File
	     button.
	
	     NOTE: Do not click Close File on the Normal.dot (global template) side of
	     the Organizer dialog box.
	
	  b. Click Open File.
	
	  c. In the Open dialog box, click your renamed Normal template file. For
	     example, click Normal.old.
	
	  d. Click Open.
	
	7. Click the items you want to copy from your renamed template to your new
	  Normal.dot template, and then click Copy.
	
	  NOTE: To select a range of items, hold down SHIFT and click the first and last
	  items in the range. To select nonadjacent items, hold down CTRL as you click
	  each item.
	
	8. Repeat steps 5 through 7 for any other items you want to add back to your new
	  Normal.dot template.
	
	  NOTE: If you copy toolbars that you assigned custom macros to, you must also
	  copy the macros.
	
	  WARNING: Do not copy any macros whose functionality and purpose are unknown to
	  you.
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	For more information about EZ-Photo and this problem, please contact Adobe
	Systems Incorporated.
	
	For information about how to contact Adobe, click the appropriate article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q65416 Hardware and Software Third-Party Vendor Contact List, A-K
	
	  Q60781 Hardware and Software Third-Party Vendor Contact List, L-P
	
	  Q60782 Hardware and Software Third-Party Vendor Contact List, Q-Z
	
	
	Additional query words: ezphoto drop copy drag-and-drop OL98 Outlook ez-photo ez photo easy easyphoto e-z-photo e-z eazyphoto eazy
	
	======================================================================
	Keywords          : kb3rdparty kbdta word97 
	Technology        : kbWordSearch kbOutlookSearch kbWord97 kbWord97Search kbZNotKeyword2 kbOutlook98Search kbZNotKeyword3
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
