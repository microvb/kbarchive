---
layout: page
title: "Q142201: FIX: Running a Query from View Designer Causes Error Message"
permalink: /kb/142/Q142201/
---

## Q142201: FIX: Running a Query from View Designer Causes Error Message

{% raw %}

	Article: Q142201
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5,3.0
	Operating System(s): 
	Keyword(s): kbvfp kbvfp300bFIX kbMDAC250
	Last Modified: 03-AUG-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft Data Access Components version 2.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Using the Run Query option from the View Designer when modifying a previously
	created view results in a dialog box reporting "CTOD is not a recognized built
	in function name" for Remote Views and "Function argument value, type, or count
	is invalid" for Local Views.
	
	This only occurs for views using parameter values where one of the parameter
	values is compared to a date field and is followed by another selection
	criteria.
	
	CAUSE
	=====
	
	The View Designer wraps the CTOD() function around the parameter value used
	against the date field, when the view definition is read in.
	
	RESOLUTION
	==========
	
	Rearrange the selection criteria so that the date field comparison is the last
	line.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in version 3.0b.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	Remote View Example
	-------------------
	
	1. Use the ODBC Administrator to Create a Data Source to the SQL Server Pubs
	  database.
	
	2. Create a test database, and then create a connection to the SQL Data Source
	  created in step 1.
	
	3. Create a new remote view, choose the newly created connection, and then
	  select the Sales table. Select all the fields for output.
	
	4. Create a new parameter (param1) with the datetime data type.
	
	5. For the selection criteria use the following:
	
	     sales.ord_date   more than   ?param1
	     sales.stor_id    equal       6380
	
	6. Run the query and type "01/01/94" (without the quotation marks) for the
	  parameter. Two records should be returned.
	
	7. Save the query, modify it again, and then run it again. The following
	  connectivity error is generated:
	
	  CTOD is not a recognized built in function name"
	
	  View SQL shows that ?param1 has been enclosed within a CTOD() function call.
	  Removing the selection criteria and adding them again in the reverse order
	  prevents the error from occurring.
	
	Local View Example
	------------------
	
	1. Open the Vfp\Samples\Data\Testdata.dbc database.
	
	2. Create a new local view based on the Employee table.
	
	3. Select all the fields for output.
	
	4. Create a new parameter (param1) and give it a date data type.
	
	5. For the selection criteria use the following:
	
	     employee.birth_date   more than  ?param1
	     employee.last_name    like       P%
	
	6. Run the query and type "01/01/60" (without the quotation marks) for the
	  parameter. Two records should be returned.
	
	7. Save the query, modify it, and then run it again. The following error is
	  generated:
	
	  Function argument value, type, or count is invalid
	
	  View SQL shows that ?param1 has been enclosed within a CTOD() function call.
	  Removing the selection criteria and adding them again in the reverse order
	  prevents the error from occurring.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbvfp kbvfp300bFIX kbMDAC250 
	Technology        : kbVFPsearch kbAudDeveloper kbMDACSearch kbMDAC250 kbVFP300
	Version           : WINDOWS:2.5,3.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
