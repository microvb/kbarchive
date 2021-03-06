---
layout: page
title: "Q165290: WD97: Cannot Reference HeadingStyle Index with String Value"
permalink: /kb/165/Q165290/
---

## Q165290: WD97: Cannot Reference HeadingStyle Index with String Value

{% raw %}

	Article: Q165290
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbProgramming kbmacroexample word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you try to reference a heading style used to compile a table of figures or
	table of contents, the following error message appears:
	
	  Run-time error '13': Type mismatch
	
	CAUSE
	=====
	
	You will receive this error message if you attempt to reference the HeadingStyle
	object with a string value. For example, you will receive this message if you
	attempt to reference HeadingStyle by using the name of the style.
	
	WORKAROUND
	==========
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	To reference a heading style that has been added to compile a table of figures or
	table of contents, use either of the following methods:
	
	- Reference the style with an integer value.
	
	-or-
	
	- Create a macro that allows you to reference the style by name.
	
	  The following example Visual Basic for Applications macro demonstrates how you
	  can reference the style by name without receiving the error message:
	
	        Sub AddRemoveHeadingStyleExample()
	           Dim oTOCStyle As Object
	           ' Add a user defined style to the document.
	           ActiveDocument.Styles.Add Name:="UserDefined Para Style", _
	           Type:=wdStyleTypeParagraph
	           ' Insert a table of contents
	           ActiveDocument.TablesOfContents.Add ActiveDocument.Content
	           ' Add User Defined style to TOC HeadingStyles.
	           ActiveDocument.TablesOfContents(1).HeadingStyles.Add _
	           "UserDefined Para Style", 1
	           ' Loop through HeadingStyle collection.
	           For Each oTOCStyle In _
	              ActiveDocument.TablesOfContents(1).HeadingStyles
	              ' Perform conditional on style name to find.
	              If oTOCStyle.Style = "UserDefined Para Style" Then
	                 ' Remove the style from the TOC HeadingStyle collection.
	                 oTOCStyle.Delete
	              End If
	           Next
	  End Sub
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products
	
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: wordcon vb vba vbe
	
	======================================================================
	Keywords          : kbProgramming kbmacroexample word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
