---
layout: page
title: "Q181720: PRB: MOVE 0 Works Only with RDO Server-Side Cursors"
permalink: /kb/181/Q181720/
---

## Q181720: PRB: MOVE 0 Works Only with RDO Server-Side Cursors

{% raw %}

	Article: Q181720
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 09-JAN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	"MOVE 0" fails to refresh the contents of a record with the current contents of
	the database after an UPDATE fails.
	
	CAUSE
	=====
	
	A client-side cursor is being used.
	
	RESOLUTION
	==========
	
	Make sure cursordriver is set to rdUseServer or rdUseIfNeeded. Some databases do
	not support server-side cursors.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The "MOVE 0" command is used to refresh a record to the current contents of the
	database after a failed update. The UPDATE failed because the contents of the
	record changed since the time it was originally retrieved for editing. The
	cursor must be a server-side cursor for MOVE 0 to work correctly. If the cursor
	is a client-side cursor, MOVE 0 will not refresh the contents of the record with
	the current contents of the database.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. In SQL Server Enterprise Manager, add two new fields to the Pub_Info table in
	  the Pubs database:
	
	  a. Open the Enterprise Manager and find the Pub_Info table in the Pubs
	     database.
	
	  b. Right-click the Pub_Info table and click Edit.
	
	  c. Add two new fields to this table. Name one field Pub_Name and make it
	     char(10) (allow NULL values). Name the second field WhatTime and make it a
	     timestamp field (also allow NULL values).
	
	  d. On the ISQL command window, issue the following query to initialize these
	     new fields:
	
	           UPDATE Pub_Info SET Pub_Name = 'Name'
	
	2. Start Visual Basic and create a new Standard EXE project. On the Project
	  menu, click References, and then check "Microsoft Remote Data Object 2.0."
	
	3. Place four command buttons on the form and paste the following code in the
	  form code window. Change dsName:=mymachine (below) to a datasource name on
	  your machine.
	
	        Option Explicit
	          Dim en As rdoEnvironment
	          Dim rs As rdoResultset
	          Dim cn As rdoConnection
	          Dim sqlstr As String
	
	        Private Sub Command1_Click()
	         sqlstr = "select * from pub_info"
	         Set rs = cn.OpenResultset(sqlstr, rdOpenKeyset, _
	            rdConcurRowVer)
	         Debug.Print rs(3)
	        End Sub
	
	        Private Sub Command2_Click()
	         rs.Edit
	         rs(3) = "McMillan"
	         Debug.Print rs(3) & " after edit"
	        End Sub
	
	        Private Sub Command3_Click()
	          On Error GoTo errhand
	          rs.Update
	          Exit Sub
	        errhand:
	          MsgBox Err.Number
	          rs.Move 0
	          Debug.Print rs(3) & " after move 0"
	        End Sub
	
	        Private Sub Command4_Click()
	          If Not (rs Is Nothing) Then
	            rs.Close
	           End If
	         cn.Close
	         Unload Me
	        End Sub
	
	        Private Sub Form_Load()
	         Set en = rdoEnvironments(0)
	         en.CursorDriver = rdUseClientbatch
	         Set cn = en.OpenConnection(dsName:="mymachine", _
	             Prompt:=rdDriverNoPrompt, _
	             Connect:="uid=sa;pwd=;database=PUBS;")
	         Command1.Caption = "resultset"
	         Command2.Caption = "edit "
	         Command3.Caption = "update"
	         Command4.Caption = "quit"
	        End Sub
	
	4. Make two copies of this project. In the second copy, change the following
	  line of code from
	
	        rs(3)="McMillan"
	
	  to the following:
	
	        rs(3)= "Schuster"
	
	  Run one of the projects. Click Resultset and then click Edit.
	
	5. Run the second copy of this project and click Resultset, click Edit and then
	  click Update. Return to the first instance of the project and click Update.
	  The 40002 error is trapped and the MOVE 0 command is executed.
	
	  NOTE: The immediate window does not show the current value in the database.
	  The value reverts to what the original query retrieved.
	
	6. Change rdUseClientBatch to rdUseServer or rdUseIfNeeded. The value displayed
	  in the debug window after the UPDATE error now shows the value currently in
	  the database. MOVE 0 does not refresh the record to the current value if
	  cursordriver is set to rdUseodbc or rdUseClientBatch.
	
	REFERENCES
	==========
	
	In Visual Basic Books Online see the following:
	
	  Guide to Building Client Server Applications in Visual Basic (Enterprise);
	  Choosing an RDO Cursor Type
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q168162 FIX: RDO Move 0 Fails to Refresh Record
	
	Additional query words: locking locktype rdconcurvalues kbVBp500 kbVBp600 kbRDO kbdse kbDSupport kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
