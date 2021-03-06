---
layout: page
title: "Q234750: SMS: Pentium Processor Speed Incorrectly Reported"
permalink: /kb/234/Q234750/
---

## Q234750: SMS: Pentium Processor Speed Incorrectly Reported

{% raw %}

	Article: Q234750
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsms120 kbsms120bug kbInventorykbfixlist
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Systems Management Server client computers running Microsoft Windows NT may
	report Pentium processor speeds incorrectly. For example, a Pentium
	200-megahertz (MHz) processor may be reported as a 198-MHz or 199-MHz processor.
	
	CAUSE
	=====
	
	This issue occurs because the processor normalization code that determines the
	processor speed does not identify Pentium processors faster than 166 MHz.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English language version of this software update should have the following
	file attributes or later:
	
	  Date      Time     Size      File name      Platform
	  -----------------------------------------------------
	  06/10/99  12:55a   866,576   INV32CLI.exe   Alpha
	  06/10/99  12:56a   883,472   InvWin32.exe   Alpha
	  06/10/99  12:46a    19,584   GETCOMP.exe    x86
	  06/10/99  12:54a   283,104   INV32CLI.exe   x86
	  06/10/99  12:54a   296,368   INVWIN32.exe   x86
	  06/10/99  12:46a    14,588   OS2BIOS.exe    x86
	
	This hotfix should be applied on a Windows NT 4.0 Service Pack 4 site server. It
	does not work with Service Pack 3.
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	The value that Systems Management Server queries is located in the following
	registry key:
	
	  HKEY_LOCAL_MACHINE\HARDWARE\DESCRIPTION\System\CentralProcessor\0\~MHz
	
	When the speed is faster than 166 MHz (0xA6), the value is directly reported (no
	normalization).
	
	The hotfix adds support for 200, 233, 266 and 300-MHz Pentium, 166-MHz Pentium
	Pro and 450-MHz Pentium II versions.
	
	For 16-bit clients it adds support for 266 and 300-MHz Pentium, 166-MHz Pentium
	Pro and 450-MHz Pentium II cpu versions.
	
	To install the hotfix, follow these steps:
	
	  1. Stop the SMS Executive and the SMS Inventory Agent services on the site
	     server.
	
	  2. In the <SMS_root_directory>\Site.srv\<platform>.bin directory
	     on the site server, replace the file Invwin32.exe with the version
	     obtained from the hotfix.
	
	  3. In the <SMS_root_directory>\Site.srv\Maincfg.box\Client.src\x86.bin
	     directory on the site server, replace the Os2bios.exe, Inv32cli.exe,
	     Invwin32.exe and Getcomp.exe files with the versions obtained from the
	     hotfix.
	
	  4. In the
	     <SMS_root_directory>\Site.srv\Maincfg.box\Client.src\Alpha.bin
	     directory on the site server, replace the Inv32cli.exe and Invwin32.exe
	     files with the versions obtained from the hotfix.
	
	  5. Restart the SMS Executive and SMS Inventory Agent services on the site
	     server. Maintenance Manager will propagate the changed files to the logon
	     servers.
	
	To update the clients, either manually run Upgrade.bat on each client or click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q166771 SMS: How to Force Site-Wide Client Updates
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms120 kbsms120bug kbInventory kbfixlist
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
