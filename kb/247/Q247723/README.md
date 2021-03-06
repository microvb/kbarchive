---
layout: page
title: "Q247723: BUG: VBCE Control Manager Only Recognizes First Control in DLL"
permalink: /kb/247/Q247723/
---

## Q247723: BUG: VBCE Control Manager Only Recognizes First Control in DLL

{% raw %}

	Article: Q247723
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 1.0,2.0,2.11,6.0
	Operating System(s): 
	Keyword(s): kbActiveX kbToolkit kbVBp600bug kbGrpDSVB kbOSWinCE211
	Last Modified: 26-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows CE Toolkit for Visual Basic 6.0, version 1.0 
	- Microsoft Windows CE Toolkit for Visual C++ 6.0, on platform(s):
	   - Microsoft Windows CE versions 2.0, 2.11 for the Handheld PC 
	   - Microsoft Windows CE version 2.11 for the Palm-size PC 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Because the Windows CE Toolkit for Visual Basic (VBCE) does not support control
	creation, it is common to create ActiveX controls with the Windows CE Toolkit
	for Visual C++ (VCCE) and host them on VBCE forms.
	
	When a VCCE DLL contains multiple ActiveX controls or property pages and is
	registered using the Control Manager so that you can host the controls on VBCE
	forms, the controls are added to the Visual Basic toolbox, but only the first
	control can be added to the form.
	
	The problem only occurs on the Handheld PC Pro and Palm-size PC platforms.
	
	CAUSE
	=====
	
	The problem is caused by a bug in the Control Manager, which only recognizes the
	GUID of the first control in the VCCE DLL.
	
	RESOLUTION
	==========
	
	The workaround is to have one ActiveX control per DLL. If the control needs to
	have property pages, make sure that the GUID for the control itself is listed
	first in the IDL file instead of the property pages.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	This article is based on the assumption that you are already familiar with
	creating ActiveX controls for Microsoft Windows CE in VCCE and that such
	controls have already been created. To learn more about the topic, please check
	the white paper listed in the "References" section of this article.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Launch Microsoft Visual Basic and create a new Windows CE HPC/Pro or PsPC
	  project. Form1 is created by default.
	
	2. From the Windows CE menu, choose Control Manager.
	
	3. Expand Palm-size PC 2.11 or H/PC Pro 2.11 in the left pane.
	
	4. Select the Desktop Design Controls option for the desired platform.
	
	5. From the Control menu, choose Add New Control, and then browse to the VCCE
	  DLL that contains multiple ActiveX controls. Now the VCCE DLL is registered
	  in the desktop design environment and you should be able to host the control
	  on VBCE forms.
	
	6. From the Project menu, choose Components, and then check the VCCE DLL from
	  the list. Now the controls in that DLL appear in the Toolbox.
	
	7. Add each of the controls in the DLL to Form1. Note only the first control
	  appears on the form.
	
	REFERENCES
	==========
	
	For information on how to create ActiveX controls for Microsoft Windows CE,
	please check the white paper at:
	
	  http://msdn.microsoft.com/library/techart/activexce.htm
	  (http://msdn.microsoft.com/library/techart/activexce.htm)
	
	Additional query words: vbce vbce6
	
	======================================================================
	Keywords          : kbActiveX kbToolkit kbVBp600bug kbGrpDSVB kbOSWinCE211 
	Technology        : kbVCsearch kbVBSearch kbAudDeveloper kbWinCETKVBSearch kbWinCETKVCSearch kbWinCESearch
	Version           : :1.0,2.0,2.11,6.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
