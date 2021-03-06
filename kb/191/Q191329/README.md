---
layout: page
title: "Q191329: SMS: How to Install the PCM Service Without Using RSERVICE"
permalink: /kb/191/Q191329/
---

## Q191329: SMS: How to Install the PCM Service Without Using RSERVICE

{% raw %}

	Article: Q191329
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbsetup kbPCM smssetup smspcm
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to install the Package Command Manager (PCM) service
	on computers running Windows NT Workstation, without using the RSERVICE utility.
	The MORE INFORMATION section of this article contains:
	
	- The steps for installing PCM as a service without using RSERVICE.
	
	- A sample script illustrating how this would look for installing the service
	  to the c:\PCMSVC directory in a domain called "ABC_Domain", with a PCM
	  service account name of "PCM_Service" with a password of "anything".
	
	MORE INFORMATION
	================
	
	To install PCM as a service, without using RSERVICE, perform the following
	steps:
	
	1. Create a source directory containing the following utilities from the
	  Resource Kit:
	
	   - Regini.exe (used to add registry entries for the service logs)
	   - Ntrights.exe (used to give the service account the proper rights)
	   - Instsrv.exe (used to install the service)
	   - Pcmsvc32.exe (the actual service executable to be installed)
	
	2. Create a batch file a file name that describes its purpose (for example,
	  Instlpcm.bat).
	
	3. Add the following to your batch file, replacing the name of your domain,
	  service account, and the service account password where applicable. This
	  batch file is written to install the PCM service from drive A and install it
	  to drive C. You can change this to the desired location from where to run the
	  batch file and/or where you want to install the PCM service, respectively.
	
	     -----------------INSTLPCM.BAT------------------------------
	     REM InstlPCM.bat
	
	     REM Add SMS related registry entries
	     a:\regini.exe a:\regfix.ini
	
	     REM Add ABC_DOMAIN\PCM_SERVICE account to the workstation's
	     REM Administrators local group
	
	     NET localgroup administrators /add ABC_DOMAIN\PCM_SERVICE
	
	     REM On the workstation, assign Logon As A Service rights to PCM_SERVICE
	     REM account
	     NTRIGHTS -u ABC_DOMAIN\PCM_SERVICE +r SeServiceLogonRight
	
	     REM Copy PCMSVC32.EXE to the workstation
	     MD c:\pcmsvc
	     COPY a:\pcmsvc32.exe c:\pcmsvc
	
	     REM Install the PCM Service
	     a:\instsrv.exe SMS_PACKAGE_COMMAND_MANAGER_NT C:\PCMSVC\PCMSVC32.EXE -a
	     ABC_DOMAIN\PCM_SERVICE -p anything
	
	     REM Start the PCM Service
	     NET start SMS_PACKAGE_COMMAND_MANAGER_NT
	     ----------------------------end of batch file------------------------
	
	4. Create the REGINI initialization file. This is the file that REGINI reads to
	  add the appropriate registry entries. The entries in the .ini file are shown
	  below. These entries assume that you have installed the service to the
	  c:\PCMSVC directory.
	
	  \registry\machine\Software\Microsoft\SMS\Identification
	                    Installation Directory = REG_SZ C:\PCMSVC
	
	  \registry\machine\Software\Microsoft\SMS\TRACING
	                    Enabled = REG_SZ 1
	
	  \registry\machine\Software\Microsoft\SMS\TRACING
	  \SMS_PACKAGE_COMMAND_MANAGER_NT
	                    Enabled = REG_SZ 1
	
	  \registry\machine\Software\Microsoft\SMS\TRACING
	  \SMS_PACKAGE_COMMAND_MANAGER_NT
	                    TraceFilename = REG_SZ C:\pcmsvc\LOGS\pacman.log
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	5. Copy the batch file and .ini file to your source directory.
	
	6. Log on to the workstation with an account that has administrator rights and
	  run the batch file. This will install and start the service.
	
	Additional query words: pcmsvc32 pcmsvc script login logon client new machines
	
	======================================================================
	Keywords          : kbsetup kbPCM smssetup smspcm 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
