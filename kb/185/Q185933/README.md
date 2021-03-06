---
layout: page
title: "Q185933: XADM: Directory Service May Stop Unexpectedly During Exception H"
permalink: /kb/185/Q185933/
---

## Q185933: XADM: Directory Service May Stop Unexpectedly During Exception H

{% raw %}

	Article: Q185933
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55sp2fix
	Last Modified: 12-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The directory service may stop unexpectedly when it encounters an error leading
	to a particular exception handling routine that is to be invoked. If Dr. Watson
	is active as the default debugger, then a Dr. Watson log and a User.dmp (if
	configured to create a User.dmp) may be produced.
	
	CAUSE
	=====
	
	The exception handling routine causes the access violation when it attempts to
	de-reference a NULL pointer.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Exchange Server version 5.5.
	This problem was first corrected in Exchange Server 5.5 Service Pack 2.
	
	
	MORE INFORMATION
	================
	
	The Drwtsn32.log file that is produced will look similar to the following:
	
	  Microsoft (R) Windows NT (TM) Version 4.00 DrWtsn32
	  Copyright (C) 1985-1995 Microsoft Corp. All rights reserved.
	
	  Application exception occurred:
	        App: DIR.DBG (pid=76)
	        When: 2/19/1998 @ 9:39:5.106
	        Exception number: c0000005 (access violation)
	
	 State Dump for Thread Id 0x1aa
	
	  EAX=000013ef  EBX=00000000  ECX=00177008  EDX=00030002  ESI=00000000
	  EDI=00000018
	  EIP=6FEEFAA8  ESP=09b5ea20 EBP=09b5eb30  EFL=00000202
	  CS=001b  DS=0023  ES=0023  SS=0023  FS=0038  GS=0000
	
	  function:ESE!GetLogicalAddress
	
	   .....
	   6FEEFACD  8B742414           mov         esi,dword ptr [esp+14h]
	   6FEEFAD1  51                    push        ecx
	   6FEEFAD2  53                  push        ebx
	   6FEEFAD3  56                 push        esi
	   6FEEFAD4  FF155411E96F        call        dword ptr [FileNameA]
	   6FEEFADA  85C0                test        eax,eax
	        6FEEFADC  746A                je          GetLogicalAddress+9Ch
	FAULT -->6FEEFADE  8B463C              mov         eax,dword ptr [esi+3Ch]
	   6FEEFAE1  33D2                xor         edx,edx
	   .....
	
	  *----> Stack Back Trace <----*
	  FramePtr  RetAddr   Param1   Param2   Param3   Function Name
	  09b5eb30  6feefa73  00000104 09b5eb54 09b5eb58
	  ESE!GetLogicalAddress+0x36
	  09b5eee8  6feef8f2  09b5ef18 6ff24eb2 6ff2f0b8
	  ESE!ImagehlpStackWalk+0x172
	  09b5eef0  6ff24eb2  6ff2f0b8 77f01361 09b5f048
	  ESE!GenerateStackWalk+0x19
	  09b5ef00  6ff25126  6fe97948 00000000 09b5f380
	  ESE!UtilDumpCallstack+0x39
	  09b5f028  7801310e  09b5f050 00000000 09b5f050 ESE!ExceptionFail+0x2075d
	  6fe97948  6fed7ae9  6fed7af6 83ec8b55 c18b0cec
	  _except_handler3+0x4b(...)
	  ffffffff  00000000  00000000 00000000 00000000 ESE!JetSeek+0x4029d
	
	======================================================================
	Keywords          : exc55sp2fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
