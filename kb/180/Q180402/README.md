---
layout: page
title: "Q180402: PRB: MFC ActiveX Control Ignores ARROW Keys on VB Container"
permalink: /kb/180/Q180402/
---

## Q180402: PRB: MFC ActiveX Control Ignores ARROW Keys on VB Container

{% raw %}

	Article: Q180402
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0,97; winnt:5.0,6.0
	Operating System(s): 
	Keyword(s): kbCtrlCreate kbVBp kbVBp500 kbVBp600 kbVC500 kbVC600 kbVS97 kbVS600 _IK kbControl
	Last Modified: 18-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An MFC ActiveX Control that contains a subclassed Edit control does not respond
	to the ARROW keys. More specifically, when a Visual Basic form contains the MFC
	ActiveX Control and the control has focus, the ARROW keys are not recognized.
	
	CAUSE
	=====
	
	This behavior is the result of ARROW keys being accelerator keys. Accelerator
	keys are handled in the main message loop of the containing application before
	the window procedure of the control is called. As a result, the MFC ActiveX
	control is not aware that the ARROW keys have been pressed. Other accelerator
	keys include the TAB, END, and HOME keys.
	
	RESOLUTION
	==========
	
	The problem can be resolved by adding the following code to your MFC ActiveX
	Control. This code forwards the Accelerator Key messages onto your MFC ActiveX
	Control:
	
	     // Trap keys and forward on to the control.
	     BOOL CMyEditCtrl::PreTranslateMessage(MSG* pMsg)
	     {
	        switch (pMsg->message)
	        {
	           case WM_KEYDOWN:
	           case WM_KEYUP:
	              switch (pMsg->wParam)
	              {
	                 case VK_UP:
	                 case VK_DOWN:
	                 case VK_LEFT:
	                 case VK_RIGHT:
	                 case VK_HOME:
	                 case VK_END:
	                    SendMessage (pMsg->message, pMsg->wParam, pMsg->lParam);
	                    // Windowless controls won't be able to call SendMessage.
	                    // Instead, just respond to the message here.
	                    return TRUE;
	              }
	              break;
	        }
	        return COleControl::PreTranslateMessage(pMsg);
	     }
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Using the MFC ActiveX Control Wizard, create a MFC control that subclasses an
	  Edit Control.
	
	2. Compile the .ocx.
	
	3. Add this MFC ActiveX .ocx to a Visual Basic form and run the project.
	
	4. Type some text in the Edit Control and attempt to use the ARROW keys to
	  navigate through the typed text. The ARROW keys are not recognized.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q168777 PRB: MFC ActiveX Control in IE Doesn't Detect Keystrokes
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCtrlCreate kbVBp kbVBp500 kbVBp600 kbVC500 kbVC600 kbVS97 kbVS600 _IK kbControl 
	Technology        : kbVCsearch kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : WINDOWS:5.0,6.0,97; winnt:5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
