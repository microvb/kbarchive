---
layout: page
title: "Q275577: BUG: Parameter Placeholders with Visual FoxPro (VFP) ODBC Driver"
permalink: /kb/275/Q275577/
---

## Q275577: BUG: Parameter Placeholders with Visual FoxPro (VFP) ODBC Driver

{% raw %}

	Article: Q275577
	Product(s): Microsoft FoxPro
	Version(s): 3.0,4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbADO kbODBC kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbCod
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC Driver for Visual FoxPro (Build 6.00.8281.00), version 6.0 
	- Microsoft ODBC Driver for Visual FoxPro, versions 3.0, 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the Visual FoxPro (VFP) ODBC driver is used to write more than 1000 records
	to a table with more than 64 fields, one of the following errors may occur:
	
	- Fatal Error: Exception code C0000005 (most common).
	
	- System locks up or stops responding (hang).
	
	- Error message: "OLE Exception Error: Exception code C00000005. OLE Object may
	  be corrupt".
	
	- Error message (the variable name will vary): "-2147467259 [Microsoft] [ODBC
	  Visual FoxPro Driver] Variable 'Q876P55' is not found".
	
	CAUSE
	=====
	
	This behavior occurs when the table being accessed contains more than 64
	columns, and more than 999 records are inserted using parameter placeholders.
	
	RESOLUTION
	==========
	
	Avoid the use of parameter placeholders in SQL statements that are passed using
	SQL Pass Through.
	
	There is presently no resolution for situations that involve remote views of
	Visual FoxPro tables with more than 64 columns through the Visual FoxPro ODBC
	driver.
	
	There is currently no resolution for situations that involve ActiveX Data Objects
	(ADO) recordsets that access Visual FoxPro tables with more than 64 columns
	through the Visual FoxPro ODBC driver.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a program file named "MAKETBLS.PRG" using the following code:
	
	  * Create folder to contain the main database.
	  MKDIR DATA
	  * Create main database and 1 table with 65 fields.
	  CREATE DATABASE DATA\maindata
	  DO mk_it WITH 65
	  CLOSE ALL
	  * Create database to hold sample data of 2500 records. Also holds the
	  * connection to maindata.dbc and 3 views of the tables in maindata.dbc.
	  CREATE DATABASE testdata
	  DO mk_it WITH 65,.T.
	  * Populate the source data with 2500 records
	  FOR x = 1 TO 2500
	     IF MOD(x,500) = 0
	        WAIT WINDOW "Creating Dummy Recs: "+STR(x) NOWAIT
	     ENDIF
	     APPEND BLANK
	  ENDFOR
	  GO TOP
	  USE
	  * End of main program.
	
	  ************************************************************************************
	  * Procedure mk_it -
	  * Creates a table with the specified number of fields passed in cfcount.
	  * If ldefault is .t. then the procedure adds default values to each field of the table.
	  ************************************************************************************
	  PROCEDURE mk_it
	     PARAMETER ifcount, ldefault
	     IF PARAMETERS() < 2
	        ldefault = .F.
	     ENDIF
	     LOCAL i, cstatement, cfcount
	     cfcount= ALLTRIM(STR(ifcount))
	     * Sample data tables are placed in the root, the destination tables are placed
	     * in the data\ subdir.
	     cstatement="CREATE TABLE "+IIF(ldefault,"","data\")+"table"+cfcount+ ;
	        "(field_1 i PRIMARY KEY"+IIF(ldefault," default recno()","")+","
	     FOR i = 2 TO ifcount
	        cfcount= ALLTRIM(STR(i))
	        cstatement=cstatement+"field_"+cfcount+" c(8)"+IIF(ldefault," default sys(3)","") + ;
	           IIF(i=ifcount,")",",")
	     ENDFOR
	     * Create the table.
	     &cstatement
	     RETURN
	
	2. Save and then run the program.
	
	3. Create another program file named "FIELDS65.PRG" using the following code:
	
	  * TEST ON TABLE WITH 65 DATA ELEMENTS
	  CLOSE ALL
	  CLEAR ALL
	  CLEAR
	  * Make sure that main tables are empty before running this program
	  WAIT WINDOW "Cleaning up destination files" NOWAIT
	  SET SAFETY OFF
	  SET EXCLUSIVE ON
	  USE DATA\table65
	  ZAP
	  CLOSE ALL
	  CLEAR ALL
	  CLEAR
	
	  gnconnhandle=SQLSTRINGCONN("DRIVER=Microsoft Visual FoxPro Driver;" + ;
	     " SourceType=DBC;SourceDB="+SYS(5)+SYS(2003)+"\data\maindata.dbc")
	
	  ? "Inserting data from sample data to "+ALIAS()
	  SELE 0
	  USE table65
	  GO TOP
	  SCAN
	     WAIT WINDOW "Table65 - Updating "+STR(RECNO())+".  Please wait ..." NOWAIT
	     SCATTER MEMVAR MEMO
	     *	insert into vwtable65 from memvar
	     cmd="INSERT INTO table65 " + ;
	        "VALUES " + ;
	        "(?m.FIELD_1," + ;
	        "?m.FIELD_2," + ;
	        "?m.FIELD_3," + ;
	        "?m.FIELD_4," + ;
	        "?m.FIELD_5," + ;
	        "?m.FIELD_6," + ;
	        "?m.FIELD_7," + ;
	        "?m.FIELD_8," + ;
	        "?m.FIELD_9," + ;
	        "?m.FIELD_10," + ;
	        "?m.FIELD_11," + ;
	        "?m.FIELD_12," + ;
	        "?m.FIELD_13," + ;
	        "?m.FIELD_14," + ;
	        "?m.FIELD_15," + ;
	        "?m.FIELD_16," + ;
	        "?m.FIELD_17," + ;
	        "?m.FIELD_18," + ;
	        "?m.FIELD_19," + ;
	        "?m.FIELD_20," + ;
	        "?m.FIELD_21," + ;
	        "?m.FIELD_22," + ;
	        "?m.FIELD_23," + ;
	        "?m.FIELD_24," + ;
	        "?m.FIELD_25," + ;
	        "?m.FIELD_26," + ;
	        "?m.FIELD_27," + ;
	        "?m.FIELD_28," + ;
	        "?m.FIELD_29," + ;
	        "?m.FIELD_30," + ;
	        "?m.FIELD_31," + ;
	        "?m.FIELD_32," + ;
	        "?m.FIELD_33," + ;
	        "?m.FIELD_34," + ;
	        "?m.FIELD_35," + ;
	        "?m.FIELD_36," + ;
	        "?m.FIELD_37," + ;
	        "?m.FIELD_38," + ;
	        "?m.FIELD_39," + ;
	        "?m.FIELD_40," + ;
	        "?m.FIELD_41," + ;
	        "?m.FIELD_42," + ;
	        "?m.FIELD_43," + ;
	        "?m.FIELD_44," + ;
	        "?m.FIELD_45," + ;
	        "?m.FIELD_46," + ;
	        "?m.FIELD_47," + ;
	        "?m.FIELD_48," + ;
	        "?m.FIELD_49," + ;
	        "?m.FIELD_50," + ;
	        "?m.FIELD_51," + ;
	        "?m.FIELD_52," + ;
	        "?m.FIELD_53," + ;
	        "?m.FIELD_54," + ;
	        "?m.FIELD_55," + ;
	        "?m.FIELD_56," + ;
	        "?m.FIELD_57," + ;
	        "?m.FIELD_58," + ;
	        "?m.FIELD_59," + ;
	        "?m.FIELD_60," + ;
	        "?m.FIELD_61," + ;
	        "?m.FIELD_62," + ;
	        "?m.FIELD_63," + ;
	        "?m.FIELD_64," + ;
	        "?m.FIELD_65)"
	
	     sqlexec(gnconnhandle,cmd)
	
	  ENDSCAN
	
	  =sqldisconn(gnconnhandle)
	
	  IF AERROR(paerror) > 0
	     ?
	     ? "Errors Occurred"
	     DISP MEMORY LIKE paerror
	  ELSE
	     ? "Table65 update completed successfully"
	  ENDIF
	  WAIT WINDOW "finished" NOWAIT
	
	4. Save and then run the program.
	
	5. Note the error that occurs.
	
	REFERENCES
	==========
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by John
	Desch, Microsoft Corporation.
	
	
	Additional query words: Exception Hang
	
	======================================================================
	Keywords          : kbADO kbODBC kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet 
	Technology        : kbVFPsearch kbAudDeveloper kbODBCSearch kbODBCVFP300 kbODBCVFP400 kbODBCVFP500 kbODBCVFP600828100
	Version           : :3.0,4.0,5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
