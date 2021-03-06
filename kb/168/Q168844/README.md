---
layout: page
title: "Q168844: FIX: Undo Check Out Not Behaving as Expected"
permalink: /kb/168/Q168844/
---

## Q168844: FIX: Undo Check Out Not Behaving as Expected

{% raw %}

	Article: Q168844
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kbusage kbSSafe400 kbSSafe500 kbSSafe600fix
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe, 16-bit, for Windows, version 4.0 
	- Microsoft Visual SourceSafe, 32-bit, for Windows 4.0 
	- Microsoft Visual SourceSafe for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Undo Check Out command does not operate as expected if you have the Compare
	Files By option set to Time and the Set Date/Time on Local Files set to Current.
	
	CAUSE
	=====
	
	When you set Compare Files By to Time, the algorithm used to determine whether a
	Get should be performed is based on a comparison between the timestamp on the
	local copy of the file and the timestamp on the last check in for the file.
	
	If the timestamp on the last check in is more recent than the timestamp on the
	local file, Visual SourceSafe does the Get and overwrites the local copy of the
	file. If the timestamp on the local file is more recent than the timestamp on
	the last check in, Visual SourceSafe does not do the Get, and the local file is
	not replaced.
	
	RESOLUTION
	==========
	
	Do one of the following:
	
	- Set Compare Files By to CheckSum instead of Time.
	
	- Remove the local copy of the file, and then perform the Get/Check Out.
	
	STATUS
	======
	
	This behavior is by design. This problem was corrected in Visual SourceSafe
	version 6.0.
	
	MORE INFORMATION
	================
	
	If you perform an Undo Check Out with the above options set in Visual
	SourceSafe, unexpected results occur.
	
	For example, you have a file checked out and you have edited it. The local file
	(the one you are editing) has a more recent timestamp on it than the last
	checked in copy of the file. After you have edited and saved the file you decide
	you really do not want the changes you made, so you go back to SourceSafe and
	perform an Undo Check Out on the file. You get the warning message stating that
	all your changes will be lost if you perform an Undo Check Out. You click Yes
	and Visual SourceSafe does not copy the changes in the local file back to the
	server.
	
	When you Get or Check Out the file again, Visual SourceSafe sees that the
	timestamp on your local file is more recent than the timestamp on the last check
	in. Visual SourceSafe does not perform the Get, and the local file is not
	replaced. As a result, you see all the changes you thought you had discarded
	instead of the unaltered copy you thought you retrieved by performing the Get.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage kbSSafe400 kbSSafe500 kbSSafe600fix 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe400 kbSSafe500 kbSSafe16bitSearch kbSSafe32bitSearch
	Version           : WINDOWS:4.0,5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
