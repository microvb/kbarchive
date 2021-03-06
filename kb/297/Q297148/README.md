---
layout: page
title: "Q297148: Costing Errors For Dial-up Networking And Internet Explorer"
permalink: /kb/297/Q297148/
---

## Q297148: Costing Errors For Dial-up Networking And Internet Explorer

{% raw %}

	Article: Q297148
	Product(s): The Microsoft Network
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	  Error Message: Internet Explorer costing failed
	
	  Error Message: Dial-up Networking costing failed
	
	CAUSE
	=====
	
	When MSN Explorer checks for available disk space, it runs Internet Explorer
	Setup in "costing mode" to find out how much space is necessary. This failure
	occurs when the "costing mode" Setup does not complete successfully.
	
	When Dial-up Networking is installed but needs to be configured, the Dial-up
	Networking costing failed error appears. This issue typically occurs on
	non-Windows 95 machines.
	
	STATUS
	======
	
	To resolve the Internet Explorer costing issue
	
	1. Set up a manual dial-up connection if you do not already have a method for
	  connecting to the Internet.
	
	2. Go http://www.microsoft.com/windows/ie/ to download the latest version of
	  Internet Explorer.
	  Note: If you have an MSN Explorer CD, run the Internet Explorer Setup
	  separately, following the steps below.
	  Note: It is recommended that you delete the dial-up connecition file you
	  created manually before you run MSN Explorer Setup again.
	
	3. Right-click the Internet Explorer icon, click Properties, click the
	  Connections tab, select the connection you just created, and then click the
	  Remove button.
	  The manually created connection is now removed.
	
	4. After you have installed Internet Explorer, run MSN Explorer Setup again.
	
	To run the Internet Explorer Setup separately
	
	1. Insert the MSN Explorer CD in to the CD-ROM drive.
	  Note: If auto-run is running and causes MSN Explorer Setup to begin, exit
	  Setup by clicking the x in the upper-right corner.
	
	2. On the desktop, double-click the My Computer icon.
	
	3. Right-click the icon for your CD-ROM drive (usually D:, look for the MSN
	  Butterfly logo), and then click Open.
	
	4. Double-click the MSN folder, and then double-click the Internet Explorer
	  folder.
	
	5. Double-click the Internet Explorer 5 Setup icon to run the Internet Explorer
	  Setup.
	
	6. After the Internet Explorer setup is complete, run the MSN Explorer Setup.
	
	To resolve the Dial-up Networking costing issue
	
	1. Insert the Windows CD in to the CD-ROM drive. Note: If auto-run is running
	  and causes MSN Explorer Setup to begin, exit Setup by clicking the x in the
	  upper-right corner.
	
	2. Click Start, point to Settings, and then click Control Panel.
	
	3. Double-click Add/Remove Programs.
	
	4. Click the Windows Setup tab.
	
	5. Double-click Communications.
	
	6. Clear the box next to Dial-up Networking, and then click OK.
	
	7. Click Apply.
	
	8. Shut down and restart your computer.
	
	9. Click Start, point to Settings, and then click Control Panel.
	
	10. Double-click Add/Remove Programs.
	
	11. Click the Windows Setup tab.
	
	12. Double-click Communications.
	
	13. Select Dial-up Networking, click OK, and then click Apply.
	
	14. Shut down and restart your computer.
	
	15. Run MSN Explorer Setup again.
	
	MORE INFORMATION
	================
	
	
	Additional query words: kbimu; MSN Explorer
	
	======================================================================
	Keywords          :  
	Technology        : kbMSNSearch kbMSN600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
