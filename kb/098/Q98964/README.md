---
layout: page
title: "Q98964: Mac RSC: Common Problems and Solutions with Remote Server"
permalink: /kb/098/Q98964/
---

## Q98964: Mac RSC: Common Problems and Solutions with Remote Server

{% raw %}

	Article: Q98964
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you use Remote Server Connection (RSC) and version 3.1 of Microsoft Mail
	for AppleTalk Networks, the following errors may occur.
	
	NOTE: Possible workarounds are listed following each error.
	
	"Time Out Value Exceeded" Error in Session Log
	----------------------------------------------
	
	Possible cause: AppleTalk Remote Access (ARA) on the answering server has been
	configured to allow access to the entire network.
	
	Workaround: Open the Remote Access Setup Control Panel and change the setting to
	Allow Access To This Macintosh Only.
	
	"Can't Find Site <site name>" Error in Session Log
	--------------------------------------------------
	
	The following is an example of the Session Log when this error occurs:
	
	  Connected to zone ZONE A
	  Scanning for site A
	  Transferring data to site A
	  Can't find site A
	  Performing full zone scan
	  ...
	
	Possible cause: The ARA connection document has been named after the server you
	are calling. However, the document should correspond to the mail site.
	
	Workaround: Rename the connection document in System Folder:Preferences:MS Mail
	Remote Sites.
	
	When the entry "Transferring data to site A" appears in the log, it means that
	the Remote Server Connection has told the local server to begin transferring
	mail to the other site. If the local server cannot find the bridge server on the
	other site, it returns the "Can't find site A" error message to the Remote
	Server Connection.
	
	Additional possible cause: The AppleTalk network is poorly terminated.
	
	Workaround: Check both sides of the LocalTalk network for correct termination.
	
	Mail Servers Connect But No Mail or Data Is Transferred,
	
	Although the Status Window Reflects Data was Transferred
	--------------------------------------------------------
	
	Possible cause: You are using Microsoft Mail Server version 3.1.
	
	There are some problems with the original Mail 3.1 release where remote servers
	connect but do not exchange any data.
	
	Workaround: This problem is corrected in the version 3.1a release of the
	Microsoft Mail Server. To obtain the latest version of the mail server, contact
	Microsoft Sales at (800) 227-4679.
	
	Mail Server Dials Continuously
	------------------------------
	
	Possible cause: Urgent mail has been sent and you are using Microsoft Mail Server
	version 3.1.
	
	There are some problems with the original Mail 3.1 release where remote servers
	attempt to process urgent mail and dial continuously. The servers connect, but
	the message is not transmitted due to the problem explained above. Mail
	therefore continues to attempt to send the message.
	
	Workaround: This problem is corrected in the version 3.1a release of the
	Microsoft Mail Server. To obtain the latest version of the mail server, contact
	Microsoft Sales at (800) 227-4679.
	
	There Are No Connection Documents Listed in the
	
	Configuration Dialog Box of the Remote Server Connection (RSC)
	--------------------------------------------------------------
	
	Possible cause: The RSC program has not been quit from since the ARA document was
	saved to the MS Mail Remote sites folder.
	
	Workaround: Quit the RSC program, and then restart it.
	
	MORE INFORMATION
	================
	
	For more information about using the Remote Server Connection with AppleTalk
	Remote Access, please refer to the Application Note MM0741, "Configuring the
	Remote Server Connection." You can obtain this Application Note by contacting
	Microsoft Product Support Services.
	
	
	Additional query words: 3.10 appnote
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
