---
layout: page
title: "Q119355: PC Gen: Answer Procedure Played Approximately Once Per Second"
permalink: /kb/119/Q119355/
---

## Q119355: PC Gen: Answer Procedure Played Approximately Once Per Second

{% raw %}

	Article: Q119355
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:2.1,3.0,3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 2.1, 3.0, 3.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Mail for PC Networks uses script files to specify a variety of serial
	devices, communications (COM) ports, and baud rates. Within a script file are
	script procedures that are run by Mail programs to accomplish certain tasks.
	
	One of these tasks is monitoring the COM port for incoming calls. This is
	accomplished by running the ANSWER procedure within a script file. When idle,
	the External Mail program (EXTERNAL.EXE) and the Listen program (LISTEN.EXE) run
	the ANSWER procedure about once per second or a little more than 50 times per
	minute. LISTEN is the MS-DOS Remote terminate-and- stay-resident (TSR) program
	that is run to monitor the COM port for incoming calls.
	
	The ANSWER procedure looks for the number 2 coming from the COM port. The number
	2 is the numeric form of a ringing phone; RING is the text form. For null-modem
	connections, the ANSWER procedure looks for the number 9 from the COM port. Once
	an incoming call is detected, the ANSWER procedure issues an ATA to answer the
	phone, or responds with the number 8 for the null-modem script. At this point,
	the modems negotiate a rate at which to exchange data and this information is
	passed to EXTERNAL.EXE or LISTEN.EXE in the form of a numeric result code.
	
	NOTE: In general, Microsoft Mail script files initialize modems to use numeric
	result codes; however, you can also initializing modems to use text.
	
	MORE INFORMATION
	================
	
	Including the ANSWER procedure, a script file has five reserved procedures/label
	names:
	
	- INITIALIZE
	
	- CALL
	
	- ANSWER
	
	- DISCONNECT
	
	- RESET
	
	Not all of these script procedures must appear in a script file. If a script
	procedure does not exist, the Mail program does not perform the function. For
	example if there is no ANSWER section, the External Mail program does not answer
	the phone.
	
	The following is more information about each section and which Mail programs use
	it.
	
	INITIALIZE
	----------
	
	The External Mail program, Mail Remote for MS-DOS, and Mail Remote for Windows
	all run this section. This section configures the serial port and the device
	attached to it. It starts the communication session to ensure the device is
	available and responding and is run once and only once during a session.
	TRANSMIT.EXE is the MS-DOS Remote program that is used to transmit mail to the
	postoffice. It is called automatically when you run MAIL.EXE and you choose to
	dial the postoffice.
	
	CALL
	----
	
	The External Mail program, Mail Remote for MS-DOS, and Mail Remote for Windows
	all run this section. This section initializes a connection between two devices.
	It is run when there is mail queued for another postoffice, an MS-DOS Remote
	user, or when a Windows Remote user has mail to send. It can also be run by the
	Microsoft Mail Gateway to MCI.
	
	ANSWER
	------
	
	The External Mail program and Mail Remote for MS-DOS both run this section. Note
	that Windows Remote does not support answering the phone for incoming calls,
	hence it does not run the ANSWER section.
	
	DISCONNECT
	----------
	
	The External Mail program, Mail Remote for MS-DOS, and Mail Remote for Windows
	all run this section. This section is run after all communications for incoming
	and outgoing calls are complete.
	
	RESET
	-----
	
	The External Mail program, Mail Remote for MS-DOS, and Mail Remote for Windows
	all run this section. This section is run after every disconnection, after the
	DISCONNECT section has been run.
	
	Additional query words: 2.10 3.00 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN300 kbMailPCN210
	Version           : WINDOWS:2.1,3.0,3.2
	
	=============================================================================
	

{% endraw %}
