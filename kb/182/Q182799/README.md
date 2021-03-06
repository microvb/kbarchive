---
layout: page
title: "Q182799: SAMPLE: MMCTRL.EXE Demonstrates Using Multiple Sound Cards"
permalink: /kb/182/Q182799/
---

## Q182799: SAMPLE: MMCTRL.EXE Demonstrates Using Multiple Sound Cards

{% raw %}

	Article: Q182799
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbfile kbsample kbsound kbVBp500 kbVBp600 kbWaveAudio kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Mmmctrl.exe is a self-extracting compressed file that contains a Visual Basic
	project demonstrating how to detect and use multiple MCI devices in a system.
	The techniques shown and the Windows API functions used in this sample project
	allow your program to have multiple sound card support so you can enable one
	sound card for recording sounds and another sound card for playing sounds.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  Mmmctrl.exe
	  (http://download.microsoft.com/download/vb60ent/Sample6/1/W9XNT4/EN-US/Mmmctrl.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	When you run the self-extracting executable file, the following files are
	expanded to the Multiple Multimedia Control Sample project directory:
	
	- Form1.frm(11K)-the main form of the project
	
	- Module1.bas(18K)-the Basic module with the function declarations
	
	- Project1.vbp(1K)-the project file
	
	- Project1.vbw(1K)-the project workspace file
	
	- Readme.txt-you are currently reading this file.
	
	The next section shows how to start and use the sample project.
	
	How to Use the Sample Project
	-----------------------------
	
	When you run the project from the Visual Basic IDE, the Multiple Multimedia
	Control Sample form displays. The form is divided into a Play section and a
	Record section.
	
	The Play section has a Wave Output Devices list box that shows all the wave
	output devices available for playing wave files. Select one of the output
	devices in the list box. Open File shows a dialog box so you can select a wave
	file to play. The file name and path are displayed in the text box. When you
	select a wave file, the appropriate multimedia control buttons are enabled.
	
	If you select a file without selecting a wave device, the following error message
	displays:
	
	  The specified parameter is out of range for the specified command.
	
	To prevent displaying this error message, select a wave device before opening a
	file.
	
	The Record section also has a listbox that displays all wave input devices.
	Select one of the input devices in the list box. Open enables the selected wave
	input device for recording and enables the appropriate multimedia control
	buttons.
	
	If you check the Use Control Panel Recording Format check box, the wave input
	device will record in the format, sample rate, and number of channels set in the
	Multimedia Properties dialog box of Control Panel. If the Use Control Panel
	Recording Format check box is cleared, then the wave input device will record at
	the default MCI setting of 8-bit mono using a 11kHz sampling rate.
	
	Save opens a dialog box so that you can save the wave file you just recorded.
	
	How the Sample Works
	--------------------
	
	In the Form Load event, the number wave input and output devices are retrieved
	using the waveOutGetNumDevsA function for output devices and
	waveInGetNumDevCapsA function for input devices. The type and capabilities of
	each device are retrieved using the waveOutGetDevCaps for output devices and
	waveInGetDevCaps for input devices. The capabilities are stored in a
	user-defined variable. The name of each device is added to the appropriate list
	box.
	
	When you open a file to record or for playback, you also enable the appropriate
	multimedia control for this task. Depending on the multimedia control command
	you select, the event executes the appropriate mciSendCommandA function.
	
	If the Use Control Panel Recording Format check box is checked, the a user-
	defined function retrieves the Control Panel settings in the registry by first
	using the RegOpenKeyExA function to open the WaveFormats registry key. The
	RegQueryValueStringA and the RegQueryValueExA functions are used to retrieve the
	registry key values. The RegCloseKey is used to close the registry key.
	
	REFERENCES
	==========
	
	For more information about sound cards or using the multimedia API functions,
	please see the following topics:
	
	The Multimedia Reference in the Platform SDK Product Documentation
	
	Multimedia MCI Control in the Visual Basic Reference
	
	The following Windows API functions were used in this sample. For more
	information on these functions, please see the Platform SDK Product
	Documentation:
	
	- mciGetErrorStringA
	
	- mciSendCommandA
	
	- RegOpenKeyExA
	
	- RegQueryValueExA
	
	- RegCloseKey
	
	- waveOutGetDevCapsA
	
	- waveInGetDevCapsA
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q147811 : HOWTO: Detect If Computer Has Sound Card That Plays Wave Audio
	
	Additional query words: kbwin32sdk kbapi kbVBp kbdsd kbDSupport kbVBp500 kbVBp600
	
	======================================================================
	Keywords          : kbfile kbsample kbsound kbVBp500 kbVBp600 kbWaveAudio kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
