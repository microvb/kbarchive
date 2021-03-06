---
layout: page
title: "Q247241: WhatsThisHelp.exe: Implement HTMLHelp &amp; WhatsThisHelp"
permalink: /kb/247/Q247241/
---

## Q247241: WhatsThisHelp.exe: Implement HTMLHelp &amp; WhatsThisHelp

{% raw %}

	Article: Q247241
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbfile kbsample
	Last Modified: 24-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	WhatsThisHelp.exe is a self-extracting file that has a sample of how to use
	"HTML Help" and "WinHelp" to fully utilize the Visual FoxPro help system.
	Utilizing custom classes and properties, both "HTML Help" and "What's This Help"
	can be implemented in Visual FoxPro.
	
	In previous versions of Visual FoxPro, the help system was based on "WinHelp". In
	Visual FoxPro version 6.0, "HTML Help" is now an option. However, "What's This
	Help" with "HTML Help" does not behave as expected. This article describes the
	steps necessary to implement "HTML Help" and produce the expected behavior of
	"What's This Help".
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  WhatsThisHelp.exe
	  (http://download.microsoft.com/download/vfox60/Utility/1.0/WIN98/EN-US/WhatsThisHelp.exe)
	
	Release Date: Mar-10-2000
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	To install the file, download it to any folder. Run the self extracting
	executable. It prompts you with the download location. After the files has been
	downloaded and extracted, run the program WhatsThis.exe.
	
	The following files are contained in the download file, WhatsThisHelp.exe:
	
	  Name                  Size
	  ---------------------------
	
	  DefaultHelp.htm         421
	  Htmlhelp.SCT          6,207
	  Htmlhelp.scx          2,559
	  Main.prg                 41
	  Myclasses.VCT         6,242
	  Myclasses.vcx         2,122
	  Readme.txt            8,853
	  TxtBox1.htm             347
	  TxtBox2.htm             347
	  TxtBox3.htm             374
	  WhatsThis.chm        11,390
	  WhatsThis.exe        25,208
	  WhatsThis.hhc         1,258
	  WhatsThis.hhk         1,466
	  WhatsThis.hhp           320
	  Whatsthis.hlp        10,623
	  WhatsThis.hpj           413
	  WhatsThis.PJT         4,323
	  WhatsThis.pjx         1,713
	  WhatsThis.rtf           676
	  --------------------------
	   20 file(s)          84,883
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	Visual FoxPro's "What's This Help" works with "HTML Help" right out of the box,
	but it does not produce the expected ontext-sensitive popup text. Instead, it
	displays the "What's This Help" in the HTML help browser. There are three steps
	that you can follow to get the correct behavior for the help system in Visual
	FoxPro.
	
	1. To make "What's This Help" work with "HTML Help", you need to be familiar
	  with both the "HTML Help" and "WinHelp" tools. You need to create two
	  different help files, an HTML Help file for the detailed help and a WinHelp
	  file for the "What's This Help" dialog boxes. For the "HTML Help" file, you
	  do not need to create HelpContextIDs, since you will be referring directly to
	  the HTML page. The other help file is created with WinHelp, and it is only
	  necessary to include the popup "What's This Help" topics.
	
	2. Create the class library necessary to run the forms. Create custom form and
	  control subclasses.
	
	  NOTE: See the following for the Property, Event or Method (PEMs)and download
	  instructions for the sample files.
	
	  Add a custom method to the form class to handle the call to the Help API. In
	  the custom controls, include a property named HelpTopic. This property is
	  evaluated at run-time to determine which page of the HTML help file to open.
	
	3. Create a new form and add your form subclass to it. When prompted to create a
	  formset, click Yes. Remove the other form, then the formset. Fill in the two
	  custom properties "HTMLHelpFile" and "WhatsThisHelpFile". Include the path,
	  if necessary, to the help files. Fill in the WhatsThisHelpID, if desired.
	  Now, place some of the custom classes on the form and assign values to their
	  HelpTopic and WhatsThisHelpID properties.
	
	The following is the sample form subclass code. Use this for reference only, as
	it cannot be used directly:
	
	  **************************************************
	  *-- Class:        mybaseform (myclasses.vcx)
	  *-- ParentClass:  form
	  *-- BaseClass:    form
	  *-- Time Stamp:   
	  *
	  DEFINE CLASS mybaseform AS form
	
	    Height = 248
	    Width = 401
	    DoCreate = .T.
	    AutoCenter = .T.
	    Caption = "HTMLHelp Sample"
	    MaxButton = .F.
	    MinButton = .F.
	    WindowType = 1
	    WhatsThisHelp = .T.
	    WhatsThisButton = .T.
	    *-- The help file to be used with the API call.
	    htmlhelpfile = ""
	    *-- Used for storing the help file before setting the help associated       *-- with the form.
	    oldhelpfile = ""
	    *-- Used exclusively for the WhatsThis help.  Must be a .HLP file for SET   *-- HELP TO
	    whatsthishelpfile = ""
	    Name = "mybaseform"
	
	    ADD OBJECT cmdclose AS mycommandbutton WITH ;
	      Top = 204, ;
	      Left = 158, ;
	      Height = 27, ;
	      Width = 84, ;
	      Cancel = .T., ;
	      Caption = "Close", ;
	      Name = "cmdClose"
	
	    *-- Calls the HTMLHelp API for objects on the form.
	    PROCEDURE htmlhelp32
	      *!*	Use this to fool the compiler, otherwise, an error is generated
	      *!*	when searching for the functions GetFocus and HtmHelpA
	      EXTERNAL ARRAY GetFocus, HtmHelpA
	
	      *!*	Help related define statements from htmlhelp.h in the
	      *!*	HTML Help WS folder.
	      #DEFINE HH_DISPLAY_TOPIC      0x0000
	      #DEFINE HH_DISPLAY_TOC        0x0001
	      #DEFINE HH_DISPLAY_INDEX      0x0002
	      #DEFINE HH_DISPLAY_SEARCH     0x0003 && not currently implemented
	      #DEFINE HH_HELP_CONTEXT       0x000F && display mapped numeric value
	                                           && in dwData
	
	      *!*	Get the HelpContextID of the active control.
	      LOCAL cHelpFile, wHnd, nCommand, cTopic
	      *!*	HTML help topic page
	      cTopic = ""
	
	      *!*   This is a custom property on the form.
	      *!*   It can be set in a base/sub class definition
	      cHelpFile = THISFORM.HTMLHelpFile
	
	      *!*   This is a custom property on the object.
	      *!*   It can be set in a base/sub class definition
	      IF VARTYPE(THISFORM.ACTIVECONTROL.HELPTOPIC) = 'C'
	        cTopic = THISFORM.ACTIVECONTROL.HELPTOPIC
	      ENDIF
	
	      *!*	Active window
	      hWnd = 0
	
	      *!* If there is not topic, goto TOC
	      nCommand = IIF(EMPTY(cTopic), HH_DISPLAY_TOC, HH_DISPLAY_TOPIC)
	
	      DECLARE INTEGER HtmlHelp IN "HHCtrl.ocx" AS "HtmHelpA" ;
	        INTEGER  nHWND, ;
	        STRING   cHelpFile, ;
	        INTEGER  nCommand, ;
	        STRING   cTopic
	
	      *!*	Get the active window handle
	      DECLARE INTEGER GetFocus IN "user32" AS "GetFocus"
	      wHnd = GetFocus()
	
	      IF hWnd = 0
	        =MESSAGEBOX("Unable to get window handle.")
	        RETURN
	      ENDIF
	
	      *!*	Call the HTML help system
	      nRetVal = HtmHelpA(@hWnd, @cHelpFile, @nCommand, cTopic)
	       RETURN
	    ENDPROC
	
	    PROCEDURE Destroy
	      *!*	The LostFocus and Deactivate do not fire when RELEASEd
	      ON KEY LABEL f1
	
	      *!*	Restore the old help system
	      SET HELP TO (THISFORM.OldHelpFile)
	    ENDPROC
	
	    PROCEDURE Deactivate
	      *!*	Clear the F1 key
	      ON KEY LABEL f1
	
	      *!*	Restore the old help system
	      SET HELP TO (THISFORM.OldHelpFile)
	    ENDPROC
	
	    PROCEDURE Activate
	      *!*	Save the old help file to restore on deactivation
	      THISFORM.OldHelpFile = SET('HELP', 1)
	      SET HELP TO (THISFORM.WhatsThisHelpFile)
	
	      *!*	Map the FoxPro help key to the active form's help routine
	      ON KEY LABEL F1 _SCREEN.ACTIVEFORM.HTMLHelp32()
	    ENDPROC
	
	    PROCEDURE cmdclose.Click
	      THISFORM.RELEASE()
	      CLEAR EVENTS
	    ENDPROC
	
	  ENDDEFINE
	  *
	  *-- EndDefine: mybaseform
	  **************************************************
	
	REFERENCES
	==========
	
	  Q197027 BUG: WhatsThisHelpID on Toolbar Does Not Function as Expected
	
	Additional query words: HTMLHELP, WINHELP, HELP, WHATSTHISHELP, WHATSTHISHELPID
	
	======================================================================
	Keywords          : kbfile kbsample 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
