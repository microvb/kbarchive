---
layout: page
title: "Q170844: Msbatch.inf Parameters: Installing PCMCIA Network Adapter Driver"
permalink: /kb/170/Q170844/
---

## Q170844: Msbatch.inf Parameters: Installing PCMCIA Network Adapter Driver

{% raw %}

	Article: Q170844
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:95
	Operating System(s): 
	Keyword(s): kbhw kbsetup win95 kbHardware
	Last Modified: 25-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to perform a batch installation of Windows 95 using
	an Msbatch.inf file and a PCMCIA (PC Card) network adapter with drivers supplied
	by the manufacturer (not included with Windows 95).
	
	MORE INFORMATION
	================
	
	Microsoft does not encourage or support changes to .inf files; therefore,
	Microsoft Technical Support does not support the procedure in this article.
	Although we have tested the following procedure and it appears to function as
	described, make a backup copy of your .inf file before you proceed.
	
	When you install Windows 95 over a network using a PCMCIA network adapter, the
	network adapter is not recognized until after the PCMCIA wizard runs. By the
	time the PCMCIA wizard runs, the temporary folder containing the PCMCIA network
	adapter drivers created by Setup has already been deleted. Because of this,
	Setup stops and prompts you for the network adapter driver disk provided by the
	manufacturer of the adapter. To automate the process, follow these steps:
	
	1. Use the Inf Installer tool to integrate the manufacturer's .inf file. The Inf
	  Installer tool is located on the Windows 95 CD-ROM in the
	  Admin\Nettools\Netsetup folder. For information about how to use this tool,
	  see the Infinst.txt file in the same folder.
	
	  NOTE: If the PCMCIA network adapter is a multifunction adapter, the
	  manufacturer's driver disk may contain more than one .inf file. If this is
	  the case, use the Inf Installer tool with the .inf file containing the
	  following entry:
	
	  Class=MultiFunction
	
	  IMPORTANT: If the Inf Installer tool does not integrate the .inf file
	  successfully, there may be a problem with the .inf file. If this occurs,
	  contact the manufacturer to inquire about obtaining an updated .inf file. You
	  cannot complete this procedure without an updated file that works with the
	  Inf Installer tool.
	
	2. Copy the network adapter's driver and .inf file from the manufacturer's
	  driver disk to the NetSetup folder on your server.
	
	3. Run Batch 2.0 to create the Msbatch.inf file with the options you want. The
	  following settings are required:
	
	   - Set the installation type to Custom. This is required so that Dial- Up
	     Networking can be added. Dial-Up Networking must be added because there is
	     no detection of the network adapter when the PCMCIA wizard is not run. If
	     there is no detection of the network adapter, the client and protocols are
	     not downloaded to the computer during Setup. Without these files, there is
	     no network connectivity. Adding Dial-Up Networking allows the installation
	     of the client and protocols during Setup.
	
	   - Set Dial-Up Networking to be installed as an optional component.
	
	4. Save the Msbatch.inf file.
	
	5. Use any text editor (such as Notepad) to open the Msbatch.inf file. Add the
	  following line to the [Network] section of the file:
	
	  IgnoreDetectedNetcards=1
	
	  This entry prevents Setup from displaying any dialog boxes that prompt for
	  disks if a network adapter is detected because of real-mode drivers that are
	  currently loaded in memory. It also prevents Setup from attempting to install
	  NDIS2 support for the network adapter instead of 32-bit protected-mode
	  drivers.
	
	6. In the [Network] section of the file, verify that this line is present:
	
	  WorkStationSetup=0
	
	7. Create these sections and entries in the file:
	
	  [DestinationDirs]
	  <section_to_copy_inf>=17
	  <section_to_copy_vxd>=11
	
	  [<section_to_copy_inf>]
	  <filename>.inf
	  <optional_file_name>.inf
	
	  [<section_to_copy_vxd>]
	  <filename>.vxd
	
	  NOTE: <optional_file_name> is the name of the second .inf file if the
	  device is a multifunction adapter. Generally, there is an .inf file for the
	  network adapter driver, and one for the other device (usually a modem). If
	  the PCMCIA device is not a multifunction device, this line is not necessary.
	
	  During Setup, the temporary folder created by Setup is removed after the first
	  reboot, along with the files necessary to run the PCMCIA adapter that were
	  initially copied during setup. The entries listed above ensure that the
	  driver and .inf files are copied during the file- copy phase of Setup and
	  placed in the correct folders as specified in the [DestinationDirs] folder
	  setting.
	
	  For more information about the destination folder values, see appendix C,
	  pages 1166-1167, of the Windows 95 Resource Kit.
	
	8. Add the following section and line to the file. This line starts the PCMCIA
	  wizard to detect the PCMCIA sockets and provide support for the PCMCIA
	  adapter:
	
	  [EnablePCMCIA.addreg]
	  HKLM,SOFTWARE\MICROSOFT\WINDOWS\CURRENTVERSION\RUNONCE\SETUP,"Enable
	  PCMCIA",,"rundll sysdm.cpl,EnablePCMCIA_RunDLL"
	
	  NOTE: This line should be typed as a single line. It has been wrapped in this
	  article for readability purposes.
	
	9. In the [Install] section, create these entries:
	
	  AddReg=EnablePCMCIA.AddReg
	  CopyFiles=<section_to_copy_vxd>, <section_to_copy_inf>
	
	  NOTE: The first entry tells Setup to run the section added in step 8. The
	  second entry tells Setup to run the sections added in step 7.
	
	10. Run Windows 95 Setup.
	
	The PCMCIA adapter should be detected automatically as one of the final steps in
	Setup and the drivers loaded automatically from the hard disk as outlined in the
	.INF file's instructions.
	
	Additional query words: automate pccard oem nic
	
	======================================================================
	Keywords          : kbhw kbsetup win95 kbHardware 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : WINDOWS:95
	
	=============================================================================
	

{% endraw %}
