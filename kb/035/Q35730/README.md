---
layout: page
title: "Q35730: Incorrect Function Declaration"
permalink: /kb/035/Q35730/
---

## Q35730: Incorrect Function Declaration

{% raw %}

	Article: Q35730
	Product(s): See article
	Version(s): 5.00 5.10 | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | docerr h_fortran h_masm s_pascal | mspl13_c
	Last Modified: 23-SEP-1988
	
	On Page 66 of the "Microsoft Mixed-Language Programmer's Guide"
	provided with C Versions 5.00 and 5.10, FORTRAN Versions 4.0x and
	4.10, MASM Versions 5.00 and 5.10, and Pascal Version 4.00, the
	example program given in section 5.4.2 "Calling C from Pascal --
	Function Call" is incorrect. If the Pascal source code in the manual
	is compiled, the following errors will occur on the function
	declaration line:
	
	                   function Fact (n : integer)  [C]; extern;
	                                              ^ ^          ^
	 Warning 173  Insert:     ____________________| |          |
	    (the compiler is expecting a colon)         |          |
	                                                |          |
	 315  Type unknown or invalid assumed integer __|          |
	      Begin Skip                                           |
	                                                           |
	 187  End Skip    _________________________________________|
	
	The function declaration in the Pascal program is missing its return
	value. If the line is corrected to look as follows the program works
	properly:
	
	function Fact (n : integer) : integer  [C]; extern;

{% endraw %}
