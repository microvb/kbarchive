---
layout: page
title: "Q150392: PRB: LoadLibrary &amp; FreeLibrary on MFC Regular DLL Leak Memory"
permalink: /kb/150/Q150392/
---

## Q150392: PRB: LoadLibrary &amp; FreeLibrary on MFC Regular DLL Leak Memory

{% raw %}

	Article: Q150392
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.1
	Operating System(s): 
	Keyword(s): kbcode kbDLL kbMFC kbVC kbArchitecture
	Last Modified: 03-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When calling LoadLibrary followed by FreeLibrary on an MFC regular DLL, and
	watching the memory allocations associated with the calling program, you see
	that four memory objects are not freed when the DLL is unloaded.
	
	CAUSE
	=====
	
	The memory allocated for the m_pszExeName, m_pszAppName, m_pszHelpFilePath, and
	m_pszProfileName members of the DLL's CWinApp-derived object is not
	automatically released when the DLL unloads.
	
	RESOLUTION
	==========
	
	If you have not added references or changes to these variables in your code, you
	can release the allocated memory manually by doing one of the following two
	procedures:
	
	- If no other global or static objects except the global CWinApp-derived object
	  rely on the strings, free the memory for them in the destructor of the global
	  CWinApp-derived object. For example:
	
	     CDllAppObject::~CDllAppObject()
	     {
	       if(m_pszExeName)
	         m_pszExeName = GlobalFree(m_pszExeName);
	
	       if(m_pszAppName)
	         m_pszAppName = GlobalFree(m_pszAppName);
	
	       if(m_pszHelpFilePath)
	         m_pszHelpFilePath = GlobalFree(m_pszHelpFilePath);
	
	       if(m_pszProfileName)
	         m_pszProfileName = GlobalFree(m_pszProfileName);
	     }
	
	  -or-
	
	- If other global or static objects rely on these strings, then free the memory
	  allocated for them in your own implementation of the RawDllMain function. The
	  RawDllMain function is called by the C Runtime after all global or static
	  objects have had their destructors called. NOTE: Due to the complexity of
	  this procedure and the knowledge that MFC's RawDllMain implementation may
	  change in future versions of MFC, this approach is not recommended unless
	  absolutely necessary. To gain access to and be able to delete the strings in
	  your version of RawDLLMai, you must declare four global variables and
	  initialize them in the DLL's CWinApp-derived object's InitInstance. For
	  example:
	
	        LPCTSTR g_pszExeName = NULL;
	        LPCTSTR g_pszAppName = NULL;
	        LPCTSTR g_pszHelpFilePath = NULL;
	        LPCTSTR g_pszProfileName = NULL;
	
	        BOOL CHeapDllApp::InitInstance()
	        {
	          if(CWinApp::InitInstance())
	          {
	            g_pszExeName = m_pszExeName;
	            g_pszAppName = m_pszAppName;
	            g_pszHelpFilePath = m_pszHelpFilePath;
	            g_pszProfileName = m_pszProfileName;
	
	            return TRUE;
	          }
	          else
	            return FALSE;
	        }
	
	  Then, in your version of RawDllMain, call GlobalFree on the global pointers
	  when the reason for calling is DLL_PROCESS_DETACH. For example:
	
	        extern LPCTSTR g_pszExeName;
	        extern LPCTSTR g_pszAppName;
	        extern LPCTSTR g_pszHelpFilePath;
	        extern LPCTSTR g_pszProfileName;
	
	        extern "C"
	        BOOL WINAPI RawDllMain(HINSTANCE, DWORD dwReason, LPVOID)
	        {
	          if (dwReason == DLL_PROCESS_ATTACH)
	          {
	            // ... Code abbreviated from DLLMODUL.CPP
	          }
	          else if (dwReason == DLL_PROCESS_DETACH)
	          {
	            // restore module state after cleanup
	            AFX_MODULE_STATE* pModuleState = AfxGetStaticModuleState();
	            _AFX_THREAD_STATE* pState = AfxGetThreadState();
	            VERIFY(AfxSetModuleState(pState->m_pPrevModuleState) ==
	              pModuleState);
	            DEBUG_ONLY(pState->m_pPrevModuleState = NULL);
	
	            #ifndef _AFXDLL
	              AfxCriticalTerm();
	            #endif
	
	            // NEW CODE ADDED HERE
	            // -------------------
	
	            if(g_pszExeName)
	              GlobalFree((HGLOBAL)g_pszExeName);
	
	            if(g_pszAppName)
	              GlobalFree((HGLOBAL)g_pszAppName);
	
	            if(g_pszHelpFilePath)
	              GlobalFree((HGLOBAL)g_pszHelpFilePath);
	
	            if(g_pszProfileName)
	              GlobalFree((HGLOBAL)g_pszProfileName);
	          }
	
	          return TRUE;
	        }
	
	If you have added references or modified the contents of these pointer variables,
	you need to free them in a manner appropriate to your usage. If you used the
	second procedure and changed the location that one of these variables points to
	after saving the address in InitInstance, the code added to RawDllMain frees the
	old (wrong) contents of memory and not the new contents that you allocated. When
	using the first procedure, make sure you free the old contents pointed to by the
	particular variable as well as any strings you have allocated yourself.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The m_pszExeName, m_pszAppName, m_pszHelpFilePath, and m_pszProfileName members
	of CWinApp are allocated in the CWinApp::SetCurrentHandles function (APPINIT.CPP
	line 107 in version 4.1). SetCurrentHandles is called during the initialization
	of a Regular DLL by default.
	
	The MFC source code in SetCurrentHandles says the following regarding the memory
	allocations for these CWinApp strings and why the memory is not automatically
	released:
	
	NOTE: there are a number of _tcsdup (aka strdup) calls that are made here for the
	exe path, help file path, and so on. This memory is not freed and will be
	reported by various memory diagnostic utilities. This is not a bug. These
	strings cannot be freed because they may be set by the application to anything,
	even something that is not on the heap. Furthermore, they may be accessed at any
	time, including during destructor calls. Because the order of destructor calls
	with respect to the CWinApp object and any other objects in the program is not
	deterministic, the CWinApp object cannot free this memory.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q148791 How to Provide Your Own DllMain in an MFC Regular DLL
	
	It describes how to provide your own DllMain function and applies to replacing
	the RawDllMain function found in Dllmodul.cpp.
	
	Additional query words: 4.00 4.10
	
	======================================================================
	Keywords          : kbcode kbDLL kbMFC kbVC kbArchitecture 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:4.0,4.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
