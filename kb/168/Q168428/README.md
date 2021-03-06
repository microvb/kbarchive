---
layout: page
title: "Q168428: HOWTO: Test Your ActiveX Documents (.VBD)"
permalink: /kb/168/Q168428/
---

## Q168428: HOWTO: Test Your ActiveX Documents (.VBD)

{% raw %}

	Article: Q168428
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0
	Operating System(s): 
	Keyword(s): kbcode kbDownload kbVBp500 kbCodeDownload kbGrpDSVB kbFAQ kbDSupport kbhowto kbieFAQ
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Visual Basic 5.0 introduces the ability to create ActiveX documents (.VBD files)
	for use with Internet browsers. This article will walk you step-by-step through
	creating a simple ActiveX document, show you how to test it while within the
	Visual Basic 5.0 development environment, then test it outside of the Visual
	Basic 5.0 development environment.
	
	The power of the Internet is that potential users from all of the world will be
	able to hit and view your page. (The same applies to the Intranet, although on a
	smaller scale; users all over your corporation may be able to hit and view your
	web page). With this in mind, different users will have different configurations
	and different software installed on their PC's. When your ActiveX page is hit by
	an Internet user, Internet Explorer searches the local PC for all of the files
	required by the document. If a required file is present and has a version equal
	to or greater than the version you require, it uses it. If a file is missing or
	is older than the version required, Internet Explorer prompts the user to
	install the file and will proceed to do so.
	
	While testing an ActiveX document, a problem occurs for developers because all of
	the required files are already installed onto the development machine. So how do
	you simulate a client's machine, one which has not been exposed to Visual Basic
	and the components you are using or which you've created? This article will also
	describe how to simulate such an environment.
	
	MORE INFORMATION
	================
	
	To begin, you need to create a simple ActiveX document for testing purposes. If
	you already have an ActiveX document to test, proceed to the section "Testing
	Your Document Using Visual Basic 5.0" later in this article.
	
	Creating a Simple ActiveX Document
	----------------------------------
	
	1. Start Visual Basic 5.0, or select New Project from the File menu if Visual
	  Basic 5.0 is already running. In the New Project dialog, select ActiveX
	  Document EXE and click OK.
	
	2. From the Project Window, open the User Documents folder and select
	  UserDocument1. This User Document is created by default. View the properties
	  for UserDocument1, change the (Name) property to MyTestDocument.
	
	3. Add some intrinsic controls to MyTestDocument, such as a CommandButton, a
	  Text Box, and a Label. You may modify the properties or add code to these
	  controls as desired. These controls will be used so you can verify that the
	  download of your ActiveX document succeeded.
	
	4. From the Project menu, choose Project1 Properties. Change the Project Name to
	  MyActiveXDocument. Click OK.
	
	5. Save the Project. Save the user document MyTestDocument.Dob and also save the
	  Project MyActiveXDocument.VBP.
	
	Testing Your Document Using Visual Basic 5.0
	--------------------------------------------
	
	The following steps assume you have Microsoft Internet Explorer version 3.00 or
	later installed onto your system. To obtain the latest version of Internet
	Explorer be sure to visit the following Web site:
	
	  http://www.microsoft.com/ie
	
	1. If you created the simple ActiveX document above, keep the project open. If
	  you are working with your own ActiveX document, open the desired project.
	
	2. Click the Start button on the Visual Basic toolbar, or choose Start from the
	  Run menu.
	
	  At this point, your document is ready to view with Internet Explorer. For
	  testing purposes, Visual Basic 5.0 has created a .VBD file in the current
	  working directory. This directory is usually where Visual Basic is installed.
	  This file can now be viewed with Internet Explorer.
	
	3. Open Internet Explorer.
	
	4. In the Address box, type in the path to the .VBD file, which will have the
	  same name as your project. For example, to open the simple ActiveX document
	  created above, type the following:
	
	  C:\Program Files\DevStudio\Visual Basic\MyTestDocument.VBD
	
	  NOTE: Your path to the .VBD file may be different, so modify the line above as
	  appropriate.
	
	  The .VBD file should open in Internet Explorer, displaying any controls you
	  added to the document and executing any code you've added to the project, as
	  appropriate.
	
	  If this test worked, you can modify the project as desired, adding code,
	  adding controls, etc. You may then continue to test the VBD file with
	  Internet Explorer simply by running the project and viewing the VBD file with
	  Internet Explorer.
	
	  NOTE: The VBD file is temporary; Visual Basic will delete the file when the
	  project stops executing.
	
	Creating Your Internet Download Setup
	-------------------------------------
	
	The following steps take you through the creation of your Internet download
	setup. If you have created your own ActiveX document (rather that using the
	example created above), substitute your ActiveX document name where necessary.
	
	1. From the File menu, choose Make MyActiveXDocument.Exe. Create the executable
	  file in the desired location.
	
	  NOTE: The executable file created is designed to execute as an ActiveX
	  document within Internet Explorer. The file cannot be executed successfully
	  by itself.
	
	2. Exit Visual Basic 5.0.
	
	3. Run the Application Setup Wizard. This Setup Wizard should be available from
	  the Start menu, under Programs\Visual Basic 5.0.
	
	  If you are prompted with the "Setup Wizard - Introduction," click Next.
	
	4. From the "Select Project and Options" step, click the Browse button to locate
	  your ActiveX document project. If you created the example provided with this
	  article, locate MyActiveXDocument.vbp.
	
	5. Under "Options," choose to "Create Internet Download Setup." Click Next.
	
	6. On the "Internet Distribution Location" step, select the location where you
	  would like to place the files for Internet download and click Next. For
	  testing purposes, "SWSETUP" may be sufficient.
	
	  NOTE: It is important to note that the folder must be accessible, with at
	  least read-only access, from other machines on your network in order to test.
	  In future deployments, you may wish to place the files created onto a web
	  server.
	
	7. For the "Internet Package" step, choose "Download from the Microsoft Web
	  site."
	
	  NOTE: With this option selected, when a user hits your ActiveX document with
	  Internet Explorer and needs a component installed, IE will go to the
	  Microsoft Web site to install the latest version. If you would like
	  information on how to use an alternate location, refer to the chapter on
	  "Distributing Your Applications" in the Visual Basic 5.0 Programmer's Guide.
	  You may desire to use an alternate location if you are developing an ActiveX
	  document for an intranet where potential users may not have access to the
	  World Wide Web.
	
	8. For the remaining steps in the Setup Wizard, go with the defaults, clicking
	  Next until you reach the final step.
	
	9. On the final step, you may save the template if you prefer. When you are
	  done, click Finish.
	
	The Visual Basic Setup Wizard creates all of the files necessary for an Internet
	download. The next section of this article describes how to test the page.
	
	Testing the Internet Download
	-----------------------------
	
	As a developer, you may want to test the Internet Download from your own machine
	first. Remember, however, that because Visual Basic 5 is already installed on
	your machine, you know all of the necessary files are installed and the ActiveX
	document should load without incident. To test the document from the development
	machine, locate the Internet download files the Setup Wizard created. In the
	setup folder there will be an HTM file; if you created the example above this
	file will be named MyActiveXDocument.HTM. Simply double-click the file or locate
	it with Internet Explorer to open it.
	
	The second test you should apply to your ActiveX document is testing it from a
	machine without Visual Basic 5.0 installed. If you do not have such a machine
	available to you for testing, refer to the "Simulating a Clean Machine" section
	of this article.
	
	From a machine that does not have Visual Basic 5.0 installed, use Internet
	Explorer to locate and open the HTM file created by the Setup Wizard.
	
	IMPORTANT NOTE: Before testing the ActiveX document, be sure the safety level in
	Internet Explorer is set to Medium or None. If the safety level is set to High,
	the required files will not get downloaded and the ActiveX document will not
	load. To check the security level in Internet Explorer, choose Options from the
	View menu. From the Options window, select the Security tab, and then click the
	Safety Level button.
	
	
	If you set the Safety Level to None, all of the missing components will be
	installed without warning. If the Safety Level is set to Medium, the following
	warnings will occur:
	
	First, you will be warned that an attempt to install the CAB file is being made
	if you created the example above you will be prompted to install
	MyActiveDocument.CAB. If you respond Yes, the MyActiveXDocument.Exe and
	MyActiveXDocument.INF will be installed onto the client machine in the
	Windows\OCCache folder.
	
	Second, you will be asked if you wish to install Microsoft Automation. The
	Authenticode screen will display information about this component. If you
	respond Yes, a similar screen will warn you that the Microsoft Visual Basic 5.0
	Run-time Library is going to be installed. Both of these components will be
	installed from the Microsoft Web site into the Windows\System folder
	(Windows\System32 folder on Windows NT).
	
	Third, a script warning will appear warning the user that the HTM file contains
	scripting code. This code is necessary in order to view your ActiveX document.
	
	These warnings are all part of the Internet Explorer's safety mechanisms. If you
	do not receive all of the above warnings, do not be alarmed. You may not receive
	a warning if a necessary component is already installed on the client machine or
	a security level option in Internet Explorer is set to something other than the
	defaults.
	
	As part of testing, you may wish to test various Internet Explorer security
	settings to be sure your document loads as expected under varying
	circumstances.
	
	Simulating a Clean Machine
	--------------------------
	
	As a developer, you should test your application on various machines with varying
	configurations. However, if you do not have a "clean machine" (one that does not
	have Visual Basic 5.0 or the Visual Basic 5.0 Run-time Library installed), the
	steps outlined below describe how to configure a development machine so that it
	behaves like a clean client. These steps may also be taken to clean a client
	machine that may have been previously exposed to your ActiveX document, Visual
	Basic 5.0, or the Visual Basic 5.0 Run-time Library.
	
	WARNING: Before following the steps below to simulate a clean machine, be aware
	that unregistering, renaming, and deleting any of the following files could
	impact other applications installed onto your machine. For more information
	about undoing the steps provided here, see the "Restoring Your Machine" section
	of this article.
	
	In order to clean a machine for testing an Internet download, you must begin by
	unregistering the Visual Basic 5.0 Run-time Library. This step will require a
	copy of REGSVR32.EXE. This file may be installed onto your development machine;
	if it is not, it may be found on the Visual Basic 5.0 installation CD-ROM.
	
	1. From the Start menu, choose Run.
	
	2. In the Run dialog, type in the following command;
	
	  "<PATH>\REGSVR32.EXE /U <Path to Windows
	  folder>\System\MSVBVM50.DLL"
	
	  NOTE: If you are running on a Windows NT machine, the MSVBVM50.DLL is
	  installed into the Windows\System32 folder.
	
	3. Next, rename or delete the Visual Basic 5.0 Run-time Library.
	
	4. From the Start menu, choose Find, and then select Files or Folder.
	
	5. In the Find dialog, search the entire hard drive for files named
	  MSVBVM50.DLL.
	
	  The file MSVBVM50.DLL may appear in more than one location; if it does, delete
	  or rename the file located in the Windows\System folder (System32 on Windows
	  NT platforms).
	
	6. Next, the Microsoft Automation DLL must be deleted or renamed. Follow the
	  steps outlined above for MSVBVM50.DLL, except locate and rename ASYCFILT.DLL,
	  which will also be located in the Windows\System folder (System32 on Windows
	  NT platforms). Do not delete other versions of this file if it is found in
	  alternative locations.
	
	7. Next, you must unregister and delete or rename any remaining dependency files
	  installed on the client machine. These files will typically be custom
	  controls that are used in the ActiveX document. For a list of the dependency
	  files used by your ActiveX document, open the INF file created by the Setup
	  Wizard and placed in the Support folder of the Internet Download setup.
	
	  The INF file will have a [Add.Code] section, listing the dependency files used
	  by your ActiveX document. For example, the MyActiveXDocument.INF file created
	  for the example in this article appears as follows:
	
	        [Add.Code]
	        MYACTIVEXDOCUMENT.EXE=MYACTIVEXDOCUMENT.EXE
	        ASYCFILT.DLL=ASYCFILT.DLL
	        MSVBVM50.DLL=MSVBVM50.DLL
	
	  The dependency files must be unregistered, if necessary, and deleted or
	  renamed. The MyActiveXDocument.Exe file does not need to be unregistered.
	  However, it will need to be deleted or renamed. Internet Explorer 3.x places
	  this file into the \Windows\OCCache folder. Internet Explorer 4.0 places this
	  file into the "\Windows\Downloaded Program Files" directory. If you are
	  uncertain whether a file needs to be unregistered or not, you can run
	  REGSVR32.EXE with the /U switch to determine whether or not it can be
	  unregistered. If you receive an error, the file does not need to be
	  unregistered.
	
	  NOTE: One file installed that is not listed in the [Add.Code] section is the
	  INF file which is installed into the Windows\OCCache folder for each ActiveX
	  document. This file will have the same name as the ActiveX EXE with an INF
	  extension; for example, MyActiveDocument.INF. For a truly clean machine, this
	  file would need to be deleted as well. However, not deleting the file will
	  not have any adverse affects on the setup.
	
	  Other dependency files may include OCX files for custom controls or DLLs for
	  various components. For example, if you used any of the Windows Common
	  Controls in your application ,the Add.Code section of your INF file may
	  appear as follows;
	
	        [Add.Code]
	        MYACTIVEXDOCUMENT.EXE=MYACTIVEXDOCUMENT.EXE
	        ASYCFILT.DLL=ASYCFILT.DLL
	        MSVBVM50.DLL=MSVBVM50.DLL
	        COMCTL32.OCX=COMCTL32.OCX
	
	  In order to remove the COMCTL32.OCX file from the system, run:
	
	  REGSVR32.EXE /U <PATH>\System\COMCTL32.OCX
	
	  This will unregister the control, then locate the file and either delete or
	  rename it. Most of the custom controls that ship with Visual Basic 5.0 will
	  install themselves into the Windows\System folder. Internet Explorer,
	  however, will install some custom controls into the Windows\OCCache folder.
	  You will need to be sure the path to the desired OCX is correct when using
	  REGSVR32.EXE or else an error will occur.
	
	  This same procedure must be followed for every dependency file used by your
	  ActiveX document.
	
	  Once all of the dependency files have been unregistered and renamed or
	  deleted, open Internet Explorer and view your HTM page. When you view the HTM
	  page, all of the missing components will automatically be downloaded and
	  installed onto the user's machine.
	
	Restoring Your Machine
	----------------------
	
	Opening the HTM file as described in the last step of the previous section of
	this article will restore your machine to its original configuration. Internet
	Explorer will download and register each required file for you. However, if
	something should go wrong during the Internet download setup, you can reverse
	the changes made by restoring all of the original files and registering the
	necessary components.
	
	Any file deleted or renamed would need to be renamed back to its original name or
	restored from the Windows Recycle Bin. If a file cannot be restored from the
	Windows Recycle Bin, an original may be found on the Visual Basic 5.0 CD-ROM
	(unless the file was provided by a third party, in which case you will need to
	restore the file from the appropriate location). Once the necessary files have
	been restored, you can run REGSVR32.EXE to register those files that were
	initially unregistered. For example, to register the Visual Basic 5.0 Run-time
	Library, execute the following command from the run dialog:
	
	  REGSVR32 <Path to Windows>\System\MSVBVM32.DLL
	
	Troubleshooting
	---------------
	
	This section addresses some of the problems you might encounter during the
	Internet Download setup.
	
	Problem 1:
	
	You receive one of the following error messages when you try to delete or rename
	the Visual Basic 5.0 Run-time Library:
	
	  Cannot delete MSVBVM50.DLL: Access is denied.
	
	  Cannot rename MSVBVM50.DLL: Access is denied.
	
	Resolution 1:
	
	You cannot delete a file while it is in use because Visual Basic 5.0 uses this
	file while it is running. Be sure Visual Basic 5.0 is not running when you
	attempt to delete this file. This error may also occur if Internet Explorer is
	currently or has recently viewed a Visual Basic 5.0 ActiveX Document. In this
	case, close Internet Explorer before attempting to delete the file.
	
	Problem 2:
	
	You receive the following error message:
	
	  The dynamic link library could not be found in the specified path...
	
	Resolution 2:
	
	The ActiveX document file is still present on the machine. Delete or rename the
	ActiveX document file found in the Windows\OCCache folder and refresh the page.
	If you built the ActiveX document example in this article, the file would be
	named MyActiveXDocument.Exe.
	
	Problem 3:
	
	You receive the following error message:
	
	  An error has occurred copying MSVBVM50.DLL. Ensure the location
	  specified below is correct...C:\TEMP\ICD10E.TMP
	
	The exact file names and paths may vary.
	
	Resolution 3:
	
	There is insufficient disk space on the target machine. Free up some disk space
	on the target machine and refresh the page.
	
	Problem 4:
	
	A dialog box with the following messages appear in Internet Explorer:
	
	  Opening file <ActiveX Document>.VBD
	
	  What would you like to do with this file?
	
	  Open it or Save it to disk.
	
	Resolution 4:
	
	This error occurs because the Visual Basic 5.0 Run-time Library (MSVBVM50.DLL) is
	not installed. This will most likely occur if the Internet Explorer safety level
	is set to High. Set the Internet Explorer safety level to Medium or None.
	
	REFERENCES
	==========
	
	Visual Basic 5.0 Component Tools Guide, Chapter 5 "Creating an ActiveX
	Document"
	
	Visual Basic 5.0 Programmer's Guide, Chapter 17 "Distributing Your Applications"
	
	For more information, see the following Webcast:
	
	  How Does Internet Component Download Work?
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbDownload kbVBp500 kbCodeDownload kbGrpDSVB kbFAQ kbDSupport kbhowto kbieFAQ 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVB500 kbZNotKeyword3
	Version           : WINDOWS:5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
