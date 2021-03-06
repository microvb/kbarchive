---
layout: page
title: "Q118328: Multimedia Viewer Title Limits"
permalink: /kb/118/Q118328/
---

## Q118328: Multimedia Viewer Title Limits

{% raw %}

	Article: Q118328
	Product(s): Miscellaneous Software Development Kits
	Version(s): 2.0,2.0a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Multimedia Viewer Publishing Toolkit, versions 2.0, 2.0a 
	-------------------------------------------------------------------------------
	
	The table below is a collection of the limits for titles developed using
	the Microsoft Multimedia Viewer Publishing Toolkit. Each of the limits
	below mentions where the information was found in the Viewer documentation.
	
	  AG = Microsoft Multimedia Viewer 2.0 Authoring Guide
	  TR = Microsoft Multimedia Viewer 2.0 Technical Reference
	
	Element                               Limit                    Source
	----------------------------------------------------------------------
	context string                        255 characters           AG
	                                     128 is incorrect         TR 1-27
	
	title                                 128                      TR 1-28
	                                     50 for Sony              AG
	                                     127 characters incorrect AG
	
	footnote text                         1,023                    TR 2-25
	
	build tag                             32 characters            AG 3-9
	
	topic paragraph                       32K (8K for Sony)
	
	commands                              512 chars
	
	group entry or exit command script    512 chars                AG, TR 4-13
	
	topic entry command script            512 chars                AG 4-17
	
	keyword index title                   50 chars                 AG 7-4
	(defined in [KEYINDEX] in .MVP)                                TR 4-15
	
	keyword footnote text                 1,023 chars              AG 7-6
	
	keywords                              255                      AG 7-6
	                                                              TR 1-30
	
	characters in a vfld                  127                      AG 8-12
	
	alias text                            16,383                   AG 8-17
	                                                              TR 4-31
	
	characters to alias (i.e. characters  255 chars                AG 8-18
	to highlight when alias text matched                           TR 2-2
	in search)                                                     TR 4-31
	
	largest alias number                  4,294,967,295            TR 4-31
	
	max length of embedded pane statement 1023                     TR 1-35
	(including braces)                                             TR 2-17
	
	Topic-entry commands for a topic      512 characters           README.TXT
	(combined limit) The Authoring Guide
	incorrectly states that the limit is
	512 characters per footnote.
	
	topic group names                     127 chars                TR 4-12
	
	topic group titles                    127 chars (only about 40 TR 4-12
	                                     chars will display in
	                                     Search dialog box)
	
	title for edit box title for vfld     50 chars                 TR 4-22
	in Search dialog box
	
	Word wheel subfile name               24                       TR 4-22
	                                                              TR 4-29
	
	Window caption length                 50 chars                 TR 4-24
	
	ROOT option                           1,024 chars              TR 4-41
	
	Viewer Title                          50 chars                 TR 4-41
	
	nonscrolling regions, scrolling       256                      TR 1-31
	regions, panes and popups (per topic)                          TR 2-29
	                                                              TR 4-17,23
	
	topics per RTF source file            32,767
	
	build tags                            32                       AG 3-9
	                                                              TR 4-6
	
	total groups (including browse        200 (10 topic groups for AG 8-15, 21
	sequences) and word wheels            Sony)                    AG 8-26
	                                                              TR 1-28
	                                                              TR 4-11, 22
	                                                              TR 4-28, 29
	
	data types                            16 (numbered 0-15,       AG 8-6
	                                     including defaults)      TR 4-9
	                                     range -32,767 to 32,768  TR 2-16
	
	alias file entries                    4 billion                AG 8-17
	
	stop words per stop word file         1,024                    AG 8-23
	                                                              TR 4-10
	
	files in baggage                      10,000 (actually can     AG 2-13
	                                     have 16,000 files, but   TR 4-5
	                                     performance degrades)
	
	Citation                              2,000 chars              AG 2-18
	                                                              TR 4-34
	
	Copyright                             50 chars                 TR 4-36
	
	Total group entry and exit scripts    32,768 chars             TR 4-13
	for title
	
	Titles with topic groups cannot have more than 512,000 topics indexed for
	the search index. (TR 1-29, TR 4-11)
	
	The maximum number of windows, panes, and popups that Project Editor allows
	you to define is approximately 153 total (windows, panes, and popups
	combined). However, the actual Viewer limit is 255 for each type: 255
	windows, 255 panes, and 255 popups. If you wish to define more windows,
	panes, and popups than Project Editor will allow, edit the .MVP file
	without using Project Editor. (README.TXT)
	
	The largest legal value for the NEAR operator in the [SEARCHDLG] section of
	the project file is 32,768. (README.TXT)
	
	Section names specified in an MCI [sections] option or section file should
	have no more than 40 characters to ensure the section name fits when the
	title is viewed on a low-resolution display. (README.TXT)
	
	Additional query words: 2.00 capacity
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbHomeMMsearch kbMMViewer200 kbMMViewer200a
	Version           : :2.0,2.0a
	
	=============================================================================
	

{% endraw %}
