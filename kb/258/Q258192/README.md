---
layout: page
title: "Q258192: PRB: Errors Recompiling ActiveX Component w/ Binary Compability"
permalink: /kb/258/Q258192/
---

## Q258192: PRB: Errors Recompiling ActiveX Component w/ Binary Compability

{% raw %}

	Article: Q258192
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbActiveX kbCtrlCreate kbDLL kbInprocSvr kbLocalSvr kbVBp kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A run-time error is raised when an ActiveX component is recompiling in Visual
	Basic, as follows.
	
	When recompiling a Visual Basic ActiveX EXE or ActiveX DLL, the client
	application may display the following error message:
	
	  Run-Time Error '430':
	
	  Class Does not support Automation or does not support expected interface
	
	When a Visual Basic UserControl is recompiled, the client application may display
	the following error message:
	
	  Failed to activate control 'VB.UserControl'. This control may be incompatible
	  with your application. Make sure that you are using the version of the
	  control that was provided with your application.
	
	CAUSE
	=====
	
	These errors occur if Public Methods or Properties are added to the ActiveX
	component after making a copy for Binary Compatibility and then recompiling the
	component a second time.
	
	When new Public Methods or Properties are added to an ActiveX .exe, ActiveX .dll,
	or a UserControl with Binary Compatibility set, Visual Basic adds a new
	Interface to the second version for new client applications to use, and creates
	a pointer from the old interface to the new Interface so that old clients
	continue to work.
	
	However, a problem occurs when a third version of this new ActiveX component is
	compiled without resetting the Binary Compatible file to the second version of
	the ActiveX .exe, .dll, or .ocx file. When this occurs, a new universally unique
	identifier (UUID) and Interface are generated and any client applications
	compiled against the second version fail.
	
	RESOLUTION
	==========
	
	Ensure that the Binary Compatibility is always set to the latest version of your
	ActiveX component, or a version that includes all Public Methods and Properties.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The following discussion uses an ActiveX .exe file as an example, but it should
	be noted that the behavior for Interfaces is the same for all three types of
	ActiveX components.
	
	When you first compile an ActiveX .exe, ActiveX .dll, or UserControl (for
	example, Server1.exe), Visual Basic creates an Interface for the Public Methods
	and Properties, as follows:
	
	+------------+
	| Interface1 | 
	+------------+
	| Method1    | 
	+------------+
	| Method2    | 
	+------------+
	| Method3    | 
	+------------+
	| Property1  | 
	+------------+
	| Property2  | 
	+------------+
	
	If a new Method is added to the existing ActiveX .exe and Binary Compatibility is
	set to Server1.exe, when the modified .exe is recompiled to Server2.exe, the
	Interface structure is as follows:
	
	+-------------------------------+
	| Interface1 | --> | Interface2 | 
	+-------------------------------+
	|            |     | Method1    | 
	+-------------------------------+
	|            |     | Method2    | 
	+-------------------------------+
	|            |     | Method3    | 
	+-------------------------------+
	|            |     | Property1  | 
	+-------------------------------+
	|            |     | Property2  | 
	+-------------------------------+
	|            |     | Method4    | 
	+-------------------------------+
	|            |     | Property3  | 
	+-------------------------------+
	
	Calls on Interface1 are redirected to the correct Method or Property on
	Interface2 for old clients. New clients automatically use Interface2.
	
	This mechanism is transparent to the user and needs no special coding on the
	client or the server.
	
	If the .exe is compiled again without changing the file reference for binary
	compatibility, (call it Server3.exe) then the following table is generated:
	
	+-------------------------------+
	| Interface1 | --> | Interface3 | 
	+-------------------------------+
	|            |     | Method1    | 
	+-------------------------------+
	|            |     | Method2    | 
	+-------------------------------+
	|            |     | Method3    | 
	+-------------------------------+
	|            |     | Property1  | 
	+-------------------------------+
	|            |     | Property2  | 
	+-------------------------------+
	|            |     | Method4    | 
	+-------------------------------+
	|            |     | Property3  | 
	+-------------------------------+
	
	Interface2 and Interface3 now have the same Methods but they are not the same
	interface because they do not have the same UUID. This means that Server2.exe
	and Server3.exe cannot be used interchangeably because they are not compatible
	with each other. They are, however, both compatible with Server1.exe and can be
	used with applications that are already compiled to use Server1.exe.
	
	REFERENCES
	==========
	
	  Q161137 HOWTO: Use Project and Binary Compatibility
	
	Additional query words: 430
	
	======================================================================
	Keywords          : kbActiveX kbCtrlCreate kbDLL kbInprocSvr kbLocalSvr kbVBp kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
