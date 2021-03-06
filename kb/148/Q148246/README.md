---
layout: page
title: "Q148246: PC Ext Gen: Questions Asked About X.25 and External &#91;Part II&#93;"
permalink: /kb/148/Q148246/
---

## Q148246: PC Ext Gen: Questions Asked About X.25 and External &#91;Part II&#93;

{% raw %}

	Article: Q148246
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2,3.2a,3.5; :3.2,3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 3.2, 3.2a, 3.5 
	- Microsoft Mail Multitasking MTA, version 3.2 
	- Microsoft Mail Multitasking MTA for Windows NT, version 3.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Setting up External computers communicating through X.25 requires considerable
	configuration procedures. The following are some of the frequently asked
	questions related to X.25 and the Mail External program (EXTERNAL.EXE).
	
	MORE INFORMATION
	================
	
	1. Q. Can one Multitasking Message Transfer Agent (MMTA) service X.25 and Async
	  External instances simultaneously, for more than the home postoffice?
	
	  A. Yes, but every instance of External can handle only one connection method
	  in the Admin program (Direct via either MS-DOS Drive, Modem, or X.25). The
	  X.25 instance can service many permanent drives or dynamic drive connections
	  (both MS-DOS Direct Drives). The number of these connections are limited
	  largely by the memory on the OS/2 computer. Dynamic Drives can use DynAdmin
	  tables only on the home postoffice. DrivesUNC or DrivesNovell do not use the
	  DynAdmin tables.
	
	  NOTE: The EXTERNAL.INI options DrivesDirectPO, DrivesDynamic, DrivesHomePO,
	  and DrivesNovell are not available for the Multitasking MTA for Windows NT
	  Server version 3.5 (NT MMTA).
	
	2. Q. How do you configure an MMTA to service more than one home PO?
	
	  A. Use the DriveHomePO option with different DirectDrives in the EXTERNAL.INI
	  as follows:
	
	  [External - Instance1]
	  DriveHomePO=M
	
	  [External - Instance2]
	  DriveHomePO=N
	
	3. Q. Can one instance of External handle both an X.25 and an Async call?
	
	  A. No, choosing "CommType=X25Eicon", precludes using asynchronous (async)
	  communication for the same instance, and vice-versa. The External program,
	  for example, can launch either ASYNC.OVL or the X25<card-type>.OVL, but
	  not both in the same instance. Only one X.25 session can be done at any time
	  by one External instance.
	
	4. Q. What happens when two remote postoffices or remote users dial-in at the
	  same time to one DOS MTA, or one instance of External on an MMTA?
	
	  A. One PO or remote user will connect, and the second user will fail to
	  connect, receiving a busy signal. Concurrent connections are only possible
	  with:
	   - Multiple instances of External on one OS/2 machine.
	
	   - Several instances on a Windows NT Server version 3.51 running the
	     Multitasking MTA (NT MMTA).
	
	   - Multiple MS-DOS machines running the MTA.
	
	5. Q. Can one instance of External (MS-DOS or MMTA) connecting to multiple
	  postoffices via multiple directly attached permanent drives (DrivesDirectPO),
	  support remote mail for all users on all postoffices?
	
	  A. Yes, provided that they are not dialing in at the same time. To avoid this
	  limitation, multiple instances would need to be setup. Each instance would
	  need to be connecting to a separate set of direct drive mappings. If
	  Instance1 was connecting to drives M, N, and O, Instance2 would need to
	  connect to a different set of direct drives. For example, Instance2 could
	  connect to drives P, Q, and S.
	
	6. Q. Are there any special flags or attributes in the \MAILDATA directory to
	  prevent file locking (in a Novell environment), when using X.25?
	
	  A No, there are no special flags or access rights for the Novell NetWare
	  environment for X.25. Flags and rights are the same as for "direct drive"
	  connections. For details, refer to the Microsoft Mail for PC Networks
	  "Administrator's Guide", Appendix G Troubleshooting Guide.
	
	7. Q. What is the command line for each External instance, used for X.25, to
	  differentiate it from the others?
	
	  A. The best way to differentiate the instances is to add "X25" (without the
	  quotes) to the beginning of the instance name. For example, to initiate the
	  instance from a command line use the instance name from the EXTERNAL.INI file
	  with the /InstanceName command line parameter:
	
	  EXTERNAL /InstanceName=<X25Instance_Name>
	
	8. Q. Can I specify the last X.25 channel specifically for outbound and the rest
	  of the channels for inbound mail?
	
	  A. Yes, but you control the Virtual Circuits (VC) by specifying the Comm
	  options of the External instance using this VC. Given the fact that you can
	  not specify the "Virtual Circuit" with the X25PortNumber, you are still able
	  to include CommOutOnly (-KO) and CommInOnly (-KI) EXTERNAL.INI options (-KO
	  and -KI External command line parameters). When you configure the Eicon card,
	  specify one-way or two-way in External_Admin, Setup, VCs by number. The other
	  option is to use the -KI, -KO switches with X.25. It is recommended to use a
	  single two-way virtual circuit in the Eicon setup (the default), rather than
	  using -KI and -KO switches in the External command line.
	
	9. Q. What are X.25 subaddresses, and how do they relate to External_Admin,
	  Setup and to the EXTERNAL.INI file entries?
	
	  A. When an X.25 application, such as the MTA is on a LAN workstation, and the
	  X.25 card and software are installed on a second computer, the X.25 card
	  software (Eicon or Atlantis) needs a way of identifying which LAN process it
	  is establishing a X.25 virtual circuit.
	
	  The subaddress is an arbitrary but unique two-digit number assigned by the
	  mail Admin that is added to the end of the original X.21 subaddress.
	
	  ADMIN PROGRAM
	  An X.25 connection is defined under the Admin program by selecting
	  External-Admin, Create, Network, Postoffice, Direct/X.25.
	
	  EXTERNAL.INI FILE
	  In the EXTERNAL.INI file, the required entries look similar to the following
	  for the Eicon X.25 card and software:
	
	  [External - X.25]
	  CommType=X25Eicon
	  X25PortNumber=255 ; 255 is for a DOS MTA
	  X25SubAddress=234187654321XX ; where XX is a unique 2-digit number
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q130231 External Command Line Options Not Used with NT MMTA
	
	Additional query words: 3.00 3.20 3.20a faq ntmmta
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword2 kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN320a kbMailPCN350 kbMailMMTA320 kbMailMMTA350NT
	Version           : WINDOWS:3.2,3.2a,3.5; :3.2,3.5
	
	=============================================================================
	

{% endraw %}
