---
layout: page
title: "Q50349: PUBLIC Keyword Necessary in Most Multiple Modules Programs"
permalink: /kb/050/Q50349/
---

## Q50349: PUBLIC Keyword Necessary in Most Multiple Modules Programs

{% raw %}

	Article: Q50349
	Product(s): See article
	Version(s): 2.01
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | docerr | mspl13_masm
	Last Modified: 17-JUL-1990
	
	According to Page 173 of the "QuickAssembler Programmer's Guide," a
	function must be declared PUBLIC in the case of full segment
	definitions, but is not needed when using simplified segments. This is
	only partially correct. Simplified segment directives must be used
	with a language declaration to resolve external symbols to avoid the
	need for the PUBLIC keyword. If a high level language is not
	specified, the PUBLIC keyword must be included on every symbol that
	will be accessed from another module.

{% endraw %}
