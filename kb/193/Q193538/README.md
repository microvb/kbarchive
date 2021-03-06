---
layout: page
title: "Q193538: WD97: How to Remove Unused Standard Styles from a Document"
permalink: /kb/193/Q193538/
---

## Q193538: WD97: How to Remove Unused Standard Styles from a Document

{% raw %}

	Article: Q193538
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After you use a standard style in a document, Word for Windows adds it to the
	list of styles. You cannot remove the style name from this list, even if you are
	no longer using the style in the document. Although this feature is by design,
	you can use the methods described in this article to remove unused standard
	styles from the list of styles.
	
	Note: You can always delete unused styles that are not standard Word styles.
	
	WORKAROUND
	==========
	
	To remove unused standard styles from the style list in your Word document, use
	one of the following methods:
	
	Method 1: Copy Document Text to a New Document
	----------------------------------------------
	
	This method is useful if your document is small or if you only need to remove the
	styles from a portion of your document. This method does not work for selections
	of text that are larger than approximately 50 paragraphs. If your selection is
	larger than approximately 50 paragraphs, Word copies the entire list of styles,
	including unused standard styles. If you need to remove unused standard styles
	from a large document, use Method 2 instead.
	
	1. Create a new, blank document that lists only the four default standard
	  styles.
	
	2. Open the document that contains the unused styles you want to remove.
	
	3. If necessary, remove any standard style formatting you do not want to appear
	  on the style list in the new document.
	
	4. Select the entire document or the portion of the document you want to copy to
	  the new document. In any case, do not select more than approximately 50
	  paragraphs.
	
	5. From the Edit menu, choose Copy.
	
	6. Switch to the new document you created in step 1.
	
	7. From the Edit menu, click Paste.
	
	8. Open the Style list on the ribbon. No unused standard styles should appear on
	  this list.
	
	Note: If the entire list of styles appears in the new document, your selection is
	too large. Perform the above procedure again and select fewer paragraphs or use
	Method 2 instead.
	
	Method 2: Save the File in RTF and Then Delete Style References
	---------------------------------------------------------------
	
	You should use this workaround for large documents when Method 1 is cumbersome or
	does not work.
	
	1. Open the document that contains the unused styles you want to remove.
	
	2. From the File menu, click Save As.
	
	3. From the Save File As Type list, select Rich Text Format (*.rtf).
	
	4. Type a new name with a ".TXT" extension in the Name box and choose the OK
	  button.
	
	5. Make sure Confirm Conversion at Open is on.
	
	  a. On the Tools Menu, click Options and select the General Tab
	
	  b. Check Confirm conversion at Open
	
	  c. Click OK
	
	6. Open the RTF file you saved in steps 2 and 3 above. When the Convert File
	  dialog box appears, select Text Only in the Convert File From list [do not
	  choose Rich Text Format (RTF)]. Choose the OK button.
	
	7. In the document, Word for Windows formatting appears as RTF code. In this
	  code, style information appears in curly brackets after the "\stylesheet"
	  label. The following is a sample style definition in RTF format:
	
	    {\stylesheet{\s242\tqc\tx4320\tqr\tx8640 \fs20\lang1033
	    \sbasedon0\snext242 footer;}{\s243\tqc\tx4320\tqr\tx8640
	    \fs20\lang1033 \sbasedon0\snext243 header;}{\s251 \b\f2\fs20\lang1033
	    \sbasedon0\snext255 heading 4;}{\s252\li-360\sa120 \b\f2\fs20\lang1033
	    \sbasedon0\snext255 heading 3;}{\s253\li-360\sb120\sa120
	    \b\f2\lang1033 \sbasedon0\snext0 heading 2;}{\s254\li-360\sb240\sa120
	    \b\f2\fs28\lang1033 \sbasedon0\snext0 heading 1;}{\fs20\lang1033
	    \snext0 Normal;}}
	
	  To remove an unused style definition, delete the bracketed information for
	  that style. For example, to remove the Footer style from the above sample,
	  delete the following text:
	
	    {\s242\tqc\tx4320\tqr\tx8640 \fs20\lang1033 \sbasedon0\snext242
	    footer;}
	
	As another example, to remove the Heading 4 style from the above sample, delete
	the following text:
	
	    {\s251 \b\f2\fs20\lang1033 \sbasedon0\snext255 heading 4;}
	
	8. After you delete all unwanted style text, save and close the document.
	
	9. Open the RTF file you closed in step 7 above. When the Convert File dialog
	  box appears, select Rich Text Format (RTF) in the Convert File From list and
	  choose the OK button.
	
	10. Open the Style list on the ribbon. The unused styles you deleted in step 6
	  above should not appear in this list.
	
	11. To save the document back into Word for Windows format:
	
	  a. On the File Menu, click Save As
	
	  b. From the Save File As Type list, select Word Document (*.doc)
	
	  c. Click Save
	
	MORE INFORMATION
	================
	
	By default, Word always displays the following five standard styles:
	
	1. Normal
	
	2. Heading 1
	
	3. Heading 2
	
	4. Heading 3
	
	5. Default Paragraph Font
	
	After you apply a style in your document, Word adds it to the Style Name list in
	the Format Styles dialog box and to the Style box on the ribbon. Once you apply
	a standard style in your document, it remains on these lists, even if you later
	no longer use the style.
	
	Additional query words: removing
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
