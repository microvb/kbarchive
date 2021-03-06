---
layout: page
title: "Q201575: How to Configure the Telnet Server to Use the Korn Shell"
permalink: /kb/201/Q201575/
---

## Q201575: How to Configure the Telnet Server to Use the Korn Shell

{% raw %}

	Article: Q201575
	Product(s): Microsoft Windows NT
	Version(s): 2.0,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 01-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Services for UNIX Add-On Pack 
	- Microsoft Windows Services for UNIX, version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article outlines how to configure your Services for UNIX telnet server to
	use the Korn Shell (Sh.exe) in place of the default logon shell (Cmd.exe).
	
	MORE INFORMATION
	================
	
	The following instructions assume that Services for UNIX has been installed to
	the C:\SFU directory. This is not the default directory, but it is easier to
	show. The assumption is also made that you have created a user named TelnetUser
	and assigned this user a home directory of F:\home\TelnetUser.
	
	1. Run Notepad and insert the following lines:
	
	  @echo off
	  C:\SFU\Shell\SH.EXE -rL
	
	2. Save this file as C:\SFU\Telnet\shell.bat.
	
	3. Create a new file in Notepad and insert the following lines:
	
	     EDITOR=vi
	     export EDITOR
	     alias ll="ls -l"
	     alias la="ls -a"
	     USERNAME=`basename $PWD`
	     export USERNAME
	     USER=$USERNAME
	     export USER
	     LOGNAME=$USERNAME
	     export LOGNAME
	     echo
	     echo
	     echo "Welcome to the Korn Shell!"
	     echo
	     echo
	
	4. Save this file as F:\home\TelnetUser\profile.ksh.
	
	5. Run Tlntadmn.exe from Start, Run or from a command prompt.
	
	6. Select selection number 3 to make a registry change.
	
	7. Select selection number 4 to change the default shell.
	
	8. Change DefaultShell to C:\SFU\Telnet\shell.bat
	
	9. Select selection number 0 to exit this menu.
	
	10. Select selection number 5 to stop the Telnet service.
	
	11. Select selection number 4 to start the Telnet service.
	
	12. Telnet in and test your modifications.
	
	If you need to go back to the default Cmd.exe shell, the following is the exact
	syntax used for DefaultShell:
	
	  %SystemRoot%\System32\Cmd.exe /q /k
	
	Additional query words: telnetd solar coaster sfu sh exe cmd
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400xsearch kbWinNTSsearch kbWinNTS400xsearch kbWinNTS400 kbWinNTServicesUnix kbWinServiceUNIX200 kbWinServiceUNIXSearch
	Version           : :2.0,4.0
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
