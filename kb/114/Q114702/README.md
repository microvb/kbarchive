---
layout: page
title: "Q114702: How to Use the LIKE and EXCEPT Clauses"
permalink: /kb/114/Q114702/
---

## Q114702: How to Use the LIKE and EXCEPT Clauses

{% raw %}

	Article: Q114702
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.6; WINDOWS:2.6,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, version 2.6 
	- Microsoft FoxPro for MS-DOS, version 2.6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In FoxPro 2.6, the number of commands that can accept a LIKE or EXCEPT clause
	has been increased. This article explains the functionality of the LIKE and
	EXCEPT clauses, and lists some of the commands that do or do not accept the new
	LIKE/EXCEPT clauses.
	
	MORE INFORMATION
	================
	
	You can use the following commands to create a database so that you can test the
	examples listed below:
	
	     CREATE TABLE test ;
	     (afld  C(5), ;
	     bfld  C(5), ;
	     cfld  C(5), ;
	     dfld1 C(5), ;
	     dfld2 C(5), ;
	     xfyd  C(5))
	
	     INSERT INTO test ;
	     (afld,  ;
	     bfld,  ;
	     cfld,  ;
	     dfld1, ;
	     dfld2, ;
	     xfyd ) ;
	     VALUES ;
	     ('afld',  ;
	     'bfld',  ;
	     'cfld',  ;
	     'dfld1', ;
	     'dfld2', ;
	     'xfyd' )
	
	When you are using a LIKE or EXCEPT clause, you can specify a list of fields. For
	example, using the table created above, the following commands would set fields
	to "afld" and "bfld":
	
	     SET FIELDS TO ALL LIKE a*, b*
	     LIST
	
	The following commands, demonstrating the EXCEPT clause, would set fields to
	"bfld" and "cfld":
	
	     SET FIELDS TO ALL EXCEPT d*, a*
	     LIST
	
	You can also use LIKE and EXCEPT together. For example, the following commands
	would set fields to only "dfld1":
	
	     SET FIELDS TO ALL LIKE d* EXCEPT dfld2
	     LIST
	
	The above statement would include all fields beginning with "d" (dfld1 and
	dfld2), but would then exclude all fields named "dfld2", which leaves "dfld1".
	
	
	You cannot specify a traditional field list when using LIKE or EXCEPT. For
	example, the following commands would set fields to "afld" and "bfld" but not
	"xfyd":
	
	     SET FIELDS TO afld,bfld ALL LIKE x*
	
	Only one LIKE clause and/or EXCEPT clause can be specified. A second instance of
	these clauses will be ignored. For example, the following statement will set
	fields to "dfld1". The "LIKE x*" portion of the command is ignored.
	
	     SET FIELDS TO ALL LIKE d* EXCEPT dfld2* LIKE x*
	
	You can also specify all fields that contain the specified text. For example,
	this command would set fields to "xfyd":
	
	     SET FIELDS TO ALL LIKE *y*
	
	Of those commands that accept a field list, the commands that now accept LIKE and
	EXCEPT clauses include:
	
	  APPEND FROM ARRAY
	  BLANK
	  COPY STRUCTURE
	  COPY STRUCTURE EXTENDED
	  COPY TO
	  COPY TO ARRAY
	  DISPLAY
	  EXPORT
	  GATHER
	  REPLACE FROM ARRAY
	  SCATTER
	  SET FIELDS
	  SORT
	
	Of those commands that accept a field list, the commands that do not accept the
	LIKE/EXCEPT clauses include:
	
	  APPEND FROM
	  BROWSE
	  CHANGE
	  CREATE REPORT - Quick Report
	  CREATE SCREEN - Quick Screen
	  DISPLAY MEMO
	  EDIT
	  JOIN
	  LIST
	  SET CARRY
	  TOTAL
	
	
	Additional query words: VFoxWin FoxDos FoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro260DOS kbFoxPro260 kbVFP300
	Version           : MS-DOS:2.6; WINDOWS:2.6,3.0
	
	=============================================================================
	

{% endraw %}
