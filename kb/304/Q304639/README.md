---
layout: page
title: "Q304639: HOWTO: Find PaperSize for Custom Print Sizes Under Windows NT/2K"
permalink: /kb/304/Q304639/
---

## Q304639: HOWTO: Find PaperSize for Custom Print Sizes Under Windows NT/2K

{% raw %}

	Article: Q304639
	Product(s): Microsoft FoxPro
	Version(s): 6.0,7.0
	Operating System(s): 
	Keyword(s): kbprint kbAPI kbPrinting kbvfp kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 6.0, 7.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Windows NT 4.0 and Windows 2000 do not respect custom paper sizes as Windows 95
	and later do. The custom paper size is stored in the report header, under
	PaperSize in the EXPR field. Under Windows 95 and later, the PaperSize for
	custom is 256, with PaperLength and PaperWidth controlling the actual size.
	Under Windows NT 4.0 and later, the custom size must correspond to a predefined
	form.
	
	To determine the correct PaperSize to use for a Windows NT 4.0 or Windows 2000
	report, you must use Windows API calls. This article includes code that
	demonstrates how to determine the name and size of the forms that are installed
	on your system.
	
	MORE INFORMATION
	================
	
	In Windows 95, you can select the paper size Custom, and then select the page
	height and width. Under NT-based systems, to print to a custom size, you must
	select a printer form, which specifies the paper size. To view the different
	forms that are available on your system, open the Printers window, and click
	Server Properties on the File menu. You may not be able to directly select all
	of these from Visual FoxPro.
	
	The number of the form is stored in the report header, under PaperSize in the
	EXPR field. To view this, USE the report as a table (USE myReport.frx), BROWSE
	it, and double-click the Memo in the first line of the EXPR field. The default
	PaperSize can also be displayed with the PRTINFO(2) function.
	
	This code requires Christof Lange's STRUCT.VCX class, which can be downloaded at
	various sites on the Internet, including the following:
	
	  Universal Thread
	  http://www.universalthread.com (http://www.universalthread.com/)
	
	  SET PATH TO c:\STRUCT  && Change this to be wherever you unzipped the class.
	  SET CLASSLIB TO STRUCT.vcx
	
	  CLEAR ALL
	  CLEAR
	
	  *!* Windows API call to list printer forms.
	  DECLARE LONG EnumFormsA IN winspool.drv AS EnumForms ;
	     LONG hPrinter, LONG Level, LONG pForm, ;
	     LONG cbBuf, LONG @pcbNeeded, ;
	     LONG @ pcReturned
	     
	  *!* Windows API call to get a printer handle.
	  DECLARE LONG OpenPrinterA IN winspool.drv AS OpenPrinter ;
	     STRING pPrinterName, LONG @ phPrinter, LONG pDefault
	
	  phPrinter = 0   && Define printer handle for pass-by-reference
	  *!* You do not pass a specific printer here, because the custom form
	  *!* is defined on the local computer.
	  lnRetVal = OpenPrinter(0, @phPrinter, 0)
	  IF lnRetVal = 0
	     MESSAGEBOX("OpenPrinter failed!")
	     RETURN
	  ENDIF
	
	  *!* Create structure to hold returned printer forms.
	  loForms = CREATEOBJECT("clsPrinterForms")
	
	  *!* Define variables for pass-by-reference.
	  lnFormsPtr = loForms.GetPointer(255)
	  lnBytesNeeded = 0
	  lnFormCount = 0
	
	  *!* lnRetVal will indicate that this next call failed. This is because
	  *!* it was told to return 0-length information.
	  *!* The second call should work properly.
	  lnRetVal = EnumForms(phPrinter, 1, lnFormsPtr, 0, @lnBytesNeeded, ;
	     @lnFormCount)
	  loForms.FreePointer(lnFormsPtr) && clean up memory
	
	  *!* Get the proper memory size reserved, and call EnumForms.
	  lnFormsPtr = loForms.GetPointer(lnBytesNeeded)
	  lnRetVal = EnumForms(phPrinter, 1, lnFormsPtr, lnBytesNeeded, ;
	     @lnBytesNeeded, @lnFormCount)
	  IF lnRetVal = 0
	     MESSAGEBOX("EnumForms call failed")
	     loForms.FreePointer(lnFormsPtr) && clean up memory
	     RETURN
	  ENDIF
	
	  *!* When you defined the PrinterForms class, you didn't know how many forms
	  *!* were being returned. Now that you do, you need to redimension the array
	  *!* property to hold the proper number of forms, and get them ready to hold 
	  *!* the form information.
	  DIMENSION loForms.aForms[lnFormCount]
	  FOR i = 1 TO lnFormCount
	     loForms.aForms[i] = CREATEOBJECT("clsFormInfo")
	  ENDFOR
	
	  *!* Take the memory pointer you received, and break it up into the objects you 
	  *!* defined below.
	  loForms.SetPointer(lnFormsPtr)
	
	  loForms.FreePointer(lnFormsPtr) && clean up memory
	
	  FOR i = 1 TO lnFormCount
	     loForm = loForms.aForms[i]
	     
	     *!* i is what you would see in PaperSize in the Expr field, or in 
	     *!* the PRTINFO() function. The Size.cx and cy values are in 1000ths
	     *!* of a millimeter: there are 25.4 millimeters to an inch.
	     ? i, PADR(loForm.pName, 30), loForm.Size.cx / 25400, loForm.Size.cy / 25400
	  ENDFOR
	
	  RETURN
	
	  *!* The class properties correspond to the members of the structures,
	  *!* and cMembers indicates what type of variables are in the return
	  *!* from the API call. "l:" indicates a long, "o:" indicates 
	  *!* a structure, and "pz:" indicates a pointer to a null-terminated 
	  *!* string.
	  *!* See Struct.vcx documentation for more information about the STRUCT 
	  *!* class and its settings.
	  DEFINE CLASS clsPrinterForms AS STRUCT
	     DIMENSION aForms[1]
	     cMembers = "o:aForms"
	
	     nMemorySize = 100000  && Reserve memory for pointers
	
	     PROCEDURE INIT
	        This.aForms[1] = CREATEOBJECT("clsFormInfo")
	        DODEFAULT()
	     ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS clsFormInfo AS STRUCT
	     flags = 0
	     pName = ""      && form name
	     Size = .NULL.   && paper size
	     ImageableArea = .NULL.
	
	     cMembers = "l:flags, pz:pName, o:size, o:imageableArea"
	
	     PROCEDURE INIT
	        This.Size  = CREATEOBJECT("clsSizeL")
	        This.ImageableArea = CREATEOBJECT("clsRectL")
	        DODEFAULT()
	     ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS clsSizeL AS STRUCT
	     cx = 0   && paper width
	     cy = 0   && paper height
	
	     cMembers = "l:cx, l:cy"
	  ENDDEFINE
	
	  DEFINE CLASS clsRectL AS STRUCT
	     nLeft = 0
	     nTop = 0
	     nRight = 0
	     nBottom = 0
	
	     cMembers = "l:nLeft, l:nTop, l:nRight, l:nBottom"
	  ENDDEFINE
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	REFERENCES
	==========
	
	For additional information about OpenPrinter and EnumForms, see the Platform
	Software Development Kit (SDK) documentation in the Microsoft Developer Network
	(MSDN) library.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbprint kbAPI kbPrinting kbvfp kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600 kbVFP700
	Version           : :6.0,7.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
