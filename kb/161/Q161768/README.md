---
layout: page
title: "Q161768: SNALINK.EXE - Cancel Timeout in &#92;driver&#92;DLC"
permalink: /kb/161/Q161768/
---

## Q161768: SNALINK.EXE - Cancel Timeout in &#92;driver&#92;DLC

{% raw %}

	Article: Q161768
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.0,2.1,2.11,2.11 SP1,3.0,4.0; winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.0, 2.1, 2.11, 2.11 SP1, 3.0, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	When you stop the SNA Server service, the following error message may be
	displayed:
	
	  SNALINK.EXE - Cancel Timeout
	  The driver \driver\DLC failed to complete a cancelled I/O request in the
	  allotted time.
	
	After clicking OK, the same message may appear over and over again. You may not
	be able to perform any other operations until this error is cleared.
	
	
	CAUSE
	=====
	
	The error message is a Windows NT "hard error popup" which occurs if the SNA
	Server 802.2 link service terminates while the underlying DLC.SYS driver has
	completed IRP's to return to the calling thread. However, the link service has
	already ended. This error causes Windows NT to report a system-modal hard error
	popup which freezes the application subsystem until the user cancels the dialog.
	If multiple IRP's are completing, each IRP will cause another popup to appear.
	
	This problem will only occur when the SNA Server service is stopped, which causes
	underlying SNA Server link services to stop too.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	While this error may occur during SNA Server shutdown, it is recommended that the
	hard error popup be suppressed by configuring the following Windows NT registry
	setting:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Windows\ ErrorMode:
	  REG_DWORD: 2
	
	The default is 0 which causes the error popup to appear, requiring the user to
	manually clear the error. This option is not recommended for Windows NT servers
	which may not be accessible to users. A value of 2 causes the error to be
	reported to the event log and returns OK to the hard error so the system can
	continue. Popups don't appear. This entry is described in the Windows NT 3.5
	Resource Kit Volume 4 "Optimizing Windows NT", Appendix B on page 614.
	
	STATUS
	======
	
	Microsoft has confirmed this to be an operational issue with Windows NT version
	3.5, 3.51, and 4.0. It is recommended that the ErrorMode entry is modified for
	servers which aren't normally accessible to administrator personnel.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ200 kbSNAServ211 kbSNAServ400 kbSNAServ210 kbSNAServ211SP1
	Version           : WINDOWS:2.0,2.1,2.11,2.11 SP1,3.0,4.0; winnt:3.5,3.51,4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
