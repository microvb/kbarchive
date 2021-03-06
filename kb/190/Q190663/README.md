---
layout: page
title: "Q190663: PRB: Opening an ODBC Database Inside a Jet Workspace Hangs VB"
permalink: /kb/190/Q190663/
---

## Q190663: PRB: Opening an ODBC Database Inside a Jet Workspace Hangs VB

{% raw %}

	Article: Q190663
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 13-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Attempting to use a Jet workspace to open an ODBC datasource based on a Jet
	database can cause Visual Basic to hang. This is essentially causing Jet to talk
	to itself. This is not a supported way of accessing an Access/Jet database.
	
	RESOLUTION
	==========
	
	You can use an ODBC workspace to open an ODBC datasource based on a Jet
	database. You can also open a Jet database directly, without an using an ODBC
	datasource.
	
	STATUS
	======
	
	Microsoft is researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. In 32-bit ODBC Administrator, create a new File DSN based on the Access ODBC
	  driver. For the database, select the NWind.mdb file that is in the Visual
	  Basic program folder. Name the new File DSN NWind.
	
	2. In Visual Basic, create a new Standard EXE Project. Form1 is created by
	  default.
	
	3. Select the Project menu, and choose Remove Form1.
	
	4. Select Project, References and add a reference to the Microsoft DAO 3.51
	  Object Library.
	
	5. Select Project, Add Module to add a new code module. In the new module's code
	  window, add the following code:
	
	        Sub main()
	
	          Dim ws as DAO.Workspace
	          Dim db as DAO.Database
	          Set ws = CreateWorkspace("ws", "admin", "", dbUseJet)
	          Set db = ws.OpenDatabase("", , False, "odbc;")
	
	        End Sub
	
	6. Save the module as TestHang.BAS and the project as TestHang.VBP.
	
	7. Test the project:
	
	  a. Press F5 to run the code.
	     From the Select Data Source dialog box, select the NWind.dsn
	     File Data Source.
	     Visual Basic will hang.
	     Press CTRL+ALT+DEL to end the TestHang application and Visual Basic.
	
	  b. Restart Visual Basic.
	     Open the TestHang project.
	     In the code module, change the workspace from dbUseJet to dbUseODBC:
	     Set ws = CreateWorkspace("ws", "admin", "", dbUseODBC)
	     Press the F5 key to run the code.
	     From the Select Data Source dialog box, select the NWind.dsn
	     File Data Source.
	     Visual Basic will not hang.
	
	REFERENCES
	==========
	
	Microsoft Visual Basic Books Online, Guide to Data Access Objects
	
	Additional query words: kbDAO350 kbJET kbdse kbDSupport kbVBp kbVBp500 kbVBp600
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
