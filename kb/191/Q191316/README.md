---
layout: page
title: "Q191316: PRB: SET DATASESSION TO Fails From a Method of _Screen"
permalink: /kb/191/Q191316/
---

## Q191316: PRB: SET DATASESSION TO Fails From a Method of _Screen

{% raw %}

	Article: Q191316
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Attempting to set the data session of a form by calling the SET DATASESSION TO
	command from a method of _SCREEN fails.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a program that contains the following code:
	
	        CLEAR ALL
	        PUBLIC yy,Y,zz
	
	        * The target session we are trying to SET TO:
	        Y = CREATEOBJECT("zform")
	
	        * A separate custom object, which can set to that session:
	        zz = CREATEOBJECT("myobj")
	
	        * A form in another session, which can set to that session:
	        yy = CREATEOBJECT("zform2")
	
	        * A member of screen, which will show the problem:
	        _SCREEN.ADDOBJECT("z","myobj")
	
	        Y.SHOW()
	        yy.SHOW()
	
	        RETURN
	
	        DEFINE CLASS myobj AS CUSTOM
	
	           PROCEDURE SetToActiveSession
	              WAIT WINDOW TIMEOUT 1 ;
	              "current ;
	              session: "+STR(SET("datasession"))
	              SET DATASESSION TO ;
	              (_SCREEN.ACTIVEFORM.DATASESSIONID)
	              WAIT WINDOW "session we want: "+;
	              ALLTR(STR(_SCREEN.ACTIVEFORM.DATASESSIONID))+ ;
	              ", "+ CHR(13)+ ;
	              "session we got: "+ ;
	              ALLTR(STR(SET("DATASESSION"))) TIMEOUT 3
	           ENDPROC
	
	        ENDDEFINE
	
	        DEFINE CLASS zform AS FORM
	           DATASESSION = 2
	        ENDDEFINE
	
	        DEFINE CLASS zform2 AS zform
	           AUTOCENTER = .T.
	           ADD OBJECT z AS COMMANDBUTTON WITH ;
	           CAPTION="Push Me"
	           PROCEDURE  z.CLICK
	           WAIT WINDOW TIMEOUT 1 "current session: "+STR(SET("datasession"))
	           SET DATASESSION TO (Y.DATASESSIONID)
	           WAIT WINDOW "session we want: "+ ;
	           ALLTR(STR(Y.DATASESSIONID))+ ;
	           ", "+CHR(13)+ ;
	           "session we got: "+ ;
	           ALLTR(STR(SET("DATASESSION"))) TIMEOUT 1
	           ENDPROC
	        ENDDEFINE
	
	2. Run the program and press the command button. Notice the data session starts
	  out with a value of three (3) and changes to a value of two (2).
	
	3. Change the data session from the Command window by typing the following
	  command:
	
	  " zz.SetToActiveSession()" (without the quotation marks)
	
	  Notice the data session starts with a value of one (1) and successfully
	  changes to two (2).
	
	4. Attempt to change the data session from the Command window using a method of
	  the _SCREEN object by typing the following:
	
	  " _Screen.z.SetToActiveSession()" (without the quotation marks)
	
	  Calling the _SCREEN object does not allow you to change the data session to a
	  value of two (2). It remains a value of one (1).
	
	Additional query words: kbVFp500a kbVFp600 kbOOP
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
