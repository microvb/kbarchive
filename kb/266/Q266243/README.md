---
layout: page
title: "Q266243: HOWTO: Add CPU Support for Existing eVC Projects"
permalink: /kb/266/Q266243/
---

## Q266243: HOWTO: Add CPU Support for Existing eVC Projects

{% raw %}

	Article: Q266243
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbDSupport kbGrpDSETK
	Last Modified: 10-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft eMbedded Visual C++ version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you develop applications for Windows CE devices, it may be necessary to
	later add support for another central processing unit (CPU) when you port an
	application to target a different type of device. This article explains how to
	use the eMbedded Visual C++ IDE to add CPU support for existing projects.
	
	MORE INFORMATION
	================
	
	The cross-compiler functionality of eMbedded Visual C++ adds a level of
	complexity to project and workspace management in the IDE that does not appear
	in the desktop version of Microsoft Visual Studio. You must pay attention to
	which device or platform you want to target for the application, and also which
	CPUs to build the code for. For example, different vendor Palm-sized-class
	devices use different CPUs. Therefore, it can be easy to forget or fail to plan
	for which CPUs to support for your application.
	
	The eMbedded Visual C++ tools allow you to add support of a CPU if the CPU
	support exists for that platform. For example, there are no Palm-sized version
	1.2 devices that use the StrongARM CPU; therefore, you cannot add the ARM CPU
	support for your project to target the Palm-sized 1.2 device.
	
	Similarly, if an existing project targets only a CPU found in the retail Software
	Development Kits (SDKs) but not a custom SDK that is provided by a third-party,
	then adding support for the custom SDK can be complicated. For additional
	information, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q266240 PRB: Custom SDK Not Available for Existing eVC Projects
	
	The steps below describe how to use the IDE to add the needed CPU support.
	Consider a project that was created for the Hand-Held Pro 3.0 platform with
	support only for the MIPS CPU. The project needs to be compiled for the
	StrongARM CPU. The following steps simulate this scenario:
	
	1. Open eMbedded Visual C++.
	
	2. From the File menu, click New, and then click the Projects tab.
	
	3. Give a name to a new project, and then click WCE Application.
	
	4. In the CPUs list box, click to select the Win32 (WCE MIPS) check box.
	
	5. Clear all other CPUs.
	
	6. Click OK.
	
	You now have a project that will target any platforms for which you have
	installed SDKs that support the MIPS CPU. Notice that if you have any SDKs that
	do not support the MIPS CPU, their platform names are not listed in the IDE's
	drop-down list box list of platforms.
	
	Follow these steps to add the ability to compile the StrongARM CPU:
	
	1. With the current project open, click Configurations on the Build menu.
	
	2. Click Add.
	
	3. Click Win32 (WCE ARM) from CPU drop-down list.
	
	4. Click *Default Debug Configuration from the Copy settings from drop-down list
	  box.
	
	5. Click OK.
	
	You can repeat these steps to add a Release configuration.
	
	Notice that there is no option to select a CPU that is exclusively supported in
	another SDK, such as a custom SDK. For example, if you have installed a custom
	SDK for a custom x86 CEPC device, that SDK only supports the X86 CPU. Yet X86 is
	not listed in the CPU drop-down list box in the Build Configurations dialog box.
	Consequently, you'll must create a new, empty project to target the X86 CPU, and
	then include the existing project's source files.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDSupport kbGrpDSETK 
	Technology        : kbVCsearch kbAudDeveloper kbVCeMb
	Version           : WINDOWS:3.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
