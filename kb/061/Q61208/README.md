---
layout: page
title: "Q61208: C 6.00 README: Loading PWB Quickly"
permalink: /kb/061/Q61208/
---

## Q61208: C 6.00 README: Loading PWB Quickly

{% raw %}

	Article: Q61208
	Product(s): See article
	Version(s): 6.00   | 6.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 15-AUG-1990
	
	The following information is taken from the C Version 6.00 README.DOC
	file.
	
	Loading PWB Quickly
	-------------------
	
	Programmer's WorkBench (PWB) consists of the basic editor and four
	editor extensions that contain the functionality for building,
	linking, online help, and the Source Browser. These editor extensions
	are loaded automatically each time you invoke PWB.
	
	If you want PWB to load more quickly, you can rename some or all of
	the PWB extensions and then load them only when they are needed.
	
	For example, you can change the names of all the extension files from
	*.MXT (DOS) or *.PXT (OS2) to *.EXT. Then include the following section in
	your TOOLS.INI file:
	
	   [pwb-ext]
	   load:$PATH:pwbhelp.ext      ;Online Help
	   load:$PATH:pwbc.ext         ;C compiler
	   load:$PATH:pwbrowse.ext     ;Source Browser
	   load:$PATH:pwbutils.ext     ;LINK, NMAKE, and CodeView
	
	To load all the extensions at once, execute the following in PWB:
	
	   arg "ext" initialize
	
	With the default key assignments, this is
	
	   ALT+A "ext" SHIFT+F8
	
	To load a single extension -- the help extension, for example -- you
	can use the following:
	
	   arg "load:$PATH:pwbhelp.ext" assign
	
	With the default key assignment, this translates to
	
	   ALT+A "load:$PATH:pwbhelp.ext" ALT+=
	
	If you decide to rename the extensions and thus disable the extension
	autoload feature of PWB, you still have the option of starting up PWB
	with all the extensions loaded.
	
	To do this, define a macro in the PWB section of TOOLS.INI and assign
	it to a key of your choice. The following TOOLS.INI entry creates a
	macro called "extload" and assigns it to the F11 key:
	
	   extload:=arg "ext" initialize
	   extload:F11
	
	Then when you start PWB, you can use the /e option to execute
	"extload" on start up:
	
	   PWB /e extload

{% endraw %}
