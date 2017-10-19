---
layout: page
title: "Q311212: SMS: Missing Advertisement Status Messages"
permalink: /kb/311/Q311212/
---

## Q311212: SMS: Missing Advertisement Status Messages

	Article: Q311212
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3,2.0 SP4
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms120 kbsms120bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3, 2.0 SP4 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Some advertisement status messages from client computers may not be returned to
	the SMS database and Status Manager may sporadically delete status message files
	and log errors stating that the files are in use and damaged. If you experience
	this problem, you can view the log entries that are similar to the following log
	entries in the Statmgr.log file:
	
	  ERROR: Could not open file
	  "C:\SMS\inboxes\statmgr.box\statmsgs\IBNQWXY4.SVF", the file is assumed to be
	  corrupt. The operating system reported error 5: Access is denied. Deleted
	  corrupt file "C:\SMS\inboxes\statmgr.box\statmsgs\IBNQWXY4.SVF".
	
	  -or-
	
	  ERROR: Could not open file
	  "C:\SMS\inboxes\statmgr.box\statmsgs\IUSH4YZ5.SVF", the file is assumed to be
	  corrupt. The operating system reported error 32: The process cannot access
	  the file because it is being used by another process. ERROR: Could not delete
	  corrupt file "C:\SMS\inboxes\statmgr.box\statmsgs\IUSH4YZ5.SVF". The
	  operating system reported error 32: The process cannot access the file
	  because it is being used by another process.
	
	Similar problems with other components may also occur. View the following
	Microsoft Knowledge Base article for information about similar symptoms when you
	use the Software Inventory Processor component:
	
	  Q303279 SMS: Software Inventory Processor Has a Critical Status
	
	CAUSE
	=====
	
	This problem occurs when Inbox Manager Assistant (SMS_INBOX_MANAGER_ASSISTANT)
	copies a file from a Client Access Point (CAP) to the site server because Inbox
	Manager Assistant uses the file's original file extension. If the file is large
	or if the CAP-to-site server link is slow, the receiving SMS component (for
	example, Status Manager) can start processing the file before it is completely
	copied.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server (SMS) service
	pack that contains this fix.
	
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
	
	The English-language post-Service Pack 3 (SP3) version of this fix should have
	the following file attributes or later:
	
	  Date         Time    Version        Size     File name     Platform
	  -------------------------------------------------------------------
	  01-Mar-2001  01:30p  2.0.1493.3206  38,784   Inboxast.dll  Intel
	  01-Mar-2001  01:30p  2.0.1493.3206  107,920  Inboxmgr.dll  Intel
	  01-Mar-2001  01:30p  2.0.1493.3206  61,200   Inboxast.dll  Alpha
	  01-Mar-2001  01:30p  2.0.1493.3206  173,328  Inboxmgr.dll  Alpha
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	After you apply this hotfix, Inbox Manager Assistant copies every file from a CAP
	to the appropriate site server Inbox by using a .tmp file extension. After the
	file is copied to the Inbox, it is renamed with the correct file extension,
	which signals the receiving SMS component to process the file.
	
	
	How to Install the Hotfix
	-------------------------
	
	Install this hotfix on all primary and secondary site servers. To install the
	hotfix, use one of the following methods.
	
	How to Use the Hotfix Installer:
	
	NOTE: Use this method only on Intel-based computers.
	
	To use the hotfix installer:
	
	1. Create a folder in a location that is accessible to your SMS site servers.
	
	2. Copy the update file (Q311212.exe) and platform folders to the new folder.
	  The update file must be located one folder above the platform folders.
	
	3. From each of the primary and secondary SMS site servers in your environment,
	  log on to your site server by using an account with administrative
	  privileges.
	
	4. Quit the SMS Administrator console if it is running.
	
	5. Run Q311212.exe and follow the directions in the wizard.
	
	How to Manually Install the Hotfix:
	
	To manually install the hotfix:
	
	1. Create a folder in a location that is accessible to your SMS site servers.
	
	2. Copy the platform folders that contain the hotfix files to the new folder.
	
	3. From each of the primary and secondary SMS site servers in your environment,
	  log on to your site server by using an account with administrative
	  privileges.
	
	4. Quit the SMS Administrator console if it is running.
	
	5. Stop all SMS services.
	
	6. Replace the Inboxast.dll file in the
	  <Sms_root_folder>\Bin\<Platform> folder with the version of the
	  file that you obtain from the hotfix.
	
	7. Replace the Inboxmgr.dll file in the
	  <Sms_root_folder>\Bin\<Platform> folder with the version of the
	  file that you obtain from the hotfix.
	
	8. Perform a site reset for the new Inboxast.dll and Inboxmgr.dll files that
	  need to be installed on the CAPs. To perform a site reset, run the SMS Setup
	  program and follow the prompts.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	the Systems Management Server 2.0 Service Pack 4 Hotfix Rollup Package (HRP).
	
	For additional information about the SMS 2.0 SP4 HRP, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q323206 SMS: List of Bugs Fixed in the Systems Management Server 2.0 SP4 HRP
	
	MORE INFORMATION
	================
	
	The fix that is discussed in this article also resolves the problem that is
	discussed in the following Microsoft Knowledge Base article:
	
	  Q303279 SMS: Software Inventory Processor Has a Critical Status
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3 kbSMS200SP4
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3,2.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	