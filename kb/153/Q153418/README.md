---
layout: page
title: "Q153418: PRB: Error Caused By 68K EXE Created by Visual FoxPro Mac"
permalink: /kb/153/Q153418/
---

## Q153418: PRB: Error Caused By 68K EXE Created by Visual FoxPro Mac

{% raw %}

	Article: Q153418
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:3.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following error message is returned when a particular code sequence is
	compiled to a 68K .exe file:
	
	  Sorry,a system error occurred. "VFP Support Library 68K" error type 11.
	  Restart
	
	The code works correctly when run as a .prg file or an .app file.
	
	STATUS
	======
	
	Microsoft is researching this behavior and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	The following code when put in a program, added to a project, and compiled to a
	68K .exe file will cause errors that differ depending on the system's software
	and type of computer:
	
	     SET TALK OFF   && without this line it works
	     SET PRINTER ON && without this line it works
	     mMain=0
	
	     @  3,5 GET mMain  FUNCTION '*RT A'
	     * TO SEE THE ERROR,CLICK ON THE RADIO BUTTON
	     READ
	     CLEAR && without this line it works
	
	     SET PRINTER TO "STOX1A.TXT" && without this line it works
	
	     ** this could be virtually any SQL SELECT statement
	
	     SELECT DISTINCT BMASTER.SITEID;
	        FROM BMASTER, SITE;
	        WHERE SITE.SITEID = BMASTER.SITEID;
	        INTO ARRAY aSTUDY
	
	     WAIT WINDOW STR(ALEN(aSTUDY,1)) NOWAIT
	
	Additional query words: VFoxMac
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac
	Version           : MACINTOSH:3.0b
	
	=============================================================================
	

{% endraw %}
