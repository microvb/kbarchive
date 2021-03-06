---
layout: page
title: "Q39374: FIX: MASM 5.1 Generates Incorrect Listing for RET Statement"
permalink: /kb/039/Q39374/
---

## Q39374: FIX: MASM 5.1 Generates Incorrect Listing for RET Statement

{% raw %}

	Article: Q39374
	Product(s): Microsoft Macro Assembler
	Version(s): 5.1,5.1a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Macro Assembler (MASM), versions 5.1, 5.1a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the /LA option is used to show the instructions generated for the RET
	instruction, where the RET statment has a label on the same line and is
	contained in a PROC that has a USES clause, and/or parameters, the listing shows
	the original source line, including the label, after the POP instructions which
	are inserted by MASM. Running the program under CodeView, checking the object
	code generated for jumps, and checking the value of the label on the RET in the
	symbol listing at the end of the program all confirm that MASM is producing
	correct code. It is just the listing that is incorrect.
	
	RESOLUTION
	==========
	
	To produce a correct listing, change the code so that the label and the RET are
	not on the same line of source. In other words, change
	
	  JUMPHERE:   RET
	
	to the following:
	
	  " JUMPHERE: RET " (without the quotation marks)
	
	and the statement will appear in the correct location in the listing file.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in MASM version 5.10. This problem
	was corrected in MASM version 6.00.
	
	MORE INFORMATION
	================
	
	The sample code below illustrates the problem. Note: The the first three lines
	are necessary for using the "USES" directive.
	
	Sample Code:
	------------
	
	  ; Assemble options needed: none
	
	          dosseg
	          .model small,c
	          .code
	  myproc  proc uses si di bp
	          jz there
	  there:  ret
	  myproc     endp
	          end
	  ........................................................................
	
	  ; Incorrect listing file
	
	         1                                        dosseg
	         2                                        .model small,c
	         3                                assume cs:@code,ds:@data,ss:@data
	         4                                        .code
	         5 0000                           _TEXT segment 'CODE'
	         6 0000                           myproc  proc uses si di bp
	         7 0000  56                       push SI
	         8 0001  57                       push DI
	         9 0002  55                       push BP
	        10 0003  74 00                            jz there
	        11 0005  5D                       pop BP
	        12 0006  5F                       pop DI
	        13 0007  5E                       pop SI
	        14 0008  C3                       there:  ret
	        15 0009                           myproc  endp
	        16                                        end
	        17 0009                           @CurSeg ends
	
	Additional query words: 5.10 5.10a buglist5.10 buglist5.10a fixlist6.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMASMsearch kbAudDeveloper kbMASM510 kbMASM510a
	Version           : :5.1,5.1a
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
