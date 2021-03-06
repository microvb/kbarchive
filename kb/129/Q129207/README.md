---
layout: page
title: "Q129207: PRB: &quot;Property Not Found&quot; Occurs When Running Form"
permalink: /kb/129/Q129207/
---

## Q129207: PRB: &quot;Property Not Found&quot; Occurs When Running Form

{% raw %}

	Article: Q129207
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 03-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following error message displays while you are running a form:
	
	  Property Not Found
	
	CAUSE
	=====
	
	The period (.) operator was used in conjunction with macro substitution to
	reference a property that contains the name of an object. Because the compiler
	recognizes the period as the macro terminator, it doesn't evaluate the remainder
	of the line that contains the property.
	
	WORKAROUND
	==========
	
	To work around this problem, add an additional period after the macro
	substitution. The first period terminates the macro and the second allows the
	compiler to reference the property.
	
	For example, to fix the problem, refer to the "Steps to Reproduce Behavior"
	section of this article, and replace the lines that use a single period to
	reference properties with the following lines of code:
	
	     This.&cOButton..Caption="Button"-cOldbNo && Originally used one period
	     This.&cOButton..Picture=''
	
	  *** ...
	
	     This.&cButton..Caption=""                && These lines are farther
	     This.&cButton..Picture='c:\vfp\fox.bmp'  && down in the example
	
	NOTE: Macro substitution can usually be replaced by the superior EVALUATE()
	function, but using EVALUATE() requires an additional line of code. In this
	example, program execution is faster and the amount of executable code generated
	by the compiler/linker is smaller. For example:
	
	Instead of:
	
	     This.&cOButton..Picture=''
	
	Use:
	
	     oRef=EVAL("THIS."+cOButton)
	     oRef.Picture=''
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	The following program displays a form that contains three buttons (Button1,
	Button2, and Button3). Macro substitution is used to modify the Picture and
	Caption properties of these objects.
	
	1. From the File menu, choose New. Select the Program option, and then choose
	  the New File button.
	
	2. Enter the following source code:
	
	     oMyForm = CREATEOBJECT("MyForm")
	     oMyForm.show
	     READ EVENTS
	
	     DEFINE CLASS MyForm AS FORM
	        nCurrentb=1
	
	        ADD OBJECT Button1 AS COMMANDBUTTON WITH ;
	          top=1,left=1,height=2,width=10,caption="",picture='c:\vfp\fox.bmp'
	
	        ADD OBJECT Button2 AS COMMANDBUTTON WITH ;
	          top=7,left=1,height=2,width=10
	
	        ADD OBJECT Button3 AS COMMANDBUTTON WITH ;
	          top=13,left=1,height=2,width=10
	
	        PROCEDURE Button1.Click
	          This.Parent.ChangeProp(1)
	        ENDPROC
	
	        PROCEDURE Button2.Click
	          This.Parent.ChangeProp(2)
	        ENDPROC
	
	        PROCEDURE Button3.Click
	          This.Parent.ChangeProp(3)
	        ENDPROC
	
	        PROCEDURE ChangeProp
	           PARAMETERS nNewbutton
	
	          cOldbNo=''
	          cNewbNo=''
	          cOButton=''
	          cButton=''
	
	           * Clear .bmp on old button
	           cOldbNo=ALLTRIM(STR(This.nCurrentb))
	           cOButton="Button"-cOldbNo
	           This.&cOButton.Caption="Button"-cOldbNo  && WILL NOT WORK
	           This.&cOButton.Picture=''                && WILL NOT WORK
	
	           * Display .bmp on new button
	           cNewbNo=ALLTRIM(STR(nNewbutton))
	           cButton="Button"-cNewbNo
	           This.&cButton.Caption=""                 && WILL NOT WORK
	           This.&cButton.Picture='c:\vfp\fox.bmp'   && WILL NOT WORK
	
	           This.nCurrentb=nNewbutton
	        ENDPROC
	     ENDDEFINE
	
	Additional query words: VFoxWin 3.00 akz
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
