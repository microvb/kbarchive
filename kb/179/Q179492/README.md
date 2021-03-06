---
layout: page
title: "Q179492: PRB: Error Message &quot;MSVBVM50.dll Not Found&quot;"
permalink: /kb/179/Q179492/
---

## Q179492: PRB: Error Message &quot;MSVBVM50.dll Not Found&quot;

{% raw %}

	Article: Q179492
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbsetup kbVBp kbVBp500 kbGrpDSVB kbDSupport
	Last Modified: 10-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An attempt to install a Visual Basic program results in the following error
	message:
	
	  A required file, MSVBVM50.dll, was not found.
	
	CAUSE
	=====
	
	The Microsoft Visual Basic Virtual Machine run time was not properly installed
	on the computer. File corruption or failure of a third-party application to
	install this required run time during setup may also cause this error message.
	
	RESOLUTION
	==========
	
	Download and run MSVBVM50.EXE from the Microsoft Download Center. Run the
	executable file after download. This file installs the correct Visual Basic
	Virtual Machine and associated files. This should eliminate the error Message.
	See the "References" section of this article for more information.
	
	MORE INFORMATION
	================
	
	Programs written in Microsoft Visual Basic require that the client computer have
	a local installation of the Microsoft Visual Basic Virtual Machine run time
	engine. In some situations, this file was not distributed or installed correctly
	by a third-party software package or has become corrupted. While the Microsoft
	Visual Basic 5.0 Service Pack 2 updated this Virtual Machine run time engine for
	developers, a client or customer computer may not have the most recent version
	installed.
	
	REFERENCES
	==========
	
	For additional information about MSVBVM50.EXE, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q180071 FILE: MSVBVM50.EXE Installs Visual Basic 5.0 Run-Time Files
	
	Additional query words: setup installation msvbvm50
	
	======================================================================
	Keywords          : kbsetup kbVBp kbVBp500 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Version           : :5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
