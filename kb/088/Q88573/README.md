---
layout: page
title: "Q88573: Troubleshooting Autodial in Windows Cardfile"
permalink: /kb/088/Q88573/
---

## Q88573: Troubleshooting Autodial in Windows Cardfile

{% raw %}

	Article: Q88573
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1,3.11
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1, 3.11 
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides troubleshooting information for the Autodial feature in
	Microsoft Windows Cardfile. Autodial allows you to dial a number listed in a
	card by choosing Autodial from the Card menu or by pressing the F5 key.
	
	The following topics are discussed:
	
	- Configuring Cardfile
	
	- How Cardfile Looks for the Number to Dial
	
	- Dialing a Number with Fewer than Four Digits
	
	- Maximum Length of a Number You Can Dial with Cardfile
	
	- Telephone Number Formats That Cardfile Recognizes
	
	- Picking Up the Phone Causes Disconnect
	
	- Cardfile 3.0 Does Not Save Use Prefix Setting
	
	- Cardfile 3.1 Saves and Uses Only the First Four Characters of the Prefix
	
	- Cardfile Autodial Displays the Incorrect Phone Number When Using Go To
	
	- Cardfile Err Msg: Unable to Dial Number
	
	- Cardfile Err Msg: Cannot Dial the Number
	
	
	MORE INFORMATION
	================
	
	Configuring Cardfile
	--------------------
	
	If your modem does not make a connection when you use Autodial, there may be a
	problem with the COM port configuration settings. Try the following steps:
	
	1. From the Card menu, choose Autodial.
	
	2. Choose the Setup button.
	
	  The settings should most likely be set to:
	
	  Data Bits-8, Parity-None, Stop Bits-1
	
	  -or-
	
	  Data Bits-7, Parity-Even, Stop Bits-1
	
	  If the COM port setting is 7 data bits and no parity, Autodial does not work.
	  The only time parity should be set to none is if 8 data bits are being used.
	  (To correct this setting, see step 3, below.)
	
	  Autodial uses the Modem= and Prefix= settings in the [Windows] section of the
	  WIN.INI file. For example:
	
	  Modem=Com1,T,3
	  Prefix=9-
	
	  The Modem= parameters are COM(#) port; (T)one or (P)ulse; and Data Rate
	  setting as follows:
	
	     Setting    Data rate in bits per second (BPS)
	     ---------------------------------------------
	        0           110
	        1           300
	        2          1200
	        3          2400 (default)
	        4          4800
	        5          9600
	        6         19200
	
	  The Prefix= setting is used for phone lines that need an external access
	  number to dial out.
	
	3. If the settings in the WIN.INI file are correct for your hardware but you
	  still cannot make a connection when using Autodial, check the COM port
	  settings in Control Panel:
	
	  a. Run Control Panel.
	
	  b. From the Settings menu, choose Ports.
	
	  c. Select the appropriate COM port and choose the Settings button.
	
	How Cardfile Looks for the Number to Dial
	-----------------------------------------
	
	With Windows 3.0 and 3.1, when Cardfile autodials, it looks for the first number
	in the card with four or more digits. If the card contains a numeric entry with
	four or more digits that precedes the phone number entry, Cardfile attempts to
	dial that number.
	
	To force Cardfile to dial the number you want, you can either put the phone
	number as the first line in the Cardfile data area or put the phone number in
	the Index.
	
	Dialing a Number with Fewer Than Four Digits
	--------------------------------------------
	
	Autodial does not recognize a phone number with fewer than four digits. This
	prevents it from detecting a portion of an address as a phone number.
	
	If you want to use Autodial to dial a number with fewer than four digits, you can
	substitute hyphens for missing numbers.
	
	For example, to dial a person in the same building whose phone number is 123,
	place the number in the card as -123. Autodial ignores the hyphen and dials the
	three-digit number.
	
	Maximum Length of the Number You Can Dial with Cardfile
	-------------------------------------------------------
	
	When using Autodial in Cardfile version 3.0 and 3.1, the maximum length of the
	number you can dial is 33 characters. The prefix cannot exceed four characters.
	If your number exceeds the character limit, try eliminating hyphens.
	
	To dial a 33-character number, place the first 4 characters in the Prefix text
	box and the remaining 29 characters on the first line of the Card data area.
	Both the Prefix and Number should not contain non-numeric characters such as
	hyphens and parenthesis except those required by the modem, (a comma[,] for a
	pause).
	
	Telephone Number Formats That Cardfile Autodial Recognizes
	----------------------------------------------------------
	
	The Cardfile Autodial feature does not accept the following characters as
	separators in a telephone number:
	
	- "/" (forward, or front slash)
	
	- "\" (backward, or back slash)
	
	- "." (period)
	
	- " " (space)
	
	The "-" (hyphen, dash, or minus sign) separator works correctly, and Autodial
	dials the complete number.
	
	Examples:
	
	In the following format, Cardfile's Autodial ignores the area code:
	
	  555/555-5555
	
	Cardfile Autodial dials only 555-5555.
	
	Autodial also dials the following numbers incorrectly:
	
	  555-555/5555
	
	-or -
	
	  555-555.5555
	
	In both cases, Autodial dials 555-555 and ignores the last four digits.
	
	Autodialer recognizes and correctly dials either of the following telephone
	number formats:
	
	  5555555555
	
	-or-
	
	  555-555-5555
	
	Picking Up the Phone Causes Disconnect
	--------------------------------------
	
	Autodial prompts you to "Pick up the phone" as soon as you dial a number. If you
	do this, the modem does not go online, and the number cannot be dialed.
	
	To work around this problem, listen for the sound of the modem dialing, wait
	until the number has finished dialing, and then pick up the phone.
	
	Microsoft has confirmed this to be a problem in Cardfile versions 3.0 and 3.1. We
	are researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	Cardfile 3.0 Does Not Save the "Use Prefix" Setting
	---------------------------------------------------
	
	When using the Autodial feature of Cardfile 3.0, you must select the Use Prefix
	check box for the prefix to be dialed.
	
	Cardfile has no means of saving the Use Prefix setting. It must be re-selected
	each time you start Cardfile.
	
	Microsoft has confirmed this to be a problem in Cardfile version 3.0. This
	problem was corrected in Cardfile version 3.1.
	
	Cardfile 3.1 Saves and Uses Only the First Four Characters of the Prefix
	------------------------------------------------------------------------
	
	Cardfile version 3.1 saves only the first four character that appear in the
	Prefix text box. The characters are saved to the Prefix= line in the [Windows]
	section of the WIN.INI file. Even if the Prefix= line is modified manually to
	include more than four characters, Cardfile still recognizes only the first four
	characters of the prefix.
	
	Microsoft has confirmed this to be a problem in Cardfile version 3.1. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	Cardfile Autodial Displays an Incorrect Phone Number When You Use Go To
	-----------------------------------------------------------------------
	
	When you use the Go To (F4) command while in List View and then use Autodial,
	Cardfile version 3.1 displays the phone number for the card that was previously
	selected.
	
	To work around this problem, choose Card from the View menu before using the Go
	To command.
	
	Microsoft has confirmed this to be a problem in Cardfile version 3.1. We are
	researching this problem and will post new information here in the Microsoft
	Knowledge Base as it becomes available.
	
	For more information on using Cardfile, refer to pages 382-398 in the Microsoft
	Windows "User's Guide" for version 3.0 or pages 434-447 in the Microsoft Windows
	"User's Guide" for version 3.1.
	
	Cardfile Err Msg: Unable to Dial Number
	---------------------------------------
	
	You may receive the following error message when you use Autodial:
	
	  Unable to dial number;
	  Check to ensure the communication device is available
	
	This problem can occur when you have Terminal or another program loaded and set
	to access the same communications port that Cardfile is using. Cardfile Autodial
	does not work when the COM port is set to a port that is being used by another
	program.
	
	NOTE: If you are using an Intel SatisFAXtion 400i (an internal fax modem), you
	may be able to work around this problem by obtaining version 3.1 or later of the
	Intel SatisFAXtion DOWNLOAD.400 file. You can obtain the upgraded setup program
	(including version 3.1 of DOWNLOAD.400) from Intel Technical Support, the Intel
	forum on CompuServe, or the Intel support bulletin board service (BBS). The
	filename is 29.EXE
	
	Cardfile Err Msg: Cannot Dial the Number
	----------------------------------------
	
	You may receive the following error message when using Cardfile Autodial:
	
	  Cannot dial the number.
	  Check Control Panel to see that the modem is installed properly, and check the
	  modem cables to see that they are connected properly.
	
	The instructions in this error message are incorrect. Cardfile does not use
	Control Panel's modem settings. It uses its own modem settings, which are
	configured in Cardfile.
	
	To configure a modem for use with Cardfile, do the following:
	
	1. From the Card menu, choose Autodial, then choose the Setup button.
	
	2. Select the correct modem settings, then choose OK.
	
	
	Additional query words: tshoot 3.00 3.00a 3.10 3.11 wincard Card File Auto Dial cardfile.exe Win286 Win386 four 4 phone terminal applet accessory application err msg doc com port communications 3rdparty
	
	======================================================================
	Keywords          : win31 
	Technology        : kbAudDeveloper kbWin3xSearch kbWFWSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310 kbWin311 kbWFW310 kbWFW311
	Version           : WINDOWS:3.0,3.0a,3.1,3.11
	
	=============================================================================
	

{% endraw %}
