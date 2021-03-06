---
layout: page
title: "Q186378: FIX: Keywords in WHERE Clause Cause Oracle ODBC Driver Errors"
permalink: /kb/186/Q186378/
---

## Q186378: FIX: Keywords in WHERE Clause Cause Oracle ODBC Driver Errors

{% raw %}

	Article: Q186378
	Product(s): Open Database Connectivity (ODBC)
	Version(s): Build 2.73.7269,Build 2.73.7283.01,Build 2.73.7283.03
	Operating System(s): 
	Keyword(s): kbDatabase kbDriver kbODBC kbOracle kbVBp600fix kbODBC200bug kbODBC250 kbGrpDSVCDB kbGr
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC for Oracle version 2.0, versions Build 2.73.7269, Build 2.73.7283.01, Build 2.73.7283.03 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The Microsoft Oracle Driver parses the string contents of the WHERE clause for
	SQL keywords. For example:
	
	  SELECT * FROM PRBSPACE WHERE C1 = 'For Your Eyes Only'
	
	Some SQL keywords generate different errors. The SQL keywords must be followed by
	a space to cause the problem. The sample provided later shows the problem with
	the FOR and SELECT keywords. The problem is case insensitive and the ORDER and
	GROUP keywords also cause the same problem.
	
	STATUS
	======
	
	This has been fixed in the 2.573.2927 version or later of the Microsoft Oracle
	ODBC driver. The 2.573.2927 driver is available in Visual Studio 6.0 and
	Microsoft Data Access Components version 2.0.
	
	This also has been fixed in 2.573.4403.00 version of the Microsoft Oracle ODBC
	driver and is available in Microsoft Data Access Component (MDAC) version 2.5.
	
	The current MDAC components can be downloaded at from the following Web address:
	
	  http://www.microsoft.com/data/
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior in ODBCTest
	---------------------------------------
	
	First, create the table:
	
	  CREATE TABLE PRBSPACE (C1 VARCHAR(20))
	
	  INSERT INTO PRBSPACE VALUES ('For Your Eyes Only')
	  INSERT INTO PRBSPACE VALUES ('Select a Word')
	  INSERT INTO PRBSPACE VALUES ('This is a test')
	
	1. FULL CONNECT(Use Driver).
	
	2. SET CURSOR ATTRIBUTES
	
	  SQL_CURSOR_KEYSET_DRIVEN=1
	  SQL_CONCUR_VALUES=4
	
	  Click OK.
	
	3. Type the following SQL in the Execute window:
	
	  "SELECT * FROM PRBSPACE WHERE C1 = 'For Your Eyes Only'" (without the
	  quotation marks)
	
	4. SQLPrepare.
	
	5. SQLExecute.
	
	6. SQLBindCol.
	
	7. SQLExtendedFetch.
	
	RESULTS:
	
	Return: SQL_NO_DATA_FOUND=100
	
	To show that the steps above work, use the following SQL Statement:
	
	  SQLCancel
	
	Change the WHERE clause string to (this works):
	
	  SELECT * FROM PRBSPACE WHERE C1 = 'This is a test'
	
	Follow steps 4 through 7. No Error, and data is returned.
	
	To show that different KEYWORDS are effecting the query try the following:
	
	  SQLCancel
	
	Change the WHERE clause to:
	
	  SELECT * FROM PRBSPACE WHERE C1 = 'Select a Word'
	
	Follow steps 4 through 7. Now the error occurs on the SQLPrepare:
	
	  [Microsoft][ODBC driver for Oracle]Cannot use Keyset-driven cursor on join,
	  with distinct clause, union, intersect or minus or on read only result set.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbDatabase kbDriver kbODBC kbOracle kbVBp600fix kbODBC200bug kbODBC250 kbGrpDSVCDB kbGrpDSMDAC kbDSupport kbMDACNoSweep 
	Technology        : kbAudDeveloper kbODBCSearch kbODBCOracle2737269 kbODBCOracle273728303 kbODBCOracle273728301 kbODBCOracle200Search
	Version           : :Build 2.73.7269,Build 2.73.7283.01,Build 2.73.7283.03
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
