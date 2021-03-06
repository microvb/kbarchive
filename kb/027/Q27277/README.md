---
layout: page
title: "Q27277: IF Statement Missing Colon Not Always Trapped at Compile Time"
permalink: /kb/027/Q27277/
---

## Q27277: IF Statement Missing Colon Not Always Trapped at Compile Time

{% raw %}

	Article: Q27277
	Product(s): See article
	Version(s): 3.00 4.00 4.00b
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | B_BasicCom buglist3.00 buglist4.00 buglist4.00b fixlist4.50 | mspl13_basic
	Last Modified: 17-JAN-1990
	
	The program below, which is missing a colon (:) before the GOTO
	statement in the IF statement, correctly gives the run-time error
	"Expected: end-of-statement" in the QuickBASIC Version 4.00 editor.
	
	However, when compiled from the DOS command line with BC.EXE and
	LINKed into an EXE program, the EXE program runs successfully without
	an error, printing "a=1" as if the missing colon were present.
	
	The same behavior occurs when compiling with QB.EXE Version 3.00 using
	the separate compilation method. (There is no BC.EXE in 3.00).
	
	To work around the problem, detect the missing colon by running and
	debugging the program in the editor before compiling to an EXE file.
	
	Microsoft has confirmed this to be a problem in QuickBASIC Versions
	3.00, 4.00, and 4.00b, and in Microsoft BASIC Compiler Versions 6.00
	and 6.00b (buglist6.00, buglist6.00b) for MS-DOS and OS/2. This
	problem was corrected in QuickBASIC Version 4.50 and in Microsoft
	BASIC Professional Development System Version 7.00 for MS-DOS
	(fixlist7.00).
	
	The following is the sample program:
	
	if a = 0 then a = 1 goto ending   ' A colon is missing before the GOTO.
	print "should not be seen"
	ending:
	print "a =";a
	system

{% endraw %}
