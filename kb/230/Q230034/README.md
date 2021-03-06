---
layout: page
title: "Q230034: WD97: Bullet Replaces Leading Number in Paragraph"
permalink: /kb/230/Q230034/
---

## Q230034: WD97: Bullet Replaces Leading Number in Paragraph

{% raw %}

	Article: Q230034
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you create a list or paragraphs containing bullets, Word replaces any
	leading numbers or a single letter followed by a period (an initial, for
	example) with the bullet character.
	
	CAUSE
	=====
	
	Word does not allow both a number and a bullet to appear at the beginning of a
	paragraph or list item when you use the Bullets and Numbering command.
	
	WORKAROUND
	==========
	
	To prevent Word from removing leading numbers from paragraphs or lists that you
	want to format with bullets, use any of the following methods.
	
	Method 1: Insert an Optional Hyphen
	
	1. Press CTRL+HYPHEN.
	
	2. Type the number, followed by the text you want.
	
	3. Select the numbered text, and then on the Tools menu, click Bullets and
	  Numbering.
	
	4. On the Bullet tab, click to select the bullet you want, and then click OK.
	
	5. On the Edit menu, click Replace.
	
	6. In the Find what box, press CTRL+HYPHEN, leave the Replace with box blank,
	  and then click Replace All.
	
	Method 2: Place the Number in a QUOTE Field
	
	1. Press CTRL+F9 to insert field braces.
	
	2. Type "quote" and press the SPACEBAR.
	
	3. Type the number you want between the quotation marks. For example, the field
	  code should appear as follows:
	
	  {quote "12.2"}
	
	4. Press F9 to update the display results.
	
	Method 3: Use a Macro
	
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
	
	The following Visual Basic for Applications macro can replace the
	ToolsBulletListDefault macro, which is assigned to the Bulleted List toolbar
	button. The macro automates the typing of unique characters in front of the
	numbers before adding bullets.
	
	  Sub formatbulletdefault()
	      With Selection
	      If Selection.Range.ListFormat.ListType = wdListNoNumbering Then
	      Selection.HomeKey Unit:=wdLine
	      Selection.TypeText Text:=Chr(31)
	      With ListGalleries(wdBulletGallery).ListTemplates(1).ListLevels(1) _
	          .NumberStyle = wdListNumberStyleBullet
	          With .Font
	              .Name = "Symbol"
	          End With
	      End With
	      ListGalleries(wdBulletGallery).ListTemplates(1).Name = ""
	      Selection.Range.ListFormat.ApplyListTemplate _ 
	           ListTemplate:=ListGalleries(wdBulletGallery).ListTemplates(1), _ 
	           ContinuePreviousList:=False, ApplyTo:=wdListApplyToWholeList
	      Selection.TypeBackspace
	      Else
	      Selection.Range.ListFormat.RemoveNumbers NumberType:=wdNumberParagraph
	      End If
	      End With
	  End Sub
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
