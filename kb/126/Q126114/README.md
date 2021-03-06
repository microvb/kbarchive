---
layout: page
title: "Q126114: Ultimate Haunted House README.WRI Contents"
permalink: /kb/126/Q126114/
---

## Q126114: Ultimate Haunted House README.WRI Contents

{% raw %}

	Article: Q126114
	Product(s): Microsoft Home Games
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-2001
	
	kbreadme kbmm
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Haunted House for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the README.WRI file included
	with Microsoft Gahan Wilson's The Ultimate Haunted House.
	
	NOTE: This Readme document refers to the Microsoft Download Service (MSDL). As of
	12/31/1998, the MSDL service is no longer available. To download support files,
	visit one of the following Microsoft Internet sites:
	
	  http://support.microsoft.com/support
	
	  ftp://ftp.microsoft.com/softlib/mslfiles
	
	MORE INFORMATION
	================
	
	Gahan Wilson's The Ultimate Haunted House Read Me File
	Microsoft Corporation
	December 16, 1994
	
	To read this file on-screen, use the Page Down and Page Up keys. You
	can also print the file by choosing the Print command from the File
	menu in any Windows word processing program. This README file
	contains important information on the following topics:
	
	Section Description
	Problems Setting Up Gahan Wilson's  - The Ultimate Haunted House
	Running In Low Memory or Running Slowly
	CD-ROM Problems
	Video Display Problems
	Audio Problems
	Skipping the Introduction
	Problems Setting Up Gahan Wilson's  - The Ultimate Haunted House
	
	Installing on Non-Windows' Program Manager Systems
	Most Tandy Sensations use WinMate as their default desktop shell.
	WinMate may cause a conflict with the setup procedure and needs to be
	disabled by changing the shell= line in the SYSTEM.INI file to read
	as follows:
	
	shell=progman.exe
	
	To change the shell= line in the SYSTEM.INI file:
	
	From the Windows Accessories group, run Notepad.
	Open the SYSTEM.INI file and comment out the shell= line in the
	[boot] section by typing a semicolon (;) at the beginning of the
	shell= line.  This is the line loading the Tandy WinMate shell.
	Create a new line under the commented shell= line reading as
	follows:  shell=progman.exe.
	After saving the changes to the SYSTEM.INI file, exit and restart
	Windows.  The WinMate shell will now be disabled and your shell will
	now be Program Manager.
	Run Gahan Wilson's  - The Ultimate Haunted House Setup.
	
	Upon completion of Gahan Wilson's  - The Ultimate Haunted House
	Setup, you can change your shell back to the WinMate desktop, if so
	desired:
	
	Edit the SYSTEM.INI file again by commenting out the
	"shell=progman.exe" line (adding a semicolon to the beginning of the
	shell=progman.exe line).
	Remove the semicolon (;) in front of the previously commented
	"shell=" line that loads WinMate.
	
	Running In Low Memory or Running Slowly
	Gahan Wilson's  - The Ultimate Haunted House uses your computer's
	system memory to display pictures. Gahan Wilson's  - The Ultimate
	Haunted House requires you have 8MB of RAM memory in your system. If
	you find Gahan Wilson's  - The Ultimate Haunted House runs slowly or
	if you encounter out-of-memory errors, Gahan Wilson's  - The Ultimate
	Haunted House probably doesn't have enough memory. Consider doing the
	following to improve your computer's performance:
	
	Close all unnecessary applications.
	If you are running Windows for Workgroups, Run without network
	support by typing "win /n" at the DOS prompt.
	Make sure you have the most recent versions of SmartDrive and
	MSCDEX (SmartDrive 5.0 and MSCDEX 2.23 are the most recent versions
	at the time of this release). The most recent version of SmartDrive
	can cache the
	CD-ROM drive, greatly improving performance. Make sure smartdrv is
	after MSCDEX in your Autoexec.bat. For information on the current
	SmartDrive
	settings type "smartdrv" at the DOS prompt. For help with SmartDrive
	type "smartdrv /?" at the DOS prompt or consult your DOS User's
	Guide.
	Determine how much memory your computer has available by typing
	"mem" and pressing ENTER at the DOS prompt. You need a minimum of 8MB
	of total memory to use Gahan Wilson's  - The Ultimate Haunted House.
	If you do not have at least 8MB of memory, you may not be able to run
	Gahan Wilson's  - The Ultimate Haunted House until you add more
	memory.
	When using Windows 3.1, we require you run Windows in Enhanced
	mode while using Gahan Wilson's  - The Ultimate Haunted House in
	order to improve performance. To see if you are running Windows in
	Enhanced mode, from the Program Manager Help menu choose About
	Program Manager (or from the File Manager Help menu choose About File
	Manager). In the bottom section of the dialog box, you should see the
	phrase "386 Enhanced Mode." If you do not see this phrase, you can
	force Windows to run in Enhanced mode by typing WIN/3 or WIN/E at the
	DOS prompt when launching Windows. Windows for Workgroups always runs
	in Enhanced mode and no message is displayed in the About dialog box.
	When running Windows in Enhanced mode, set up a permanent Windows
	swap file on your hard disk. See your Windows User's Guide for more
	information.
	Defragment ("clean up") your hard disk by running a
	defragmentation program (MS-DOS 6.2 and above includes the program
	"defrag").
	
	CD-ROM Problems
	Do not remove Gahan Wilson's  - The Ultimate Haunted House compact
	disc from your CD-ROM while the program is running. If Gahan Wilson's
	The Ultimate Haunted House program cannot find the data files it
	needs from the compact disc, you'll see a message telling you the
	correct
	CD must be in the drive to continue. To find the source of the
	problem, do the following:
	Make sure Gahan Wilson's  - The Ultimate Haunted House compact disc
	is correctly inserted into the CD-ROM drive.
	
	Make sure you have the most recent versions of SmartDrive and MSCDEX
	(SmartDrive 5.0 and MSCDEX 2.23 are the most recent versions at the
	time of this release). The most recent version of SmartDrive can
	cache the CD-ROM drive, greatly improving performance. Make sure
	smartdrv is after MSCDEX in your Autoexec.bat. For information on the
	current SmartDrive settings type "smartdrv" at the DOS prompt. For
	help with SmartDrive type "smartdrv /?" at the DOS prompt or consult
	your DOS User's Guide.
	
	Make sure Gahan Wilson's  - The Ultimate Haunted House program is
	looking for the compact disc on the correct drive. Check to see if
	the drive letter for your CD-ROM drive has changed. You can use the
	Windows File Manager to determine which drive letter is assigned to
	the CD-ROM drive.  The Select Drive command in the Disk menu will say
	"CD-ROM" next to the CD-ROM drive letter.
	
	If you have an external CD-ROM drive, make sure the drive is
	connected to your computer, plugged in, and turned on. If you still
	see the error message after checking the points above, check the
	documentation that came with your CD-ROM drive or contact the company
	that supplied the drive.
	
	Make sure your CD-ROM drive is MPC2-compatible. An MPC2-compatible
	drive "has an average seek time of less than one second and can
	transfer data from the compact disc at 300K per second while using
	less than 40% of the CPU bandwidth." Check the documentation that
	came with your CD-ROM drive to make sure it meets these requirements.
	An incompatible CD-ROM drive will slow down the performance of Gahan
	Wilson's  - The Ultimate Haunted House.
	
	Video Display Problems
	
	Gahan Wilson's  - The Ultimate Haunted House is a 256 color
	application. In order to view Gahan Wilson's  - The Ultimate Haunted
	House properly, you need a video card which supports 256 colors in at
	least 640x480 resolution. Gahan Wilson's  - The Ultimate Haunted
	House requires you run in 256 color mode. If your computer is running
	in 16-color mode, and your video card will support 256 colors in at
	least 640x480 resolution, you should run Windows Setup to change the
	screen driver to see Gahan Wilson's  - The Ultimate Haunted House at
	256 (8-bit) colors. Check your Windows documentation for information
	on changing video drivers.
	
	If Gahan Wilson's  - The Ultimate Haunted House is too small on your
	screen, you are probably running in a resolution greater than
	640x480. To make Gahan Wilson's  - The Ultimate Haunted House fill
	the screen, run Windows Setup* and change your video driver to run in
	640x480 resolution
	with 256 colors. You will need to restart windows. Gahan Wilson's  -
	The Ultimate Haunted House will now fill the entire screen.
	
	* - (Some Video display adapters have a separate program you may have
	to run to change the display mode, see your display adapters user
	manual to check how to change your display resolutions)
	
	Make sure you are using the most recent Windows video drivers for
	your video card.  These may be obtained from your video card
	manufacturer.
	
	To find out what video driver you are using, go to the Windows
	Program Manager Main group window and double-click the Windows Setup
	icon. To the right of "Display" you will see the name of the video
	driver currently in use.
	
	Screen Savers:
	If you are running a screen saver of any kind, Gahan Wilson's  - The
	Ultimate Haunted House will continue to play unless you pause the
	game (CTRL-P) manually. Gahan Wilson's  - The Ultimate Haunted House
	will continue to count down time unless you pause the game manually.
	
	Dell S3 Drivers, versions 1.3 and 1.3a:
	If you have a Dell computer with S3 video and are using the Dell S3
	video drivers version 1.3 or 1.3a, you should install the latest
	driver. For details on installing this driver, contact Dell.
	
	ATI Mach Drivers
	Gahan Wilson's  - The Ultimate Haunted House is incompatible with
	some advanced features used by some video cards such as the Mach32
	chip set running the ATI drivers. For information about ATI video
	cards contact ATI Technical Support at (416) 756-0711.
	
	ATI Ultra Crystal Driver:
	The ATI ULTRA CRYSTAL driver will allow you to select a 256-color
	1024x768 display for a video card having 512K of memory. However,
	512K of memory will not support 256 colors at this resolution.
	Because Gahan Wilson's  - The Ultimate Haunted House requires 256
	colors to run
	properly, you must select a driver supporting a 256-color display.
	You must also make sure the video driver is compatible with your
	specific video card. For details on selecting an appropriate driver,
	see your ATI documentation or contact ATI technical support. A
	256-color SVGA driver is included with Windows for Workgroups. For
	details on installing this driver, see your Windows for Workgroups
	documentation.
	
	Obtaining Updated Drivers
	Contact the manufacturer of your video card to determine if newer
	Windows display drivers are available. Another option for obtaining
	updated drivers is the Microsoft Download service, an electronic
	bulletin board accessible via modem at (425) 936-MSDL(6735).
	
	Drivers provided on the MSDL are compressed with the PKWare
	utilities, and are in the form of executable files (.EXE extension).
	It is best to download the file or files you need into an empty
	directory on your hard disk or a blank formatted floppy. To
	decompress these drivers after downloading them, either:
	
	From Windows File Manager: double click on the filename (e.g., the
	appropriate file ending in .EXE) you downloaded.
	From the DOS prompt: change to the directory containing the
	downloaded file, type the filename, and press ENTER.
	
	The following video cards have been tested and give good results with
	Gahan Wilson's  - The Ultimate Haunted House:
	
	Model  Bus Date Driver Notes
	Actix ProStar VL VLB               8/18/93   1.42 Note 1
	ATI Graphics Ultra ISA             3/19/93   2.3
	ATI Graphics Ultra Plus ISA        4/25/94   2.3
	ATI Graphics Ultra Pro ISA & VLB   4/25/94   2.3
	Blackship Color DesignerA3 VLB     7/8/93    1.32
	Diamond Speed Star Pro ISA         2/17/94   1.08
	Diamond Speed Star VGA ISA         4/14/92
	Diamond Stealth 24 VLB             6/3/94    3.00
	Diamond Stealth Pro VLB            10/6/93
	ELSA Winner2000 Pro PCI            6/23/94   1.22
	Hercules Dynamite Pro ISA          12/1/93   2.10 Note 2
	Hercules Dynamite Pro VLB          12/1/93   3.00
	Hercules Graphite Power ISA        4/6/94    2.10
	IBM XGA Display MCA                11/12/93  2.11 Note 3
	Matrox MGA Power Graphics PCI      3/28/93
	Mitac MVA-CL5428-1MB VLB           3/15/94   V1.43
	Number Nine 9GXe Level 10 ISA      2/9/94    V3.11 Note 4
	Number Nine 9GXe Level 11 VLB      2/9/94    3.10.061 Notes 4, 5
	Number Nine 9GXe Level 14 VLB      4/7/94    3.15 Note 4
	Number Nine 9GXE64 VLB             6/22/94   1.19.04 Recommended
	Orchid Celsius VLB                 10/1/93   1.32 Recommended
	Orchid Fahrenheit 1280 Plus VLB    3/1/94    rel 7 Note 6
	Orchid Fahrenheit VA VLB           4/29/93   5.01
	Orchid Kelvin 64 PCI               3/14/94   1.1
	Orchid Kelvin 64 VLB               2/23/94   1.21
	Orchid ProDesigner IIS ISA         3/1/92    2.0
	Paradise WD90c33 VLB               6/28/93   1.2
	Standard 1Mb-24X ISA               3/19/93   1.30
	STB Horizon VL Pro VLB             6/29/93   1.3
	STB Lightspeed PCI                 12/1/93   1.1
	STB Pegasus VLB                    11/29/93  1.3
	TrueVision Bravado 8 ISA           1/15/92
	
	Note 1: Driver version 1.53 sometimes hangs when playing certain
	transitions.  Driver version 1.42 is recommended.
	Note 2: Does not always properly display QuickTime digital video in
	16 bit (thousands) and 24 bit (millions) color modes.
	Note 3: Does not draw extremely wide arcs properly.
	Note 4: There is sometimes sound break-up or distortion during
	complex transitions using most sound cards.
	Note 5: The cursor sometimes disappears when using a large virtual desktop.
	Note 6: Video snow appears during some palette transitions.
	
	Audio Problems
	Audio problems can have many causes. Other applications playing
	sounds may interrupt sounds in Gahan Wilson's  - The Ultimate Haunted
	House, because your computer cannot play two sounds simultaneously.
	This is generally a temporary clash that will resolve itself.
	However, a few
	applications that play sounds, such as some screen savers, may remove
	audio capability from all other Windows applications. If you suspect
	you have such an application, turn it off or do not run it while
	running Gahan Wilson's  - The Ultimate Haunted House.
	
	Sounds play, but not very well
	Distorted or "fuzzy" sounds have several possible causes. A likely
	cause is simply your speakers are not of high quality.
	
	It is also possible the software settings on your sound board are
	causing distortion. For example, if the sound card volume or "WAVE
	file input" is set to near its maximum, it will produce amplification
	distortion, just as it would on a stereo system. To find out how to
	change your sound board settings, check the documentation that came
	with your sound board
	
	Your CD-ROM drive should be MPC2-compatible. An MPC2-compatible drive
	"has an average seek time of less than one second and can transfer
	data from the compact disc at 300K per second while using less than
	40% of the CPU bandwidth." Check the documentation that came with
	your CD-
	ROM drive to make sure it meets these requirements. An incompatible
	CD-ROM drive may work but give lower-quality sound or cause the sound
	to be interrupted while playing.
	
	Sound doesn't play at all
	
	If you don't hear any sounds, make sure the volume for your speakers
	is set to an audible level.  If the volume is set to an audible level
	and you still hear no sounds at all, something may be wrong with your
	sound board setup. Check to see the driver is installed correctly
	and, if necessary, reinstall it. Refer to the documentation that came
	with your sound card for more information on installing audio
	drivers.
	
	Please note Gahan Wilson's  - The Ultimate Haunted House requires an
	MPC-compatible sound board to be installed and is not intended to run
	with drivers which use the PC internal speaker, such as the
	unsupported "PC Speaker" driver. Such a driver will in most cases not
	play any sounds, and if the driver setup option "Enable Interrupts"
	is not checked, your system may crash. If you have both a sound board
	and the PC Speaker driver installed, it is preferable to un-install
	the PC Speaker driver.
	
	Media Vision cards
	A small number of Media Vision sound card drivers (Pro Audio
	Spectrum cards) may cause problems. If you have a Media Vision card
	and don't hear speech but you hear music, you may need to upgrade
	your driver. Contact Media Vision Technical Support to find out how
	to obtain a new or updated driver.
	
	Ensoniq Soundscape cards
	The Ensoniq Soundscape card will not play sounds with the driver in
	the Windows driver default configuration. Try the following
	suggestion to improve audio performance.
	
	Problems with WAV files under Windows
	If you are having trouble hearing sound with WAV files, check the
	following:
	
	Go to your Drivers applet [Control Panel] and double-click on
	Soundscape DVD MIDI, WAVE, AUX.  Ensure that you have WAVE A setup as
	0 and that WAVE B is setup to Disable [Note: if there is something
	else in your system that is using those DMA channels, you will need
	to use another DMA setting such as 3].
	
	Contact Ensoniq Technical Support to find out how to obtain a new or
	updated driver.
	
	Sound Cards - General
	The following sound cards have been tested and are compatible with
	Gahan Wilson's  - The Ultimate Haunted House:
	
	Sound Card                         Notes and comments
	Compaq Business Audio
	Creative Labs SoundBlaster
	Creative Labs SoundBlaster Pro
	Creative Labs SoundBlaster 16
	Creative Labs SoundBlaster AWE32
	Gateway 2000
	IBM M-Audio                        Driver version 1.3 - Note 1
	MediaVision ProAudio Spectrum
	MediaVision ProAudio Spectrum 16
	MediaVision ProAudio Spectrum 16 Pro
	Microsoft Sound System Version 1
	Microsoft Sound System Version 2
	Orchid SoundWave 32
	Reveal Forte 16
	Roland Rap-10
	
	Note 1: IBM computers having the M-Audio sound card should use driver
	version 1.3 or higher for best results. Older versions of this driver
	don't play some sounds in Director or AVI movies.  The version 1.3
	driver does not pass the 16-bit sounds test for Director. Testing has
	revealed
	8 bit sounds are corrupted when played after a 16-bit sound. At the
	time these release notes were written, version 1.3 (dated 1/10/94)
	was the most recent driver available from IBM.
	
	Skipping the Introduction
	To skip the introduction, click the mouse button anytime while it's
	playing.
	
	Additional query words: kbhowto ensonic 1.00
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword kbKidsSearch kbHauntedHouse
	Version           : :1.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
