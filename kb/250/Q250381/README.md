---
layout: page
title: "Q250381: SMS: Package Share Comment Date Displays Year as 100"
permalink: /kb/250/Q250381/
---

## Q250381: SMS: Package Share Comment Date Displays Year as 100

{% raw %}

	Article: Q250381
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbsms120 kbsms120bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you create a new package share (SMS_PKGx) for a "Run Command on
	Workstation" package in the year 2000, the share comment is created with a date
	format of XX/XX/100.
	
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
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Time     Size     File name    Platform
	  -------------------------------------------------
	  01/26/00  8:13pm   254,912  Smsinst.dl_  Intel
	  01/26/00  8:15pm   481,552  Smsinst.dl_  Alpha
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	
	
	WORKAROUND
	==========
	
	This is a cosmetic issue only. There are no known problems caused by this issue.
	To work around this problem, modify the share comment and change the date format
	(XX/XX/00).
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	To install the hotfix, follow these steps on the Systems Management Server site
	server:
	
	1. Stop all SMS services.
	
	2. Quit all Systems Management Server programs (including the SMS Administrator
	  program, SMS Database Manager, and so on).
	
	3. Replace the Smsinst.dll file in the
	  <SMS_root>\Site.srv\<Platform>.bin folder with the hotfix
	  version. Rename Smsinst.dl_ to Smsinst.dll.
	
	4. Restart the SMS services.
	
	
	Additional query words: prodsms y2k sms_pkg share comment
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
