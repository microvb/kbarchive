---
layout: page
title: "Q192552: HOWTO: Create an HTML Form With DHTML Page Designer"
permalink: /kb/192/Q192552/
---

## Q192552: HOWTO: Create an HTML Form With DHTML Page Designer

{% raw %}

	Article: Q192552
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 25-JUN-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to use the DHTML Page Designer to create a simple
	HTML form application. Currently, the DHTML Page Designer will not insert all
	the tags required to do this so you need to manually insert the missing tags.
	
	MORE INFORMATION
	================
	
	You can build a simple HTML form using the DHTML Page Designer. The form will
	have two fields and a submit button. The information will be posted to an ASP
	file on the server. The server will simply display the values entered in the
	fields. Follow these steps:
	
	1. Start Visual Basic 6.0 and create a new DHTML Application project.
	
	2. Open the DHTMLPage1 from Designers.
	
	3. From the toolbox, drag a textbox and change its NAME to Field1.
	
	4. Drag another textbox and change its NAME to Field2.
	
	5. Drag a submit button and change its VALUE to Submit.
	
	6. Save the project.
	
	7. You now need to save the HTM as an External HTML file. To do this:
	
	  a. Bring up the DHTML Page Designer Properties.
	
	  b. Select "Save the HTML as an External file" check box.
	
	  c. Click the "New" button.
	
	  d. Specify the location and name of the file you want.
	
	8. Click the Launch Editor button on the Designer tool bar. You will see HTML
	  similar to the following in your editor:
	
	        <BODY>
	        <INPUT id=TextField1 name=TextField1>
	        <P>
	        <INPUT id=TextField2 name=TextField2>
	        <P>
	        <INPUT id=SubmitButton1 name=Submit1 type=submit value=Submit></P>
	        </BODY></HTML>
	
	  Notice that there are some tags missing. First the HTML tag is missing.
	  Secondly, there is no FORM tag. Edit the file manually to enter these tags so
	  that the final HTM looks like the following:
	
	        <HTML>
	        <BODY>
	        <P<
	        <FORM ID=Form1 NAME=Form1 METHOD=POST
	              ACTION="http://MyServer/MyDir/Test1.ASP">
	        <INPUT id=TextField1 name=TextField1>
	        <P>
	        <INPUT id=TextField2 name=TextField2>
	        <P>
	        <INPUT id=SubmitButton1 name=Submit1 type=submit value=Submit></P>
	        </FORM>
	        </BODY>
	        </HTML>
	
	9. Save the file from the HTML editor and, when prompted by the designer, say
	  Yes to reloading the file into the designer
	
	10. At this point, you can add some validation code. This can be done by writing
	  the onSubmit event handler for the form as follows:
	
	        Private Function Form1_onsubmit() As Boolean
	
	            Dim Valid As Boolean
	
	            Valid = True
	            If TextField1.Value = "" Then
	                BaseWindow.alert "You must enter a value for Field1"
	                Valid = False
	            End If
	            If TextField2.Value = "" Then
	                BaseWindow.alert "You must enter a value for Field2"
	                Valid = False
	            End If
	
	            Form1_onsubmit = Valid
	
	        End Function
	
	11. Save the Visual Basic 6.0 project.
	
	12. Now create the Test1.asp file you used in the ACTION attribute in your FORM
	  tag. This file must be stored on your IIS web server. If you are not using
	  IIS, you will not be able to use ASP. Use NotePad to save the following as
	  test1.asp on your server:
	
	        <%@ LANGUAGE="VBSCRIPT" %>
	
	        You entered the following values from your DHTML Page Designer
	        form:<p>
	        TextField1 = <%=Request.Form("TextField1") %><br>
	        TextField2 = <%=Request.Form("TextField2") %><br>
	
	13. Run the project. You should see the values you enter into Field1 and Field2
	  returned to you by the server.
	
	Additional query words: kbdsi kbDSupport kbVBp kbVBp600 kbDHTML kbInternet kbPageDesigner
	
	======================================================================
	Keywords          :  
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
