---
layout: page
title: "Q299645: BUG: Error &quot;Unable to Register MSADO15.TLB&quot; If You Use PDW Pkg."
permalink: /kb/299/Q299645/
---

## Q299645: BUG: Error &quot;Unable to Register MSADO15.TLB&quot; If You Use PDW Pkg.

{% raw %}

	Article: Q299645
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbwizard kbADO kbAppSetup kbDeployment kbMDAC kbVBp kbVBp600bug kbGrpDSVB kbDSupport
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use a package that you created with the Package and Deployment Wizard
	(PDW) to install a Visual Basic application, you may receive the following error
	message (or similar) during the installation:
	
	  Unable to register MSADO15.TLB
	
	This error message may reference any of the following files:
	
	- MSADO15.TLB
	- MSADO20.TLB
	- MSADO21.TLB
	- MSADO25.TLB
	
	CAUSE
	=====
	
	The Package and Deployment Wizard adds the type library (.tlb) file to the
	package because the type library is referenced in your project. The PDW also
	erroneously assigns the $(DLLSelfRegister) registration macro to the type
	library in the Setup.lst file that is created for your installation package.
	
	Most commonly, this problem occurs when your Visual Basic project contains a
	reference to a version of ActiveX Data Objects (ADO) that is earlier than the
	latest installed version. The reference for the latest installed version of ADO
	points to MSADO15.DLL. Earlier version references point to the above-mentioned
	ADO type library files.
	
	RESOLUTION
	==========
	
	This file does not need to be explicitly included in your package. If you have a
	reference to an ADO type library in your project, you are utilizing ADO in your
	application and must distribute Microsoft Data Access Components (MDAC_TYP.EXE).
	The only exception is if you can guarantee that the correct version of MDAC will
	already be installed on your target computers. Because the MDAC installer
	includes the type library, there is no reason to include it specifically.
	
	There are several ways to resolve this problem. Which method you use depends on
	your circumstances and whether it is convenient for you to repackage the
	application. In Resolutions 1 and 2, you do not have to repackage the
	application. Resolutions 3, 4, and 5 require repackaging. Resolutions 4 and 5
	are the only long-term fixes and are recommended.
	
	Resolution 1:
	
	1. Locate the Setup.lst file for your package.
	
	2. In any text editor, open Setup.lst.
	
	3. In Setup.lst, locate the line that references the ADO type library that is
	  referenced in the error. If you are using Notepad, you can search for the
	  file name.
	
	4. Change $(DLLSelfRegister) to $(TLBRegister).
	
	5. Save the file, and try the installation again.
	
	Resolution 2:
	
	1. Locate the Setup.lst file for your package.
	
	2. In any text editor, open Setup.lst.
	
	3. In Setup.lst, locate the line that references the ADO type library that is
	  referenced in the error. If you are using Notepad, you can search for the
	  file name.
	
	4. Delete this line from Setup.lst.
	
	5. Make sure that the File##= statements are sequential, and, if necessary,
	  renumber the lines after the line that you deleted.
	
	6. Save the file, and try the installation again.
	
	Resolution 3:
	
	1. Start the Package and Deployment Wizard, and open the Package script if it
	  was saved.
	
	2. Complete the steps in the wizard until you reach the "Package and Deployment
	  Wizard - Included Files" page.
	
	3. Clear the check box next to the ADO type library that is referenced in the
	  error message.
	
	4. Complete the steps to repackage the application, and try the installation
	  again.
	
	Resolution 4:
	
	1. Locate the VB6DEP.ini file. By default, this file is located in the
	  C:\Program Files\Microsoft Visual Studio\VB98\Wizards\PDWizard\ folder.
	
	2. In any text editor, open VB6DEP.ini.
	
	3. Locate the [Do Not Redistribute] section.
	
	4. Add the following lines to the [Do Not Redistribute] section:
	
	  
	
	  MSADO15.TLB=
	  MSADO20.TLB=
	  MSADO21.TLB=
	  MSADO25.TLB=
	
	5. Save the file, and close the text editor.
	
	6. Repackage your application, and try the installation again.
	
	NOTE: This method prevents the problem from reoccurring.
	
	Resolution 5:
	
	1. Open your project in Visual Basic.
	
	2. From the Project menu, click References. Note the version of Microsoft
	  ActiveX Data Objects Library that is selected, and select the check box for
	  the ADO reference. If the reference points to a .tlb file, clear the check
	  box. Scroll the list to find the other versions of ADO, select the latest
	  version that points to MSADO15.DLL, and click OK.
	
	3. Test the project to confirm that the ADO features still work properly.
	
	4. Save the project, and then build the EXE.
	
	5. Repackage your application, and try the installation again.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Package and Deployment
	Wizard for Visual Basic 6.0.
	
	MORE INFORMATION
	================
	
	The error is raised because the PDW attempts to use $(DLLSelfRegister) for type
	libraries rather than $(TLBRegister). However, if you receive this error during
	installation, it does not necessarily mean that the installation will fail. It
	also does not mean that the application will not run after installation. This
	error does indicate that you may have a different version of the ADO type
	library referenced in your project than you are distributing with your
	application. This can potentially cause other problems, so Microsoft recommends
	that you verify the version information. See the "References" section for
	additional information.
	
	REFERENCES
	==========
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q217754 HOWTO: Control Which MDAC Version the Package and Deployment Wizard
	  (PDW) Distributes
	
	  Q213846 INFO: Deploy Database Applications with the Package and Deployment
	  Wizard (PDW)
	
	Additional query words: MSADO15 MSADO20 MSADO21 MSADO25
	
	======================================================================
	Keywords          : kbwizard kbADO kbAppSetup kbDeployment kbMDAC kbVBp kbVBp600bug kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : :6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
