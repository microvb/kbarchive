---
layout: page
title: "Q262934: PRB: ADO Update Method Fails When SELECT Statement has Subquery"
permalink: /kb/262/Q262934/
---

## Q262934: PRB: ADO Update Method Fails When SELECT Statement has Subquery

{% raw %}

	Article: Q262934
	Product(s): Open Database Connectivity (ODBC)
	Version(s): 2.5,2.6,2.7,Build 2.573.2927,Build 2.573.3513,Build 2.573.3711,Build 2.573.4202,Build
	Operating System(s): 
	Keyword(s): kbDatabase kbODBC kbOracle kbGrpDSVCDB kbGrpDSMDAC kbDSupport kbMDAC250 kbADO250 kbMDAC
	Last Modified: 11-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC for Oracle version 2.5, versions Build 2.573.2927, Build 2.573.3513, Build 2.573.3711, Build 2.573.4202, Build 2.573.4403, Build 2.573.5303, Build 2.573.6019, Build 2.573.6526, Build 2.573.7326, Build 2.573.7626, Build 2.573.7713.2 
	- Microsoft Data Access Components versions 2.5, 2.6, 2.7 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you call the Update method of an ActiveX Data Objects (ADO) recordset that
	is opened on a SQL statement that also contains a sub-select using the Microsoft
	ODBC Driver for Oracle, then the following error message occurs:
	
	  [Microsoft][ODBC driver for Oracle]"Cannot use Keyset-driven cursor on join,
	  with distinct clause, union, intersect or minus or on read only result set"
	  State:S1C00,Native:0
	
	This error message does not occur if a SQL statement does not contain a
	sub-select.
	
	RESOLUTION
	==========
	
	Following are two possible work-arounds for this behavior:
	
	- Avoid sub-queries when you build an updateable rowset.
	
	- Set the cursor location to use client-side cursors.
	
	MORE INFORMATION
	================
	
	This error message occurs with all Microsoft ODBC Driver for Oracle versions.
	The following is an example of SQL statement with a sub-select:
	
	  SELECT fld1, fld2E FROM table1 WHERE EXISTS 
	  		(SELECT * FROM table2 WHERE table2.fld1 = table1.fld1)
	
	Microsoft ODBC Driver for Oracle returns the following run-time error when you
	use the Update method in ADO on a recordset using a SQL statement containing a
	sub-select, and when client side cursors are not used:
	
	  The operation requested by the application is not supported by the provider.
	
	You can view this Microsoft ODBC Driver for Oracle error message in the ODBC
	trace logs.
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	1. Create a system data source names (DSN) to connect to an Oracle 7.3.x/8x
	  server that uses Microsoft ODBC Driver for Oracle (Msorcl32.dll) version
	  2.573.4303 or earlier.
	
	2. Use SQL*PLUS, an Oracle command line utility, to run the following SQL
	  statements:
	
	  CREATE TABLE EMPTEMP(ID NUMBER(18, 0) CONSTRAINT PK_EMP 
	  PRIMARY KEY,NAME VARCHAR2(255));
	  CREATE TABLE JOBTEMP(EMP_ID NUMBER(18, 0) CONSTRAINT NL_JOB_1 
	  NOT NULL,
	      JOB_NAME VARCHAR2(255));
	  ALTER TABLE JOBTEMP ADD CONSTRAINT FK_JOB_EMP_ID FOREIGN KEY (EMP_ID)
	       REFERENCES EMPTEMP (ID) ON DELETE CASCADE;
	  INSERT INTO EMPTEMP VALUES (1, 'Marinko');
	  INSERT INTO EMPTEMP VALUES (2,  'Andreas');
	
	  INSERT INTO JOBTEMP VALUES (1, 'work hard');
	  INSERT INTO JOBTEMP VALUES (1, 'drink a coffee');
	  INSERT INTO JOBTEMP VALUES (2, 'work a lot');
	
	3. Use the following code to create an ADO-based Visual Basic 6.0 project with a
	  command button on the form. (See the comments in the code for information on
	  how to reproduce and resolve the error.)
	
	  Option Explicit
	  Const SQL_GOOD As String ="SELECT ROWID, ID, NAME FROM EMPTEMP"
	  Const SQL_BAD As String = "SELECT ROWID, ID, NAME FROM EMPTEMP " & _
	                            "WHERE EXISTS (SELECT * FROM JOBTEMP " & _
	                            "WHERE JOBTEMP.EMP_ID = EMPTEMP.ID AND " & _
	                            "JOBTEMP.JOB_NAME = 'work hard')"
	
	  Private Sub Command1_Click()
	
	      Dim cn As New ADODB.Connection
	      Dim rs As New ADODB.Recordset
	      Dim er As ADODB.Error
	      
	      On Error GoTo ErrorHandler
	      ' You need to change the DSN to valid the DSN on your system.
	      cn.Open "DSN=main80;UID=demo;PWD=demo"
	     
	      'If this is uncommented, you do not encounter any problems.
	  irrespective of the sql statement
	      'rs.CursorLocation = adUseClient 
	
	      'Toggle between the two SQL statements by 
	  interchanging the comment on the two statements.
	
	      'rs.Open SQL_BAD, cn, adOpenKeyset, adLockOptimistic
	      rs.Open SQL_GOOD, cn, adOpenKeyset, adLockOptimistic    
	
	      Debug.Print "support updates", rs.Supports(adUpdate)
	
	      rs.Fields("name").Value = "www"
	      rs.Update
	      
	      rs.Close
	      cn.Close
	      
	  Exit Sub
	      
	  ErrorHandler:
	
	      Debug.Print "run-time errors"
	      Debug.Print "---------------"
	      With Err
	          Debug.Print .Description
	          Debug.Print .Number
	      End With
	      
	      Debug.Print "ado errors"
	      Debug.Print "---------------"
	      For Each er In cn.Errors
	          With er
	              Debug.Print "Description:", .Description
	              Debug.Print "NativeError:", .NativeError
	              Debug.Print "Number:", .Number
	              Debug.Print "Source:", .Source
	              Debug.Print "SQLState:", .SQLState
	          End With
	      Next
	      
	  End Sub
	
	The Microsoft ODBC Driver for Oracle does not support positioned updates or
	deletes for SQL statements containing sub-selects.
	
	Additional query words: updateable updatable nested sub
	
	======================================================================
	Keywords          : kbDatabase kbODBC kbOracle kbGrpDSVCDB kbGrpDSMDAC kbDSupport kbMDAC250 kbADO250 kbMDAC260 
	Technology        : kbAudDeveloper kbODBCSearch kbMDACSearch kbMDAC250 kbMDAC260 kbODBCOracle25732927 kbODBCOracle25733513 kbODBCOracle25733711 kbODBCOracle25734202 kbODBCOracle25734403 kbODBCOracle25736526 kbMDAC270 kbodbcOracle25737626 kbodbcoracle25735303 kbODBCOracle25736019 kbODBCOracle25737326 kbODBCOracle257377132 kbODBCOracle250Search
	Version           : :2.5,2.6,2.7,Build 2.573.2927,Build 2.573.3513,Build 2.573.3711,Build 2.573.4202,Build 2.573.4403,Build 2.573.5303,Build 2.573.6019,Build 2.573.6526,Build 2.573.7326,Build 2.573.7626,Build 2.573.7713.2
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
