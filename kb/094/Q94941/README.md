---
layout: page
title: "Q94941: BUG: EXTERNDEF ABS Fails with Span Dependent Value"
permalink: /kb/094/Q94941/
---

## Q94941: BUG: EXTERNDEF ABS Fails with Span Dependent Value

{% raw %}

	Article: Q94941
	Product(s): Microsoft Macro Assembler
	Version(s): 6.0,6.0a,6.0b,6.1,6.11,6.1a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 6.0, 6.0a, 6.0b, 6.1, 6.1a, 6.11 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In an application developed with the Microsoft Macro Assembler (MASM), an
	attempt to export a constant value with the EXTERNDEF directive fails.
	
	CAUSE
	=====
	
	The exported value is defined in a macro as the difference between the values of
	two labels (a span-dependent value).
	
	RESOLUTION
	==========
	
	To work around this problem, perform one of the following two steps:
	
	- Modify the source code to specify the PUBLIC directive instead of the
	  EXTERNDEF directive
	
	- Modify the source code of the macro to place a label before the value
	  definition
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM versions 6.0, 6.0a, 6.0b,
	6.1, 6.1a, and 6.11. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	The following information is part of the README.TXT file distributed with MASM
	version 6.1.
	
	  Span-Dependent Equates in Macros and EXTERNDEF ABS
	  --------------------------------------------------
	
	  The ABS operator causes an identifier to be exported as a relocatable
	  unsized constant (see Programmer's Guide page 220). If ABS is used with
	  EXTERNDEF within a macro, and the constant being exported depends on the
	  difference between two addresses, the constant may not be exported
	  correctly. In some cases, the listing file will show the correct value,
	  but the value in the resulting .OBJ will be incorrect. For example, the
	  following code will not evaluate correctly:
	
	     EXTERNDEF TableSize:ABS  ; Will not be exported correctly
	
	     MAKETABLE MACRO
	     Table1 LABEL BYTE
	        DB 0, 1, 2
	     TableSize EQU $-Table1
	     ENDM
	
	     SEG1 SEGMENT
	     MAKETABLE
	     SEG1 ENDS
	
	  To avoid this problem, either use the 'PUBLIC' directive in place of
	  'EXTERNDEF', or put a label before the equate, within the macro.
	
	The code example below demonstrates this behavior. To see the problem,
	build both modules with CodeView information and link them together.
	Stepping through the program in the debugger to see the incorrect
	TableSize value.
	
	Sample Code Part 1
	------------------
	
	  ; Assemble options needed: /Zi
	  ; link part 1 and part 2 together with /CO link option
	
	  EXTERNDEF TableSize:ABS
	
	  _text SEGMENT para public 'CODE'
	  ASSUME cs:_text
	  start:
	     mov ax, TableSize
	     mov ax, 4C00h
	     int 21h
	  _text ENDS
	
	  END start
	
	Sample Code Part 2
	------------------
	
	  ; Assemble options needed: /Zi
	
	  EXTERNDEF TableSize:ABS ; Will not export correctly
	
	  MakeTable MACRO
	     Table1 LABEL BYTE
	        DB 0, 1
	     ;Table2 LABEL BYTE  ; Remove comment character to work around problem
	     TableSize EQU $-Table1
	  ENDM
	
	  _data SEGMENT para public 'DATA'
	     MakeTable
	  _data ENDS
	
	  END
	
	Additional query words: 6.00 6.00a 6.00b 6.10 6.10a buglist6.00a buglist6.00b buglist6.10 buglist6.10a buglist6.11
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM600 kbMASM610 kbMASM611 kbMASM610a kbMASM600a kbMASM600b
	Version           : :6.0,6.0a,6.0b,6.1,6.11,6.1a
	
	=============================================================================
	

{% endraw %}
