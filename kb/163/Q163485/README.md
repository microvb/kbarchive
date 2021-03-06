---
layout: page
title: "Q163485: Active Server Pages Script Appears in Browser"
permalink: /kb/163/Q163485/
---

## Q163485: Active Server Pages Script Appears in Browser

{% raw %}

	Article: Q163485
	Product(s): Internet Information Server
	Version(s): winnt:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use Microsoft Internet Information Server (IIS), if you place a period
	(.) in a browser's command line after any script-mapped file name, you receive
	unexpected results. The browser produces a document that contains the scripting
	information and other data in the file.
	
	For example, if you enter:
	
	  http://server_name/asp_directory/file.asp.
	
	you will receive something similar to the following:
	
	  <% emailx=request.form("email")
	     remarkx=request.form("remark") Set Conn =
	     Server.CreateObject("ADODB.Connection") Conn.Open "Local SQL
	     Server", "sa", "DTide" Set RS = Conn.Execute("insert into
	     Web_data.dbo.ASP_data(email,remark) values('" & emailx &
	     "','" & remarkx & "')") %>
	
	     Your information has been added to our database.
	
	The browser should return a confirmation Web page without the script.
	
	CAUSE
	=====
	
	The problem affects any script-mapped files requested from a virtual directory
	that has both read and execute permissions set. Adding one or more extra periods
	onto the end of the URL causes the file to be displayed in the browser, instead
	of run on the server. This allows end users to see information that may be
	confidential, such as server-side script logic (for example, the discount
	applied to the retail price from a database). This problem affects any file in
	the script-map list, such as .asp, .ht., .id, .PL, and so on.
	
	This problem only occurs on virtual directories that have both read and execute
	access. If read is disabled, the server-side information is not viewable by the
	end user.
	
	
	RESOLUTION
	==========
	
	A supported fix that corrects this problem is now available from Microsoft, but
	it has not been fully regression tested and should be applied only to computers
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	
	This hotfix has been posted to the following Internet location. You can download
	any of these self-extracting files from the following service:
	
	  Internet (anonymous FTP)
	  ftp ftp.microsoft.com
	  Change to the bussys/winnt/winnt-public/fixes/usa/ 
	  nt40/hotfixes-postSP2/iis-fix/ folder.
	  Get Readme.1st (for instructions on downloading and installing the
	  hotfix).
	
	Or use the following full URL on your client browser:
	
	  FTP://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/ 
	  nt40/hotfixes-postSP2/iis-fix/readme.1st
	
	NOTE:After you apply the above fix, the default document in WWW Service
	Properties cannot contain any forward slashes. Any forward slashes must be
	converted to back slashes.
	
	WORKAROUND
	==========
	
	To work around this problem, do not place script-mapped files in a directory
	that has both read and execute permissions.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Internet Information
	Server version 3.0.
	
	
	Additional query words: 1.00 2.00 3.00 prodnt 4.00 hang version
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis300
	Version           : winnt:3.0
	
	=============================================================================
	

{% endraw %}
