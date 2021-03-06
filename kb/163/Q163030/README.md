---
layout: page
title: "Q163030: PRB: Report Wizard Can Generate Detail Bands Too Large"
permalink: /kb/163/Q163030/
---

## Q163030: PRB: Report Wizard Can Generate Detail Bands Too Large

{% raw %}

	Article: Q163030
	Product(s): Microsoft FoxPro
	Version(s): 3.00b 3.00 5.00 6.00
	Operating System(s): 
	Keyword(s): kbHWMAC kbvfp kbvfp300 kbvfp300b kbvfp500 kbvfp600
	Last Modified: 26-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 6.0 
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Previewing or Running a report form generated by the Report Wizard generates
	error #1298, "Detail Band is too large to fit on page."
	
	CAUSE
	=====
	
	The report form's total length is larger than the paper size the printer is
	currently setup to print on.
	
	
	RESOLUTION
	==========
	
	Either adjust the report so the total length of the report does not exceed the
	size of the paper the printer is currently set to print on or if the printer
	driver supports it, use a custom defined page size.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	This error is not limited to the Report Wizard, it is also possible to manually
	create a Report in the Report Designer that causes the error.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Issue the following command in the Command window or a program file to create
	  a table with many fields:
	
	        CREATE TABLE temp ;
	        ( x0 c(10),x1 c(10),x2 c(10),x3 c(10),x4 c(10),;
	          x5 c(10),x6 c(10),x7 c(10),x8 c(10),x9 c(10),;
	          y0 c(10),y1 c(10),y2 c(10),y3 c(10),y4 c(10),;
	          y5 c(10),y6 c(10),y7 c(10),y8 c(10),y9 c(10),;
	          z0 c(10),z1 c(10),z2 c(10),z3 c(10),z4 c(10),;
	          z5 c(10),z6 c(10),z7 c(10),z8 c(10),z9 c(10),;
	          a0 c(10),a1 c(10),a2 c(10),a3 c(10),a4 c(10),;
	          a5 c(10),a6 c(10),a7 c(10),a8 c(10),a9 c(10),;
	          b0 c(10),b1 c(10),b2 c(10),b3 c(10),b4 c(10),;
	          b5 c(10),b6 c(10),b7 c(10),b8 c(10),b9 c(10))
	
	2. Start the Report Wizard.
	
	3. From the Wizard Selection dialog box click Report Wizard. Click OK.
	
	4. In Step 1 move all the fields over to the Selected Fields list.
	
	5. Click Next until you get to the "Define Report Layout" step.
	
	6. In the "Define Report Layout" step, click Rows for Field Layout. Click
	  Finish.
	
	7. In the "Finish" step, click "Save report and modify it in the Report
	  Designer." Click Finish again.
	
	8. Give the report a name and choose Save.
	
	9. When the report comes up, select Print Preview from the File menu.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHWMAC kbvfp kbvfp300 kbvfp300b kbvfp500 kbvfp600 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac kbVFP300 kbVFP300b kbVFP500 kbVFP600
	Version           : 3.00b 3.00 5.00 6.00
	
	=============================================================================
	

{% endraw %}
