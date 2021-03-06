---
layout: page
title: "Q160018: PRB: Can't Register Controls from &quot;MSDEV&#92;REDIST&#92;OCX&quot; Directory"
permalink: /kb/160/Q160018/
---

## Q160018: PRB: Can't Register Controls from &quot;MSDEV&#92;REDIST&#92;OCX&quot; Directory

{% raw %}

	Article: Q160018
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.2,4.2b,5.0
	Operating System(s): 
	Keyword(s): kbcode kbole kbActiveX kbCtrl kbMFC kbRegistry kbVC420 kbVC500 kbGrpDSMFCATL
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 4.2b, 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 4.2b, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using Regsvr32.exe to register one of the controls from the
	MSDEV\REDIST\OCX directory, you might get an error saying:
	
	  "LoadLibrary("msmask32.ocx") failed. GetLastError returns 0x00000485."
	
	Attempting to call LoadLibrary() on the OCX will also fail with the same error
	code.
	
	CAUSE
	=====
	
	Most of the controls in the MSDEV\REDIST\OCX directory were built using MFC 4.0
	so they need Mfc40.dll and Msvcrt40.dll. There are two versions of Msvcrt40.dll:
	one in MSDEV\REDIST, and another in MSDEV\REDIST\ANSI. The version from
	MSDEV\REDIST needs Msvcirt.dll. If this file is not found, control registration
	will fail.
	
	RESOLUTION
	==========
	
	- Copy Msvcrt40.dll from MSDEV\REDIST\ANSI. This version doesn't need
	  Msvcirt.dll.
	  -or-
	
	- Copy Msvcrt40.dll and Msvcirt.dll from MSDEV\REDIST.
	
	MORE INFORMATION
	================
	
	Starting with Visual C++ 4.2, the shared DLL version of the C run time was
	changed from Msvcrt40.dll to Msvcrt.dll. This prevents having to keep a separate
	C run-time DLL for each version (for example, Msvcrt411.dll, Msvcrt42.dll, and
	so on). However, if an MFC 4.2 application were using an MFC 4.0 control, you
	would have two copies of the C run time loaded in memory (Msvcrt.dll and
	Msvcrt40.dll). To save precious memory, Msvcrt40.dll was converted to a
	"forwarder" DLL. All it does is forward calls to Msvcrt.dll and Msvcirt.dll.
	Starting with Windows NT 4.0, Msvcrt40.dll, Msvcrt.dll, and Msvcirt.dll ship
	with the operating system.
	
	A registration program will attempt to do a LoadLibrary() of the ActiveX/DLL and
	call DLLRegister() on it. If LoadLibrary() fails and GetLastError() returns
	1157(0x485), this means that a DLL needed by the control cannot be found (Error
	code 1157 is defined as ERROR_DLL_NOT_FOUND in WINERROR.H).
	
	To find out which DLL it can't load, use DUMPBIN /IMPORTS <CONTROL.OCX>
	from the command line. Dumpbin.exe is in MSDEV\BIN. This will list all the DLLs
	that the ActiveX Control is trying to load. DLLs will only be found if they are
	in the current directory, in the Windows System directory, or in a directory in
	your PATH. One of these DLLs could also be trying to load another DLL and not
	find it. In the case above, all the DLLs that DUMPBIN showed as being needed by
	MSMASK32.OCX were in the system directory.
	
	The next logical step would be to do a DUMPBIN on these DLLs. It turns out that
	DUMPBIN on Msvcrt40.dll told us that it needed Msvcirt.dll. If you have several
	DLLs in the chain, a quick way to narrow things down is to do a LoadLibrary() on
	each one. If LoadLibrary() fails on a DLL that is in the current, system or path
	directory, use DUMPBIN on it to check its list of DLLs. You will eventually find
	the offending DLL.
	
	REFERENCES
	==========
	
	For information about other possible reasons for ActiveX Control Registration
	failure, please see the following article in the Microsoft Knowledge Base:
	
	  Q140346 Possible Reasons for OLE Control Registration Failure
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbole kbActiveX kbCtrl kbMFC kbRegistry kbVC420 kbVC500 kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper kbVC420 kbVC500 kbVC32bitSearch kbVC420b kbVC500Search
	Version           : winnt:4.2,4.2b,5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
