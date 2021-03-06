---
layout: page
title: "Q160329: Msbatch.inf Parameters: Installing with PCI Network Adapters"
permalink: /kb/160/Q160329/
---

## Q160329: Msbatch.inf Parameters: Installing with PCI Network Adapters

{% raw %}

	Article: Q160329
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): kbsetup win95
	Last Modified: 14-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to install Windows 95 using a PCI network adapter and
	an Msbatch.inf file for batch installations of Windows 95.
	
	MORE INFORMATION
	================
	
	Microsoft does not encourage or support changes to .inf files; therefore,
	Microsoft Technical Support does not support the procedure in this article.
	Although we have tested the following procedure and it appears to function as
	described, make a backup copy of your .inf file before you proceed.
	
	When you are installing Windows 95 over the network using a PCI network adapter,
	the network adapter is not recognized until after the first reboot. Therefore,
	you have no network connectivity to finish copying all the necessary drivers.
	However, using an Msbatch.inf file, you can specify the network adapter on the
	"netcards=" line in the [Network] section of the file. When you do this, all of
	the necessary drivers are copied at the first reboot, but you receive the
	following error message:
	
	  Windows Networking
	  Your network adapter <network adapter name> is not working properly.
	  You may need to set it up again. For more information, see the Network
	  Troubleshooter in Windows Help.
	
	When you click OK, Setup proceeds normally. This occurs because the driver is
	installed, but the PCI bus has not been enumerated. Once the bus has been
	enumerated, the adapter functions correctly and this error message does not
	occur.
	
	This error message can interrupt an automated network installation. To work
	around this error message, follow these steps:
	
	In the Msbatch.inf file, modify the [Install] section to include the following
	line:
	
	  AddReg=pcinic.reg
	
	Also, add the following section and key to the Msbatch.inf file:
	
	  [pcinic.reg]
	  HKLM,\System\CurrentControlSet\Services\Class\Net\0000,
	  "DisableWarning",,"1"
	
	  NOTE: This line should be typed as a single line. It has been wrapped
	  in this article for readability purposes.
	
	  NOTE: For multiple adapters, multiple registry entries may be needed in
	  the Msbatch.inf file. For example two network adapters may require the
	  following section and keys:
	
	     [pcinic.reg]
	     HKLM,\System\CurrentControlSet\Services\Class\Net\0000,
	     "DisableWarning",,"1"
	     HKLM,\System\CurrentControlSet\Services\Class\Net\0001,
	     "DisableWarning",,"1"
	
	NOTE: If you are installing Dial-Up Networking, this procedure is not needed
	because the error message does not occur.
	
	Additional query words: automate
	
	======================================================================
	Keywords          : kbsetup win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : :
	
	=============================================================================
	

{% endraw %}
