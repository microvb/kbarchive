---
layout: page
title: "Q43170: CV: K Command in Secondary Module Sets Breakpoints in Main"
permalink: /kb/043/Q43170/
---

## Q43170: CV: K Command in Secondary Module Sets Breakpoints in Main

{% raw %}

	Article: Q43170
	Product(s): See article
	Version(s): 2.20   | 2.20
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist2.20 | mspl13_basic
	Last Modified: 6-APR-1989
	
	In some cases the K (call stack) command will cause CodeView to become
	uncertain as to where to set breakpoints.
	
	If an attempt to set a breakpoint is made in a module of a
	multi-module program immediately after using the K command then the
	breakpoint will be set in the module containing main() instead of in
	the current module.
	
	If the corresponding line in the first module is not an executable
	line then CodeView will issue the expected beep to indicate that the
	breakpoint could not be set.
	
	If the corresponding line is an executable line then there will be no
	indication at all that the breakpoint has been set until that module
	is again in view. At that point the breakpoint will be highlighted as
	usual. This behavior will occur in any module accessed after the one
	containing main().
	
	Breakpoints will be set properly after using the K command if any
	stepping is performed, the view is changed, or the Calls menu is
	accessed.
	
	Microsoft is researching this problem and will post new information as
	it becomes available.

{% endraw %}
