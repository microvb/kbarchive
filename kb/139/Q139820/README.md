---
layout: page
title: "Q139820: Moving or Removing Disks &amp; Fault Tolerant Drive Configurations"
permalink: /kb/139/Q139820/
---

## Q139820: Moving or Removing Disks &amp; Fault Tolerant Drive Configurations

{% raw %}

	Article: Q139820
	Product(s): Microsoft Windows NT
	Version(s): 3.10 3.50 3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 3.1 
	- Microsoft Windows NT Workstation version 3.1 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you remove any disks or members of a fault tolerant set from the computer
	without first deleting the information about them in Disk Administrator - or if
	a member of a fault tolerant set fails, the following error message appears when
	you start Disk Administrator:
	
	  Disk Administrator has determined that one or more disks have been removed
	  from your computer since Disk Administrator was last run, or that one or more
	  disks are off-line.
	
	  Configuration information about the missing disk(s) will be retained.
	
	In addition - Event viewer may post the following event messages:
	
	Event ID: 12 Source: FTDISK Description: A stripe set or volume set member listed
	in the configuration information was missing.
	
	Event ID: 14 Source: FTDISK Description: The FT set containing
	\Device\MissingMirror1Member0 cannot be used.
	
	**NOTE: Actual device membership message for event ID: 14 may be different.
	
	This article describes how to move the existing fault-tolerance registry
	information to the registry on a new computer where you install the disks or
	members of the fault tolerant set. This article also explains how to eliminate
	the error message above after moving an entire, fault-tolerant subsystem to
	another computer.
	
	MORE INFORMATION
	================
	
	When you create fault tolerant volumes in Disk Administrator such as volume
	sets, stripe sets, or mirrored drives, this configuration information is stored
	in the registry in binary format that contains specific information such as
	number of disks attached to the system, disk signature strings, drive letter
	assignments, partition information, and fault tolerant memberships.
	
	Moving a Disk or Member of a Fault-Tolerant Set
	-----------------------------------------------
	
	If you decide to move all the fault-tolerant arrays or drives from one computer
	to a different computer, intact with all data, you must save the configuration
	information to a floppy disk from Disk Administrator:
	
	1. Run Disk Administrator.
	
	2. From the Partition menu, choose Configuration, then choose Save.
	
	3. Insert a formatted floppy disk in drive A when prompted.
	
	4. Install the moved hardware on the new computer.
	
	5. Insert the floppy created in step 3 in the floppy drive of the new computer.
	
	6. Run Disk Administrator on the new computer.
	
	7. From the Partition menu, choose Configuration, and then choose Restore.
	
	NOTE: When the saved configuration information is restored to the new computer,
	the saved configuration information replaces the existing drive configuration
	information by overwriting the registry key. Because of this, it is not possible
	to move a fault tolerant subsystem to another system that has a fault tolerant
	subsystem already installed. In addition, if you separate multiple fault
	tolerant subsystems by moving them to separate computers and restoring the
	configuration information you receive the message stated above because the
	restored key contains Rogue entries about the missing fault tolerant subsystem.
	
	Eliminating the Error Msg after Moving an Entire, Fault-Tolerant Subsystem
	--------------------------------------------------------------------------
	
	If you move the entire, fault-tolerant subsystem to another computer, and no
	other volume sets, stripe sets, or mirrored drives exist on this system the
	error message above appears.
	
	To elimate the error message:
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be resolved. Use this tool at your own risk.
	
	1. Run the Registry Editor.
	
	2. Delete the \System\DISK key under HKEY_LOCAL_MACHINE subtree.
	
	3. Run Disk Administrator to re-create the DISK key with the current
	  information.
	
	Any reassigned drive or CD-ROM drive letters need to be reassigned again. In
	addition, the FTDISK device must be set to "disabled" in Control Panel devices.
	
	NOTE: If you only moved portions of a fault tolerant subsystem to another
	computer and you want to eliminate the error message, do not delete the DISK
	key, instead, please call Microsoft Product Support services for Assistance
	using the NT Resource Kit utility called FTEDIT.
	
	
	Additional query words: prodnt 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNTS310search kbWinNT310Search kbWinNTW310Search
	Version           : 3.10 3.50 3.51
	
	=============================================================================
	

{% endraw %}
