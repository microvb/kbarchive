---
layout: page
title: "Q46382: _registerfonts, _setfont Return Values Incorrect in Manual"
permalink: /kb/046/Q46382/
---

## Q46382: _registerfonts, _setfont Return Values Incorrect in Manual

{% raw %}

	Article: Q46382
	Product(s): See article
	Version(s): 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | docerr | mspl13_c
	Last Modified: 30-AUG-1989
	
	The return values for _registerfonts() and _setfont() are incorrect on
	Page 325 of the "C for Yourself" manual that comes with Microsoft
	QuickC Version 2.00. These functions are described as returning void;
	however, the return values as specified in the "Microsoft QuickC
	Graphics Library Reference" manual are signed short integers.
	
	The following _registerfonts() function return values have the
	following meanings:
	
	   Return
	   Value    Meaning
	   ------   -------
	
	   > 0      If positive, the number of fonts registered
	    -1      No such file or directory
	    -2      One or more of the .FON files was not a valid,
	            binary .FON file
	    -3      One or more of the .FON files is damaged
	
	The _setfont() function returns the following:
	
	     0      If successful
	    -1      Font wasn't registered
	    -4      Not enough memory available for the font

{% endraw %}
