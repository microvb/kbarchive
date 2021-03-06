---
layout: page
title: "Q162925: ADT/ODE: Setup Does Not Create Certain Shortcuts"
permalink: /kb/162/Q162925/
---

## Q162925: ADT/ODE: Setup Does Not Create Certain Shortcuts

{% raw %}

	Article: Q162925
	Product(s): Microsoft Access Distribution Kit
	Version(s): 
	Operating System(s): 
	Keyword(s): kberrmsg kbusage
	Last Modified: 16-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Office 97 Developer Edition 
	-------------------------------------------------------------------------------
	
	Advanced: Requires expert coding, interoperability, and multiuser skills.
	
	
	SYMPTOMS
	========
	
	If you install an ODE run-time application to a folder that contains parentheses
	() in the folder name, any shortcut that points to the installation folder will
	not be created.
	
	NOTE: This behavior occurs only with a Microsoft Access Developer's Toolkit
	(ADT), version 7.0 or a Microsoft Office Developer Edition Tools (ODE) run-time
	application being installed on Microsoft Windows NT, version 3.51.
	
	CAUSE
	=====
	
	This behavior is caused by a problem with the ACME Setup utility used by the ADT
	and the ODE.
	
	RESOLUTION
	==========
	
	On Windows NT 3.51, do not use installation folders that contain parentheses.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Office 97 Developer
	Edition Tools.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start the Setup Wizard.
	
	2. Add the Northwind sample database set as the Application's Main File and a
	  custom workgroup file that can be created by copying the system.mdw from the
	  Windows\System folder to custom.mdw set as Workgroup File.
	
	3. Create the following three shortcuts with the file to open being the
	  Northwind sample database file:
	
	   - One with the run-time option (wizard-provided command line)
	
	   - One with the workgroup option (wizard-provided command line)
	
	   - One with a user specified Command Line with wrkgadm.exe as the executable
	
	4. Click Next to go to the Registry Entries page of the Setup Wizard, and click
	  Next again.
	
	5. Make sure that Microsoft Access Run-time Version and Workgroup Administrator
	  are selected on the next page, and click Finish to generate the disk images.
	
	6. Run Setup from the disk images folder under the Setup Wizard folder to
	  install the run-time application. Change the installation folder to
	  c:\sample(sample).
	
	  Note that you receive the following error message for the run-time shortcut
	  and the wrkgrp shortcut:
	
	  Setup was unable to create an item in the Program Manager group
	  '<application name>', item: ' "<shortcut
	  name>",,0,0,0,"C:\sample(sample)",0,0,0'
	
	However, the Workgroup Administrator shortcut is created and Setup is completed
	"successfully."
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbusage 
	Technology        : kbOfficeSearch kbAudDeveloper kbOffice97Search kbOffice97 kbOffice97DevSearch
	Hardware          : x86
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
