---
layout: page
title: "Q253197: SMS: Run-Time Error When Advertising MFC-Based Package (ICP Vers"
permalink: /kb/253/Q253197/
---

## Q253197: SMS: Run-Time Error When Advertising MFC-Based Package (ICP Vers

{% raw %}

	Article: Q253197
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kberrmsg kbsms120 kbsms120bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you distribute software to a Systems Management Server (SMS) client, the
	following error message may be displayed when the advertisement runs:
	
	  Runtime ERROR!
	  Program \\server\smspkgd$\opl00003\mfctest.exe
	  abnormal program termination
	
	You may also see the following entry in the Smsapm32.log file:
	
	  SCHED DATA : Attempting to execute
	  \\SMSD4L8PDCUS\SMSPKGC$\RS100006\mfctest.exe' (SERVICE context)
	  SCHED DATA : Command line "\\SMSD4L8PDCUS\SMSPKGC$\RS100006\mfctest.exe" CWD
	  "\\SMSD4L8PDCUS\SMSPKGC$\RS100006\"
	
	  SCHED DATA : Return code = 0x3; The system cannot find the path specified.~~;
	  Program '\\SMSD4L8PDCUS\SMSPKGC$\RS100006\mfctest.exe' terminated with exit
	  code = 3.
	
	On the client, the program (the .exe file) may have a status of "Started" in Task
	Manager, even though it is no longer active.
	
	CAUSE
	=====
	
	This behavior can occur if the Setup file that is used by the advertised program
	uses the Msvcrt.dll run-time library file from Microsoft Visual C++, and if one
	of the following options is enabled on the Environment tab in the program
	properties:
	
	- Run with administrative rights
	
	- Use Windows NT client software installation account
	
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
	
	The International Client Pack 5 (ICP5) version of this fix should have the
	following file attributes or later:
	
	  Date      Time    Version           Size    File name    Platform
	  -----------------------------------------------------------------
	  11/16/99  11:03pm 2.00.1380.1077    233,312 Abnwcli.dll  I386
	  02/14/00  05:19pm                   367,800 Apasetup.exe I386
	  10/21/99  01:56pm 2.00.1380.1060    259,936 Bindclin.dll I386
	  11/10/99  10:42pm 2.00.1380.1072    160,080 Ccim32.dll   I386
	  04/03/00  05:48pm                 1,328,039 Ccmcore.exe  I386
	  04/03/00  05:47pm                 8,555,969 Clicore.exe  I386
	  11/03/99  09:01pm 2.00.1380.1063     76,656 Clisvcl.exe  I386
	  10/01/99  02:22pm 2.00.1380.1051    157,536 Falclin.dll  I386
	  10/27/99  06:33pm 2.00.1380.1063    335,712 Mslmclin.dll I386
	  11/11/99  05:01am 2.00.1380.1060    269,664 Ndsclin.dll  I386
	  11/30/99  04:59pm 2.00.1380.1082     75,120 Progrm32.dll I386
	  11/23/99  01:23pm 2.00.1380.1081    209,264 Smsapm32.exe I386
	  02/11/00  09:44pm 2.00.1380.1802         67 Compver.ini  I386
	
	  11/16/99  10:39pm 2.00.1380.1077    410,896 Abnwcli.dll  Alpha
	  02/14/00  03:25pm                   630,099 Apasetup.exe Alpha
	  11/10/99  10:42pm 2.00.1380.1072    255,760 Ccim32.dll   Alpha
	  04/03/00  03:51pm                 1,935,579 Ccmcore.exe  Alpha
	  04/03/00  03:50pm                11,616,822 Clicore.exe  Alpha
	  11/03/99  09:00pm 2.00.1380.1063    110,352 Clisvcl.exe  Alpha
	  10/01/99  02:22pm 2.00.1380.1051    285,968 Falclin.dll  Alpha
	  10/27/99  06:33pm 2.00.1380.1063    575,760 Mslmclin.dll Alpha
	  11/30/99  05:00pm 2.00.1380.1082    122,640 Progrm32.dll Alpha
	  11/23/99  01:24pm 2.00.1380.1081    279,824 Smsapm32.exe Alpha
	  02/11/00  09:44pm 2.00.1380.1802         67 Compver.ini  Alpha
	
	NOTE: Because of file dependencies, the most recent hotfix or feature that
	contains the above files may also contain additional files.
	
	
	
	WORKAROUND
	==========
	
	To work around this behavior, do not enable the Run with administrative rights
	or "Use Windows NT client software installation account" option.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 2.0.
	
	MORE INFORMATION
	================
	
	To install the hotfix, use either of the following methods.
	
	Method 1: Using the Hotfix Installer
	------------------------------------
	
	NOTE: This method only works on I386-based computers.
	
	1. Copy the hotfix folder structure to a share on your network. The Q253197.exe
	  file is a Microsoft Windows Installer file that updates specific files on
	  your site server.
	
	2. Log on to your site server using an account with administrative privileges.
	
	3. On the site server, close the SMS Administrator console.
	
	4. Start Q253197.exe and follow the directions in the wizard. You can run the
	  program in Quiet mode by using the /s switch.
	
	Method 2: Manual Installation
	-----------------------------
	
	NOTE: You can use this method for both I386-based and Alpha-based site servers.
	
	1. Copy the hotfix folder structure to a local subfolder on your site server or
	  to a share on your network.
	
	2. Close the SMS Administrator console and stop all SMS services.
	
	3. Copy the following files from the hotfix I386 folder into the
	  <Sms_root_folder>\Sms\Bin\I386 folder:
	
	  Abnwcli.dll
	  Bindclin.dll
	  Ccim32.dll
	  Clisvcl.exe
	  Falclin.dll
	  Mslmclin.dll
	  Ndsclin.dll
	  Smsapm32.exe
	
	4. If Alpha-based support is enabled on the primary site, copy the following
	  files from the hotfix Alpha folder into the
	  <Sms_root_folder>\Sms\Bin\Alpha folder:
	
	  Abnwcli.dll
	  Ccim32.dll
	  Clisvcl.exe
	  Falclin.dll
	  Mslmclin.dll
	  Smsapm32.exe
	
	5. Copy the following files from the appropriate platform subfolder into the
	  <Sms_root_folder>\Sms\Inboxes\Clicomp.src\Base\<platform >folder:
	
	  Ccmcore.exe
	  Clicore.exe
	
	6. Copy the Apasetup.exe file from the appropriate platform subfolder into the
	  <Sms_root_folder>\Sms\Inboxes\Clicomp.src\Smsapm32\<platform>
	  folder.
	
	7. Copy the updated Compver.ini file to the
	  <Sms_root_folder>\Inboxes\Clicomp.src\Smsapm32 folder.
	
	8. Copy the updated Compver.ini file to the
	  <Sms_root_folder>\Inboxes\Clicomp.src\Base folder.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q24289 Run-Time Error When Advertising MFC-Based Package (English Version)
	
	Additional query words: prodsms apm mfc runtime
	
	======================================================================
	Keywords          : kberrmsg kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
