---
layout: page
title: "Q131773: INFO: Setting Compare to Time Increases Speed of GET Command"
permalink: /kb/131/Q131773/
---

## Q131773: INFO: Setting Compare to Time Increases Speed of GET Command

{% raw %}

	Article: Q131773
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe600 kbSSafe310 kbSSafe304
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	- Microsoft Visual SourceSafe, 16-bit, for Windows, version 4.0 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0 
	- Microsoft SourceSafe for MS-DOS, versions 3.04, 3.1 
	- Microsoft SourceSafe for Windows, versions 3.04, 3.1 
	- Microsoft SourceSafe for Windows NT, versions 3.04, 3.1 
	- Microsoft SourceSafe for Macintosh, versions 3.04, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By setting Compare to Time, you can increase the speed of the Get command. This
	may, however, provide unexpected results unless you are aware of the way
	SourceSafe compares the time.
	
	MORE INFORMATION
	================
	
	SourceSafe compares the time with the Modification time of the file. Because of
	this, Compare = Time will only work correctly if SetTime = Mod.
	
	For instance, if SetTime = Current (the default), the local file will have the
	date of when the GET command was executed. Reissuing the GET will always cause
	SourceSafe to determine the files do not match. Similar behavior will occur if
	SetTime = Update.
	
	When using Compare = Time, the best behavior will occur with SetTime = Mod.
	However, for more reliable results, set Compare to Full or Checksum.
	
	For more information on how to improve the performance of a Get command by using
	the Compare to Checksum setting, please see the following article in the
	Microsoft Knowledge Base.
	
	  Q131772 Setting Compare to Checksum Increases Speed of GET Command
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe600 kbSSafe310 kbSSafe304 
	Technology        : kbHWMAC kbOSMAC kbSSafeSearch kbAudDeveloper kbZNotKeyword2 kbZNotKeyword3 kbSSafe304 kbSSafe304DOS kbSSafe310 kbSSafe310DOS kbSSafe304Mac kbSSafe310Mac kbSSafe600 kbSSafe400 kbSSafe500 kbSSafe16bitSearch kbSSafe32bitSearch kbSSafe304NT kbSSafe310NT
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
