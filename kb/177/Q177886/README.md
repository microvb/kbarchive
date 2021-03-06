---
layout: page
title: "Q177886: XCON: MTA Terminates With 218x, 2143, 2171, and 9405 Events"
permalink: /kb/177/Q177886/
---

## Q177886: XCON: MTA Terminates With 218x, 2143, 2171, and 9405 Events

{% raw %}

	Article: Q177886
	Product(s): Microsoft Exchange
	Version(s): 4.0 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-MAR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The Microsoft Exchange Message Transfer Agent (MTA) versions 4.0 and 5.0 may
	terminate unexpectedly with Events ID's similar to the following in the Windows
	NT Event Viewer Application log:
	
	  9405
	  An unexpected error has occurred which may cause the MTA to terminate.
	  Error: Access violation (0xc0000005) at Address 0x58af88 writing to
	  0x49. [BASE DELIVER 38] (16)
	
	  2171
	  An MTA database server error was encountered while reading an attribute.
	  Called from XAPI. Procedure: 44. Database error code: ODXOINIU - Object
	  does not exist. Object at fault: 0600004E. Attribute identifier: 18.
	  Value number: 1. Referenced object: 00000000 (00000000 => N/A).
	  Referenced object error 0. [DB Server DELIVER 38 26] (14)
	
	  2188
	  An MTA database server error was encountered while deleting an object.
	  Called from XAPI. Procedure 109. Database error code: ODXOINIU - Object
	  does not exist. Object at fault: 00000000. [DB Server DELIVER 38 9]1
	  109 ODXOINIU - Object does not exist 00000000 DB Server DELIVER 38] (14)
	
	  2187
	  An MTA database server error was encountered while attempting to unlock
	  an object which is not locked. Called from XAPI. Procedure 235. Object
	  at fault: 0600004E. [DB Server DELIVER 38 58] (14)
	
	  2189
	  An MTA database server error was encountered while getting a number of
	  values for an object. Called from XAPI. Procedure: 235. Database error
	  code: ODXOINIU - Object does not exist. Object at fault: 0600004E.
	  Attribute identifier: 6. Referenced object, 00000000 (00000000 => N/A).
	  Referenced object error 0. [DB Server DELIVER 38 124] (14)
	
	  2186
	  An MTA database server error was encountered while locking an object.
	  Called from XAPI. Procedure 235. Database error code: ODXOINIU - Object
	  does not exist. Object at fault: 0600004E. [DB Server DELIVER 38 57]
	  (14)
	
	  105
	  An MTA database server error was encountered. [MTA SUBMIT 17 223] (14)
	
	  62
	  A delivery failure occurred for the message with message transfer
	  service identifier . X.400 reason code unable-to-transfer. Diagnostic
	  content-too-long. Contact Microsoft Product Support Services. [0 MTA
	  SUBMIT 17 112] (12)
	
	  3144
	  An internal MTA error occurred: message submit failure. Object ID:
	  0600004E. Entity name: /o=MS/ou=GUITARS/cn=Configuration/cn=Servers
	  /cn=BRASS_KITTEN/cn=Microsoft Public MDB. [XAPI DELIVER 38 109] (12)
	
	  62
	  A delivery failure occurred for the message with message transfer
	  service identifier C=US;A= ;P=GE;L= BRASS_KITTEN-971105182614Z-409.
	  X.400 reason code unable-to-transfer. Diagnostic content-too-long.
	  Contact Microsoft Product Support Services. [0 MTA SUBMIT 17 112]
	  (12)
	
	  2171
	  An MTA database server error was encountered while reading an
	  attribute. Called from MTA. Procedure: 88. Database error code:
	  ODXFATAL - Internal or Application Error. Object at fault: 0600004F.
	  Attribute identifier: 10. Value number: 1. Referenced object:
	  00000000 (00000000 => N/A). Referenced object error 0. [DB Server
	  DELIVER 9 26] (14)
	
	  2143
	  A fatal MTA database server error was encountered. Call Microsoft
	  Product Support. Unrecoverable error: ODXFATAL - Internal or
	  Application Error. About to terminate. Called from MTA. Procedure 88.
	  Object ID: 0600004F. Attribute ID: 10. Attribute value number: 1.
	  Referenced object: 00000000 (00000000 => N/A). Referenced object
	  error 0. [1 DB Server DELIVER 9 101] (16)
	
	  2172
	  An MTA database server error was encountered while rewriting an
	  attribute. Called from MTA. Procedure: 73. Database error code:
	  ODXFATAL - Internal or Application Error. Object at fault: 0600004F.
	  Attribute identifier: 10. Value number: 1. Referenced object:
	  0600004E (00000000 => N/A). Referenced object error 2103. [DB Server
	  SUBMIT 17 75] (14)
	
	MORE INFORMATION
	================
	
	The faulting thread's stack may look similar to the following in a
	DRWTSN32.LOG:
	
	  FramePtr  RetAddr   Param1   Param2   Param3   Function Name
	  06b1ff4c  00443e4b  005e3226 02abc514 06b1ff8c EMSMTA!oxpmroer+0x178
	  06b1ff5c  0048f375  b1ffb826 00f95044 000005f0 EMSMTA!oxpmrocv+0x6b
	  06b1ff8c  004802dc  00f95044 0110fdc0 00000026 EMSMTA!oxpmrcv+0x505
	  06b1ffb8  77f04f2c  00000026 00f95044 0110fdc0 EMSMTA!sbpiwbep+0x5c
	  06b1ffec  00000000  00480280 00000026 00000000
	KERNEL32!BaseThreadStart+0x51
	
	When restarting the MTA, MTACHECK will be run which will move the corrupted
	object out of the way. This will allow the MTA to start successfully and normal
	operation should resume.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server,
	version 5.0.
	
	This problem has been corrected in the latest U.S. Service Pack for Microsoft
	Exchange Server version 5.0. For information on obtaining the Service Pack,
	query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server,
	version 4.0.
	
	
	A supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft Product
	Support Services for more information.
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbZNotKeyword2
	Version           : 4.0 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
