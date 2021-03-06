---
layout: page
title: "Q128173: Contents of the Microsoft Windows Sound System DEINSTAL.TXT"
permalink: /kb/128/Q128173/
---

## Q128173: Contents of the Microsoft Windows Sound System DEINSTAL.TXT

{% raw %}

	Article: Q128173
	Product(s): Miscellaneous Windows Products
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Sound System, versions 1.0, 1.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the DEINSTAL.TXT file
	included with the Microsoft Windows Sound System versions 1.0 and 1.0a.
	
	MORE INFORMATION
	================
	
	MICROSOFT WINDOWS SOUND SYSTEM
	Copyright (C) 1991-1992 Microsoft Corporation
	
	The following is a list of the files that make up the Windows Sound
	System and a list of initialization file changes.
	
	Not all these files can be found on any given computer due to differ-
	ences in installation and use.  Moreover, when installed on a computer
	that is running from a shared Windows installation on a remote network
	drive, all the files listed as being in the Windows System directory
	are actually located in the local Windows directory.
	
	To remove the Windows Sound System, you must remove these files and
	entries. Please delete files and remove entries from within MS-DOS
	after you have exited Windows. If you try to delete the files from
	within Windows, some of them might be in use, and you will not be
	able to do so.
	
	Files in the Windows directory (for example, C:\WINDOWS):
	
	WINDOWSS.GRP
	SNDSYS.HLP
	SNDSYS.INI
	VOICEPIL.INI
	SNDCNTRL.DLL
	SND.HLP
	SNDSCAPE.HLP
	SNDSCAPE.SCR
	MCIPLAY.EXE
	MUSICBOX.INI
	
	Backup versions of existing files:
	
	CONTROL.WSS    (Backup version of CONTROL.INI)
	SYSTEM.WSS     (Backup version of SYSTEM.INI)
	VOICEPIL.WSS   (Backup version of VOICEPIL.INI)
	WIN.WSS        (Backup version of WIN.INI)
	
	Files in the Windows System directory
	(for example, C:\WINDOWS\SYSTEM):
	
	SNDSYS.DRV
	SNDSYS.PAT
	VSNDSYS.386    (When you restart Windows after deleting this file,
	              you may receive a warning that you can ignore.)
	SNDSYSW.CPL
	MIDIMAP.CFG    (original file replaced)
	SND.CPL        (original file replaced)
	MSACM.DRV
	MSADPCM.ACM
	
	CAUTION: The files MSACM.DRV and MSADPCM.DRV can be used by other
	        applications. Therefore, their removal could hinder these
	        applications' proper functioning.
	
	Backup versions of existing files:
	MIDIMAP.WSS    (Backup version of MIDIMAP.CFG)
	
	Files in the Microsoft Excel directory
	(for example, C:\EXCEL): XLRDR.INI
	
	Files in the Microsoft Excel Library directory
	(for example, C:\EXCEL\LIBRARY): PROOF.XLA
	
	Files in the Lotus 1-2-3 for Windows directory
	(for example, C:\123WIN): 123RDR.INI
	
	Files in the directory where the Windows Sound System was installed.
	(The default is C:\SNDSYS.)
	
	In some cases, you may not be able to delete the dictionary (*.DCT)
	files that are installed with ProofReader. To delete them, start
	Windows File Manager, and select all the files with the .DCT
	extension. Then, from the File menu, choose Delete. File Manager
	warns you that the files are "system, hidden or read-only" and
	provides you with options. Choose the Yes button.
	
	All files and directories should be removed.
	
	The following is a list of modifications made to initialization
	(.INI) files that were not created by Windows Sound System. The
	files created by Windows Sound System are listed above.
	
	Note: Depending on how you installed Windows Sound System and how
	you use it, some of the entries below may not be present in the
	specified files. Also, C:\SNDSYS is replaced by the full directory
	name where you installed Windows Sound System if you did not choose
	the default C:\SNDSYS location.
	
	Initialization files in the Windows directory
	(for example, C:\WINDOWS):
	
	File:    123W.INI:
	Section: [AUTOLOAD ADDINS]
	Entries:
	  123RDR.ADW=C:\SNDSYS, 1, 0, 0
	
	File: CONTROL.INI:
	
	Note: CONTROL.WSS is a copy of your CONTROL.INI before Windows
	Sound System was installed on your system.
	
	Section: [MMCPL]
	Entries:
	  Sndsysw=sndsysw.cpl
	  SndsysSnd=snd.cpl
	
	Section: [drivers.desc]
	Entries:
	  MSACM.DRV=Microsoft Audio Compression Manager
	  SNDSYS.DRV=Microsoft Windows Sound System
	
	Section: [SoundSchemes]
	Entries: ALL
	(Note: If you have Microsoft SoundBits installed on your system,
	do not delete the entries for Musical Sounds, Hanna Barbera,
	Hollywood Movies, or Your Old Scheme.)
	
	Section: [Sndscape.Birds]
	Entries: ALL
	
	Section: [Sndscape.Chimes]
	Entries: ALL
	
	Section: [Sndscape.Clock]
	Entries: ALL
	
	Section: [Sndscape.Jungle]
	Entries: ALL
	
	Section: [Sndscape.Night]
	Entries: ALL
	
	Section: [soundscapes]
	Entries: ALL
	
	File: WIN.INI
	
	Note: WIN.WSS is a copy of your WIN.INI before Windows Sound System
	was installed on your system.
	
	Section: [Extensions]
	Entries:
	  WAV=C:\SNDSYS\QRECORD.EXE ^.WAV
	  SND=C:\SNDSYS\SNDFINDR.EXE ^.SND
	  AIF=C:\SNDSYS\SNDFINDR.EXE ^.AIF
	  VOC=C:\SNDSYS\SNDFINDR.EXE ^.VOC
	  MID=C:\SNDSYS\SNDFINDR.EXE ^.MID
	  RMI=C:\SNDSYS\SNDFINDR.EXE ^.RMI
	
	Section: [Embedding]
	Entries:
	  SoundRec=Sound,Sound,C:\SNDSYS\QRECORD.EXE,picture
	
	Note: To restore Sound Recorder as the OLE server for sound objects,
	replace C:\SNDSYS\QRECORD.EXE with SOUNDREC.EXE. This is also select-
	able from the Windows Sound System Setup program.
	
	Section: [mci extensions]
	Entries:
	
	CAUTION: The following entries can be used by other applications.
	Therefore, their removal could hinder these applications' proper
	functioning.
	
	  wav=waveaudio
	  mid=sequencer
	  rmi=sequencer
	
	Section: [sounds]
	Entries: If there are any system events that point to WSS sound
	files, you should remove the location and name of each sound file.
	You can either replace them with existing sound filenames or leave
	them blank and use the Sound Control Panel to assign existing sounds
	to these events.
	
	File: SYSTEM.INI
	
	Note: SYSTEM.WSS is a copy of your SYSTEM.INI before Windows Sound
	System was installed on your system.
	
	Section: [drivers]
	Entries:
	  WaveMapper=MSACM.DRV
	  wave=SNDSYS.DRV
	  aux=SNDSYS.DRV
	  midi=SNDSYS.DRV
	
	Section: [sndsys.drv]
	Entries: ALL
	
	Section: [386Enh]
	Entries:
	  device=vsndsys.386
	  device=vdmadx.386   (removed by Setup)
	
	Section: [mci]
	Entries:
	
	CAUTION: The following entries can be used by other applications.
	Therefore, their removal could hinder these applications' proper
	functioning. If you decide to reinstall WSS, you must restore
	these entries before you can obtain full WSS functionality.
	
	[mci]
	 CDAudio=mcicda.drv
	 WaveAudio=mciwave.drv 6
	 Sequencer=mciseq.drv
	
	Microsoft Windows Sound System Version 1.0a
	-------------------------------------------
	
	The following information applies only to the Microsoft Windows Sound
	System version 1.0a. Disregard this information if you are running
	version 1.0 of the Windows Sound System.
	
	Note
	====
	
	This following change in quotation is only for Microsoft Windows
	Sound System version 1.0a. Disregard if using version 1.0.
	
	"Section: [msacm]
	
	CAUTION: The following entry may be used by other applications. If
	you are unsure whether other applications are using this entry, DO
	NOT remove it.
	
	Entries:
	install=msadpcm.acm"
	===================================================================
	
	File: EXCEL4.INI or EXCEL.INI depending upon which version of
	Microsoft Excel is installed.
	
	Section: [Microsoft Excel]
	Entries:
	  OPEN#=/F C:\EXCEL\LIBRARY\PROOF.XLA
	     Where # is a digit (0,1,2, etc.)
	
	===================================================================
	
	File: PROGMAN.INI
	(Note: Please make a backup copy of this file before proceeding.)
	Section: [Groups]
	Entries:
	  Group#=C:\WINDOWS\WINDOWSS.GRP
	     Where # is a digit (0,1,2, etc.)
	
	Section: [Settings]
	Entries:
	  Delete the number that appears in place of the number sign (#)
	  in the section above.
	
	File: WINHELP.INI
	Section: [Files]
	Entries:
	  wsspss.hlp=c:\sndsys
	  tour.exe=c:\sndsys\demo
	
	(Note: If your WSS installation directory is not C:\SNDSYS,
	the full path you designated for WSS replaces C:\SNDSYS in
	the preceding two lines.)
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinSoundSysSearch kbWinSoundSys100 kbWinSoundSys100a
	
	=============================================================================
	

{% endraw %}
