---
layout: page
title: "Q148513: HOWTO: Use Pin and Label for Quality Assurance"
permalink: /kb/148/Q148513/
---

## Q148513: HOWTO: Use Pin and Label for Quality Assurance

{% raw %}

	Article: Q148513
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe400 kbSSafe500 kbSSafe600
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	It might be a good idea to freeze or pin a project to allow for a Code review
	while development continues on a SourceSafe controlled software project. This
	article shows by example how to do it.
	
	MORE INFORMATION
	================
	
	Back in the days when configuration management was done manually, there was a
	point in the development cycle where code was frozen for code review by a
	Quality Assurance team. This method of source control does not work in today's
	fast-paced development cycle. SourceSafe is project oriented and therefore has a
	different mechanism than other source control products for providing this
	important functionality.
	
	Step-by-Step Example
	--------------------
	
	Situation: An inprogress project Named myproject is ready for Quality Assurance
	code review. Follow these steps:
	
	1. Label myproject at the project level by highlighting the project in the
	  SourceSafe Explorer and clicking the label icon.
	
	2. Add a label, such as Submitted to QA.
	
	3. Using the history icon, choose to retrieve labels only.
	
	4. Select the proper label, and then click the share button.
	
	5. Move the selector to the proper level (often, just one level up in the
	  project tree), and name the new project "QA version." Select the recursive
	  check box, if applicable, and click OK.
	
	The newly created project will contain the project, pinned to the proper versions
	for all contained files. Pins can be removed or changed if desired.
	
	REFERENCES
	==========
	
	User's Guide "Microsoft Visual Sourcesafe", p. 64.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q139298 How to Include Specific File Revisions in a Project Label
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe400 kbSSafe500 kbSSafe600 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe400 kbSSafe500
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
