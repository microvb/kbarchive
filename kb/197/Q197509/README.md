---
layout: page
title: "Q197509: XFOR: Notes Connector May &quot;Timeout on resource lock&quot; on Startup"
permalink: /kb/197/Q197509/
---

## Q197509: XFOR: Notes Connector May &quot;Timeout on resource lock&quot; on Startup

{% raw %}

	Article: Q197509
	Product(s): Microsoft Exchange
	Version(s): WinNT:5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 14-MAY-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you start or restart the Microsoft Exchange Notes connector, the browse
	logs might display the following errors:
	
	  1998/03/17 22:19:48 - LME-NOTES-DXANOTES(0199) 2 41100:Intializing
	  Lotus Notes Interface
	  >> lsnabapi(525)
	
	  1998/03/17 22:19:50 - LME-NOTES-NTSMEX(0192) 3 41207:Successfully
	  Initialized Notes Interface
	  >> ntshcs(1480)
	
	  1998/03/17 22:19:50 - LME-NOTES-NTSMEX(0192) 4 00019:The value of the
	  NOTESSERVER keyword in the LME-NOTES-NTSMEX section is 'Test/Notes'
	  >> ntshcs(3935)
	
	  1998/03/17 22:19:50 - LME-NOTES-NTSMEX(0192) 3 41262:Performing
	  consistency check, validating items, and automatically removing old
	  deleted note stubs on Test/Notes!!Exchange.box...
	  >> ntshcs(1814)
	
	  1998/03/17 22:19:50 - LME-NOTES-MEXNTS(018b) 3 41207:Successfully
	  Initialized Notes Interface
	  >> ntshcs(1480)
	
	  1998/03/17 22:22:50 - LME-NOTES-MEXNTS(018b) 2 01211:Error {Timeout on
	  resource lock}: Unable to lock the LME-NOTESOPEN shared memory object
	  >> ntshcs(1765)
	
	  1998/03/17 22:22:50 - LME-NOTES-MEXNTS(018b) 1 00510:Error (Timeout on
	  resource lock}: The application failed to initialize.
	  >> stdmain(863)
	
	  1998/03/17 22:22:50-        LME-NOTES-MEXNTS(018b) 3 00505:LME-NOTES-
	  MEXNTS is ending, last return code was {Timeout on resource lock}
	>> stdmain(958)
	
	  1998/03/17 22:22:50 - LME-NOTES-MEXNTS(018b) 1 41220:Error: no Notes
	  Session Open
	  >> ntshcs(2317)
	
	  1998/03/17 22:22:50 - LME-NOTES-MEXNTS(018b) 3 41210:Terminating Notes
	  Interface
	  >> ntshcs(1596)
	
	CAUSE
	=====
	
	This problem is because of a bug in the Notes API. This occurs because the
	LAPI_Init/LAPI_InitExtended call to the Notes API fails or stops responding
	(hangs) when one of the Notes-related processes is (re-)starting.
	
	RESOLUTION
	==========
	
	The Notes connector will handle this problem in the Notes API DLL by
	automatically restarting upon receiving this error.
	
	WORKAROUND
	==========
	
	To work around this problem, manually restart the Exchange Notes Connector.
	
	STATUS
	======
	
	Microsoft confirms this to be a problem in Microsoft Exchange Server version
	5.5.
	
	MORE INFORMATION
	================
	
	This will likely shut down all three of the Notes connector processes.
	
	Additional query words: crash, notes connector, resource, timeout
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : WinNT:5.5
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
