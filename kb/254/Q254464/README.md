---
layout: page
title: "Q254464: PRB: Can't Add T-SQL Debugger to the Visual Basic Add-in Manager"
permalink: /kb/254/Q254464/
---

## Q254464: PRB: Can't Add T-SQL Debugger to the Visual Basic Add-in Manager

{% raw %}

	Article: Q254464
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbTSQL kbVBp600 kbGrpDSVBDB kbDSupport
	Last Modified: 09-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After Installing Visual Basic 6.0 Enterprise Edition and the Enterprise Tools,
	the T-SQL Debugger may not be listed as an available add-in in the Visual Basic
	Add-in Manager.
	
	CAUSE
	=====
	
	The current user is not logged in as the same user who installed Visual Basic.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The typical (default) installation of the Visual Studio/Visual Basic 6.0
	Enterprise edition installs the TSQL Debugger client-side components. These
	components, however, are not installed if the Enterprise Tools option is cleared
	when you perform a custom installation. The T-SQL Debugger client-side
	components and .dll files are installed in the following folder:
	
	  drive:\Microsoft Visual studio installation directory\VB98\TSQL
	
	If the T-SQL Debugger entry is not listed in the Add-in Manager after you install
	Visual Basic and the Enterprise Tools, verify that the add-in components have
	been installed correctly:
	
	1. Make sure that the following files are present in the TSQL folder:
	
	   - Vbsdiadd.dll
	
	   - Vbsdidb.dll
	
	   - Vbsdicli.exe
	
	  If you do not see the TSQL folder or the mentioned files in your Visual Basic
	  installation directory, then rerun the Visual Basic (or Microsoft Visual
	  Studio) installation program. Be sure to select custom from the installation
	  dialog box, and then choose Select All for the Enterprise Tools selection.
	
	  After completing the installation, restart the system and check to see if the
	  Visual Basic Add-in Manager lists the T-SQL Debugger.
	
	2. If the TSQL folder and the listed files are there, then try reregistering the
	  Vbsdiadd.dll and Vbsdidb.dll files, and then check to see if the T-SQL
	  Debugger add-in is listed in the Visual Basic Add-in Manager.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q190212 Add-Ins Only Visible to the User Who Installs VB
	
	Additional query words:
	
	======================================================================
	Keywords          : kbTSQL kbVBp600 kbGrpDSVBDB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
