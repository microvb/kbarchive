---
layout: page
title: "Q171097: WD97: Macro to Calculate Number of Months between Two Dates"
permalink: /kb/171/Q171097/
---

## Q171097: WD97: Macro to Calculate Number of Months between Two Dates

{% raw %}

	Article: Q171097
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbmacro kbdta kbdtacode kbmacroexample word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article contains a sample Visual Basic for Applications macro that
	calculates the number of months between two dates. This macro is useful for
	determining the number of months that have passed since a particular starting
	date.
	
	MORE INFORMATION
	================
	
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
	
	The following sample Visual Basic for Applications macro calculates the number of
	months between 1/23/1993 and 11/2/1993:
	
	     Sub Date_MonthsBetweenDates()
	        Dim dBeginDate As Date
	        Dim dEndDate As Date
	        Dim intMonths As Integer
	        ' Beginning date.
	        dBeginDate = DateValue("1/1/1993")
	        ' Ending Date.
	        dEndDate = DateValue("2/1/1993")
	        ' Calculate number of months between dates.
	        intMonths = ((Year(dEndDate) - Year(dBeginDate)) * 12) + _
	           Month(dEndDate) - Month(dBeginDate)
	        ' Display number of months.
	        MsgBox Str$(intMonths) & " month(s)"
	     End Sub
	
	NOTE: The number of months returned by this macro is not based on the exact
	number of days between the two dates. For example, given a start date of
	10/31/1993 and an end date of 11/2/1993, the macro returns one month.
	
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
	Keywords          : kbmacro kbdta kbdtacode kbmacroexample word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
