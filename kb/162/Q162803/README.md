---
layout: page
title: "Q162803: Sound Not Functioning on NEC Versa 4050 Notebook with Modem"
permalink: /kb/162/Q162803/
---

## Q162803: Sound Not Functioning on NEC Versa 4050 Notebook with Modem

{% raw %}

	Article: Q162803
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The embedded ESS688 sound chip on NEC Versa 4050 notebook computer running
	Microsoft Windows NT 4.0 will not function properly when you use a PCMCIA (PC
	Card) modem. As soon as the modem is removed and the system restarted, the sound
	chip functions properly.
	
	NOTE: The NEC versa 4050C is not currently supported for use with Microsoft
	Windows NT 4.0. Please refer to the Windows NT 4.0 Hardware Compatibilty List
	(HCL) included with your documentation for supported hardware.
	
	An updated Hardware Compatibility List is available at the Microsoft Web site:
	http://www.microsoft.com.
	
	CAUSE
	=====
	
	If all other causes are eliminated, for example, IRQ or I/O conflicts, ESS
	driver not installed properly, sound not enabled in the system BIOS (see Other
	Troubleshooting Steps later in this article) there are three other settings in
	the NEC Versa system BIOS that you need to configure properly.
	
	RESOLUTION
	==========
	
	Turn on the NEC Versa, go into the system BIOS routine and make sure the
	following options have these settings:
	
	- Infrared Port: set to REAR
	
	- Serial Ports: set to ENABLED
	
	- Infrared/Serial Ports: set to RECONFIGUREABLE
	
	Save these settings and exit the BIOS utility. Turn off the notebook, insert the
	PC Card modem, turn on the notebook, and start Microsoft Windows NT 4.0. If the
	modem and sound devices are configured properly (see Other Troubleshooting Steps
	to verify or change settings), the sound chip and the modem should now function
	properly.
	
	Other Troubleshooting Steps:
	----------------------------
	
	1. In the system BIOS, make sure that the sound chip is enabled.
	
	2. In Windows NT, make sure that the ESS688 driver is installed.
	
	3. If the driver is not installed, run the Multimedia tool in Control Panel.
	  Click the Drivers tab, click Audio Devices, click Add, then select Unlisted
	  or Updated Driver. Click OK, enter the path to the driver, click OK, and
	  select ES688/ES1688/ES1788 AudioDrive 2.00.04 from the driver list. Click OK,
	  supply non-conflicting I/O Address, IRQ, and a DMA Level (most often the
	  defaults are acceptable - see step #7 for verifying available settings). For
	  example, the system on which this article is based has audio settings of
	  IRQ=7, IO=220, and DMA=1. The COM3 Port settings are IRQ=4 and IO=3E8.
	
	4. In the Devices tool in Control Panel, verify that the AUDDRV is set for
	  Automatic and is started after the driver is installed and the system has
	  been restarted.
	
	5. Verify that Audrive.sys is located in the %Systemroot%\System32\Drivers
	  folder and has a file size of 62 KB, and is dated 5/13/96 or later.
	
	6. In the Modems tool in Control Panel, verify the Modem settings. Look at the
	  Attached To field and identify which COM port the modem is using. The
	  following table indicates the default IRQ and I/O values used by specific COM
	  port settings.
	
	  When possible use standard settings for COM ports:
	
	     SERIAL 1   COM1:  I/O Address = 3F8h   IRQ = 4
	     SERIAL 2   COM2:  I/O Address = 2F8h   IRQ = 3
	     SERIAL 3   COM3:  I/O Address = 3E8h,  IRQ = 4
	     SERIAL 4   COM4:  I/O Address = 2E8h,  IRQ = 3
	
	  Regardless of whether the modem is using the default settings (this can be
	  confirmed in the Advanced Ports tools in Control indicated by the table, make
	  sure the sound driver settings do not conflict. If they do, adjust the sound
	  driver to use different settings.
	
	  If the modem is using the default settings specified in the preceding Table,
	  you need to ensure that the modem and sound driver settings do not conflict.
	  To check the modem default settings, use the Advanced Ports tool in Control
	  Panel.
	
	7. Verify which IRQs and I/O addresses are currently in use (with the modem
	  installed) by running Microsoft Windows NT Diagnostics in the Administrative
	  Tools group and clicking the Resources tab; check both IRQ and I/O ports.
	
	8. If the sound driver resource settings conflict with devices other than a
	  configured COM port (for example, Network adapter), identify available IRQ
	  and I/O resources and modify either the sound driver or other adapter to use
	  those available resources, eliminating any conflicts.
	
	9. Make sure that the PC Card slots are enabled. Try the modem in the other
	  slot.
	
	10. Try a different, supported PC Card modem.
	
	11. If this is a non-HCL system (not on the Microsoft Windows NT 4.0 Hardware
	  Compatibility List), try a supported notebook or contact your hardware
	  vendor.
	
	MORE INFORMATION
	================
	
	The NEC products included here are manufactured by NEC Corp., a vendor
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
