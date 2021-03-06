---
layout: page
title: "Q140575: PRB: Connectivity Error: Not a Recognized Built-in Function"
permalink: /kb/140/Q140575/
---

## Q140575: PRB: Connectivity Error: Not a Recognized Built-in Function

{% raw %}

	Article: Q140575
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:2.5,3.0
	Operating System(s): 
	Keyword(s): kbMDAC250
	Last Modified: 23-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft Data Access Components version 2.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When trying to run or browse a remote view, you may receive a Connectivity error
	similar to this one:
	
	  Connectivity error: [Microsoft][ODBC SQL Server Driver][SQL Server]'CTOD' is
	  not a recognized built-in function name
	
	CAUSE
	=====
	
	The CTOD function is added by the user as one of the Output fields, Order By, or
	Group By fields, or it is added by the View Designer as part of the Selection
	Criteria. CTOD is a FoxPro-specific function that is not recognized by the SQL
	Server.
	
	When browsing the Remote View, FoxPro passes the SQL command (listed in the
	Remote View SQL window) to the back-end server for execution. A connectivity
	error message is generated when any of the FoxPro-specific functions are passed
	to the back-end server.
	
	RESOLUTION
	==========
	
	The View Designer problem in Microsoft Visual FoxPro version 3.0 for Windows is
	fixed in Microsoft Visual FoxPro version 3.0b for Windows. In version 3.0, the
	view designer added the CTOD to the WHERE clause whenever a Selection Criteria
	on a Datetime field is added to the view. Version 3.0b does not add the CTOD
	automatically. Currently, 3.0b requires that the date in the example be
	surrounded by single quotation marks.
	
	Steps to Work Around Problem
	----------------------------
	
	1. Create an updatable View using SQL Passthrough. Use one of the SQL Server
	  built-in functions or remove whatever the View Designer added.
	
	  For information about creating an updatable View, please see the following
	  article in the Microsoft Knowledge Base:
	
	  Q138094 How to Create Updatable Views by Using SQL Passthrough
	
	  Following is an example of an SQLEXEC command that queries the Employee table
	  for a range of dates in the Hire_date field and then returns only the date
	  portion of the datetime field:
	
	        =SQLEXEC(Handle, "SELECT emp_id, ;
	           STR(datepart(month,hire_date),2) + '/';
	           + STR(datepart(day,hire_date),2) + '/' ;
	           + STR(datepart(year,hire_date),4) AS 'The_hire_date' ;
	           FROM employee ;
	           WHERE hire_date >= '01/01/93' AND hire_date <= '12/31/93'")
	
	  Note: STR() and datepart() are Microsoft SQL Servers built-in functions.
	
	2. Remove all FoxPro-specific functions from the Remote View.
	
	3. Create a Local view based on the Remote View.
	
	4. Add the necessary functions or selection criteria to the Local View.
	
	STATUS
	======
	
	Microsoft is researching this behavior and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a Remote View to a Microsoft SQL Server.
	
	2. Add some fields to the Selected Output using the Functions/Expressions
	  window, and use a FoxPro function such as ALLTRIM or DTOC.
	
	3. Add Selection Criteria using a Datetime type field.
	
	4. Browse the view.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbMDAC250 
	Technology        : kbVFPsearch kbAudDeveloper kbMDACSearch kbMDAC250 kbVFP300
	Version           : WINDOWS:2.5,3.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
