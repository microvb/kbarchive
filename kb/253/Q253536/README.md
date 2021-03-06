---
layout: page
title: "Q253536: Modifying the HTML Search Results Page in MMS"
permalink: /kb/253/Q253536/
---

## Q253536: Modifying the HTML Search Results Page in MMS

{% raw %}

	Article: Q253536
	Product(s): Microsoft Windows NT
	Version(s): 2.1
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 09-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Metadirectory Services, version 2.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	You can modify all the HTML templates in the directory. This article describes
	how to modify the Search results field by adding a Location field to be returned
	to the Web browser.
	
	MORE INFORMATION
	================
	
	Using Compass, follow these steps:
	
	1. Search in the metadirectory for an object called "defaulthtmltemplate" and
	  then open its properties.
	
	2. Click the Web Search Response tab. This is the HTML template that is stored
	  in the directory. This template is used when a search is initiated. All the
	  search results are displayed using this template.
	
	3. Scroll down the template until you see:
	
	  +BeginList+
	  <tr>
	  <SPAN STYLE="text-decoration:none><FONT FACE ="Arial" size="1">
	  <td VALIGN="top" width="120" align="left"><A HREF="/Frames+myDn+"
	  target=_top>+myRdn1+</A></td> <td valign="top"><A
	  HREF="mailto:+mail+"> +mail+ </A><br>
	  +telephoneNumber+<br> +title+ </td></FONT>
	  </tr>
	  +EndList+
	
	This is the portion of the template that defines the output fields for the Web
	browser. When you perform a search you get the following fields back: MyRdn1
	(the person's name), Mail, Telephone, and Title.
	
	4. You can add or replace any of the attributes here by referring to the
	  attributes with the "+" modifier. To add the Location attribute to your
	  search results, specify the attribute with the modifier before and after the
	  attribute name (for example, +location+). The portion of the template listed
	  above would appear as follows:
	
	  +BeginList+
	  <tr>
	  <SPAN STYLE="text-decoration:none><FONT FACE ="Arial" size="1">
	  <td VALIGN="top" width="120" align="left"><A HREF="/Frames+myDn+"
	  target=_top>+myRdn1+</A></td> <td valign="top"><A
	  HREF="mailto:+mail+"> +mail+ </A><br>
	  +telephoneNumber+<br> +title+ +location+ </td></FONT>
	  </tr>
	  +EndList+
	
	5. After you make your change to the template, click OK to save your changes.
	
	Please refer to the MMS online documentation for more information about HTML
	modifiers.
	
	Additional query words: Zoomit Via MA zscript genlogs
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbMMSSearch kbMMS210
	Version           : :2.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
