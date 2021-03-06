---
layout: page
title: "Q262667: FIX: Wrong Result Using RtlMoveMemory to Copy Nested UDT"
permalink: /kb/262/Q262667/
---

## Q262667: FIX: Wrong Result Using RtlMoveMemory to Copy Nested UDT

{% raw %}

	Article: Q262667
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbAPI kbSDKWin32 kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix
	Last Modified: 20-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you copy a nested user defined type (UDT) with a fixed-length String array to
	a fixed-length String by using a RtlMoveMemory API call, you may not get the
	right result.
	
	RESOLUTION
	==========
	
	This problem can be solved in one of two ways:
	
	- Install the latest service pack for Visual Studio 6.0.
	
	- Use an intermediate byte array. That is, first copy the UDT to a byte array
	  and then assign the byte array to the fixed-length String.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in the next service pack for
	Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	You can download the latest Visual Studio service pack from the following
	Microsoft Web site:
	
	  Visual Studio Product Updates
	  (http://msdn.microsoft.com/vstudio/downloads/updates.asp)
	
	MORE INFORMATION
	================
	
	WARNING: One or more of the following functions are discussed in this article;
	VarPrt, VarPtrArray, VarPtrStringArray, StrPtr, ObjPtr. These functions are not
	supported by Microsoft Technical Support. They are not documented in the Visual
	Basic documentation and are provided in this Knowledge Base article "as is".
	Microsoft does not guarantee that they will be available in future releases of
	Visual Basic.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is added by default.
	
	2. Place a CommandButton control on Form1. Command1 is added by default.
	
	3. Paste the following code into Form1's code section:
	
	  Option Explicit
	
	  Private Sub Command1_Click()
	    Module1.main
	  End Sub
	
	  Private Sub Form_Load()
	    Command1.Caption = "Test"
	  End Sub
	
	4. From the Project menu, click Add Module to add a new module, Module1, to
	  Project1.
	
	5. Paste the following code into Module1:
	
	  Option Explicit
	
	  Const CASIZE = 14
	
	  Type WinDataType
	     ISBalance(1) As String * 1
	     ISRebate     As String * 1    '
	     Filler       As String * 1
	  End Type
	
	  Type WinIODataType
	    Filler       As String * 2
	    Data         As WinDataType
	  End Type
	
	  Type WinComDataType
	    Filler       As String * 2
	    Inp          As WinIODataType
	    Out          As WinIODataType
	  End Type
	
	  Public Declare Sub CopyMemory Lib "kernel32" Alias "RtlMoveMemory" _
	  (Destination As Any, Source As Any, ByVal Length As Long)
	
	  Dim IWIN As WinComDataType
	
	  Sub main()
	    Dim CommonREM As String * CASIZE
	    Dim y(CASIZE * 2 - 1) As Byte
	      
	    IWIN.Inp.Data.ISBalance(0) = "V"
	    IWIN.Inp.Data.ISBalance(1) = "X"
	    IWIN.Inp.Data.ISRebate = "R"
	    IWIN.Inp.Data.Filler = "F"
	   
	    ' ISBalance now starts at position 5 in the IWIN structure:
	    Debug.Print "Mid$(CommonREM, 5, 4) before MoveMemory = " _
	        & Mid$(CommonREM, 5, 4)
	   
	    CopyMemory ByVal CommonREM, IWIN, CASIZE
	
	    Debug.Print "Mid$(CommonREM, 5, 4) after MoveMemory = " _
	        & Mid$(CommonREM, 5, 4)
	        
	  End Sub
	
	6. From the View menu, click Immediate Window to open the Immediate window.
	
	7. Press the F5 key to run the project.
	
	8. Click the Test button.
	
	9. In the Immediate window, you should see the following:
	
	Mid$(CommonREM, 5, 4) before MoveMemory =     
	Mid$(CommonREM, 5, 4) after MoveMemory = VXXF
	
	10. This result is incorrect. The correct result should be:
	
	Mid$(CommonREM, 5, 6) after MoveMemory = VXRF
	
	Look at the code in the Main subroutine in Module1, and note that the correct
	result is "VXRF."
	
	Workaround
	----------
	
	If you do not install Visual Studio 6.0 Service Pack 4, then do the following:
	
	1. In the preceding project, replace the code in Module1 with the following:
	
	  Option Explicit
	
	  Const CASIZE = 14
	
	  Type WinDataType
	     ISBalance(1) As String * 1
	     ISRebate     As String * 1    '
	     Filler       As String * 1
	  End Type
	
	  Type WinIODataType
	    Filler       As String * 2
	    Data         As WinDataType
	  End Type
	
	  Type WinComDataType
	    Filler       As String * 2
	    Inp          As WinIODataType
	    Out          As WinIODataType
	  End Type
	
	  Public Declare Sub CopyMemory Lib "kernel32" Alias "RtlMoveMemory" _
	  (Destination As Any, Source As Any, ByVal Length As Long)
	
	  Dim IWIN As WinComDataType
	
	  Sub main()
	    Dim CommonREM As String * CASIZE
	    Dim y(CASIZE * 2 - 1) As Byte
	
	    ' ISBalance is starting from position 5
	    IWIN.Inp.Data.ISBalance(0) = "V"
	    IWIN.Inp.Data.ISBalance(1) = "X"
	    IWIN.Inp.Data.ISRebate = "R"
	    IWIN.Inp.Data.Filler = "F"
	     
	    ' ISBalance now starts at position 5 in the IWIN structure:
	    Debug.Print "Mid$(CommonREM, 5, 4) before MoveMemory = " _
	        & Mid$(CommonREM, 5, 4)
	
	    CopyMemory ByVal VarPtr(y(0)), ByVal VarPtr(IWIN), CASIZE * 2
	    CommonREM = y
	
	    Debug.Print "Mid$(CommonREM, 5, 4) after MoveMemory = " _
	        & Mid$(CommonREM, 5, 4)
	  End Sub
	
	2. From the View menu, click Immediate Window to open the Immediate window.
	
	3. Press F5 to run the project.
	
	4. Click the Test button.
	
	5. In the Immediate window, note the following, which is the correct result:
	
	Mid$(CommonREM, 5, 4) before MoveMemory =     
	Mid$(CommonREM, 5, 4) after MoveMemory = VXRF
	
	REFERENCES
	==========
	
	For additional information on the VarPtr function, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q199824 HOWTO: Get the Address of Variables in Visual Basic
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbSDKWin32 kbVBp kbVBp600bug kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
