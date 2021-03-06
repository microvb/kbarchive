---
layout: page
title: "Q133107: FIX: C1001 Error If More Than 127 Function Parameters"
permalink: /kb/133/Q133107/
---

## Q133107: FIX: C1001 Error If More Than 127 Function Parameters

{% raw %}

	Article: Q133107
	Product(s): Microsoft C Compiler
	Version(s): 2.0,2.1
	Operating System(s): 
	Keyword(s): kberrmsg kbCompiler
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 2.0, 2.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When compiling a file with a function definition that has more than 127
	parameters, the compiler generates this error message:
	
	  fatal error C1001: INTERNAL COMPILER ERROR
	  (compiler file 'd:\b_bld\c2.m2\P2\p2symtab.c', line 697)
	
	CAUSE
	=====
	
	Although the compiler message is unclear, which is a bug, the compiler limit for
	the number of parameters passed by a function is 127. This limit applies for any
	type of parameters and is by design.
	
	RESOLUTION
	==========
	
	Do not use more than 127 parameters for a function. One alternative is to use a
	structure to pass any number of variables as one parameter.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in the compiler that ships
	with Microsoft Visual C++, 32-bit Edition, version 4.0.
	
	MORE INFORMATION
	================
	
	Sample Code to Reproduce Problem
	--------------------------------
	
	  /* Compile options needed: any */ 
	
	  int ArgBug(int XX001, int XX002, int XX003, int XX004, int XX005,
	             int XX006, int XX007, int XX008, int XX009, int XX010,
	             int XX011, int XX012, int XX013, int XX014, int XX015,
	             int XX016, int XX017, int XX018, int XX019, int XX020,
	             int XX021, int XX022, int XX023, int XX024, int XX025,
	             int XX026, int XX027, int XX028, int XX029, int XX030,
	             int XX031, int XX032, int XX033, int XX034, int XX035,
	             int XX036, int XX037, int XX038, int XX039, int XX040,
	             int XX041, int XX042, int XX043, int XX044, int XX045,
	             int XX046, int XX047, int XX048, int XX049, int XX050,
	             int XX051, int XX052, int XX053, int XX054, int XX055,
	             int XX056, int XX057, int XX058, int XX059, int XX060,
	             int XX061, int XX062, int XX063, int XX064, int XX065,
	             int XX066, int XX067, int XX068, int XX069, int XX070,
	             int XX071, int XX072, int XX073, int XX074, int XX075,
	             int XX076, int XX077, int XX078, int XX079, int XX080,
	             int XX081, int XX082, int XX083, int XX084, int XX085,
	             int XX086, int XX087, int XX088, int XX089, int XX090,
	             int XX091, int XX092, int XX093, int XX094, int XX095,
	             int XX096, int XX097, int XX098, int XX099, int XX100,
	             int XX101, int XX102, int XX103, int XX104, int XX105,
	             int XX106, int XX107, int XX108, int XX109, int XX110,
	             int XX111, int XX112, int XX113, int XX114, int XX115,
	             int XX116, int XX117, int XX118, int XX119, int XX120,
	             int XX121, int XX122, int XX123, int XX124, int XX125,
	             int XX126, int XX127, int XX128)
	  {
	     return  0;
	  }
	
	Additional query words: 2.00 2.10 4.0
	
	======================================================================
	Keywords          : kberrmsg kbCompiler 
	Technology        : kbVCsearch kbAudDeveloper kbVC200 kbVC210
	Version           : :2.0,2.1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
