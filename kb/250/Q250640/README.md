---
layout: page
title: "Q250640: PRB: GetChunk Ignores Offset if Memo Field Included in GROUP BY"
permalink: /kb/250/Q250640/
---

## Q250640: PRB: GetChunk Ignores Offset if Memo Field Included in GROUP BY

{% raw %}

	Article: Q250640
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbJET kbVBp600 kbGrpDSVBDB kbDSupport kbDAO360bug
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Offset argument of the GetChunk method is used to set the number of bytes to
	skip before copying begins within a Memo or Long Binary Field.
	
	However, when the Memo field is included in the GROUP BY clause of the
	recordset's SELECT statement, the Offset argument is being ignored. This causes
	the characters from the beginning of the field to be retrieved instead of the
	characters beginning at the Offset position. For example, if the Memo field
	contains 500 characters and the Offset and Numbytes arguments are set to 250,
	GetChunk returns the first 250 characters instead of the last 250 characters as
	would be expected.
	
	RESOLUTION
	==========
	
	Rewrite the query to eliminate all Memo fields from the GROUP BY clause. This
	can be done by using an aggregate function on the Memo fields, such as the FIRST
	function. This allows the Memo fields to be removed from the GROUP BY clause.
	This workaround is illustrated in the example code below.
	
	MORE INFORMATION
	================
	
	Microsoft Jet 4.0 has new functionality that allows you to use MEMO fields (Long
	Varchar) in the GROUP BY clause of a SQL statement. This is not available in
	earlier versions of the Jet database engine.
	
	NOTE: The workaround SQL statement works with older versions of Jet.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. On the Project menu, select References, and add a reference to the Microsoft
	  DAO 3.6 object library.
	
	3. Add the following code to the Form_Load() Event:
	
	  Dim dbsNorthwind As Database
	  Dim rstEmployees As Recordset
	  Dim sQry As String
	  Const conChunkSize = 60
	  Dim lngOffset As Long
	  Dim lngTotalSize As Long
	  Dim strChunk As String
	      
	    Set dbsNorthwind = OpenDatabase("nwind.mdb")
	
	    'Comment this line out to see the correct behavior.
	    sQry = "SELECT FirstName, LastName, Notes FROM Employees " & _
	           "GROUP BY FirstName, LastName, Notes"
	
	    'Uncomment this line to see the correct behavior
	    'sQry = "SELECT Employees.LastName, Employees.FirstName, First(Employees.Notes) " & _
	            "AS Notes From Employees GROUP BY Employees.LastName, Employees.FirstName"
	
	    Set rstEmployees = dbsNorthwind.OpenRecordset(sQry, dbOpenDynaset)
	    Do While Not rstEmployees.EOF
	      lngTotalSize = rstEmployees("Notes").FieldSize
	      Do While lngOffset < lngTotalSize
	        strChunk = rstEmployees("Notes").GetChunk(lngOffset, conChunkSize)
	        Debug.Print strChunk
	        lngOffset = lngOffset + conChunkSize
	      Loop
	    lngOffset = 0
	    lngTotalSize = 0
	    rstEmployees.MoveNext
	    Loop
	
	NOTE: You might have to adjust the path to NWIND.MDB.
	
	4. The output from GetChunk is written to the Immediate Window, so make sure it
	  is visible. If it is not, choose Immediate Window from the View menu.
	
	5. Run the project, and note that the first 255 characters are repeated for all
	  Memo fields that contain more than 255 characters.
	
	6. Comment the first SQL statement and uncomment the second SQL statement.
	
	7. Run the project, and note that you see the complete text of all Memo fields.
	
	REFERENCES
	==========
	
	For additional information on how to use GetChunk, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q210486 ACC2000: Reading, Storing, and Writing Binary Large Objects
	
	Additional query words:
	
	======================================================================
	Keywords          : kbJET kbVBp600 kbGrpDSVBDB kbDSupport kbDAO360bug 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
