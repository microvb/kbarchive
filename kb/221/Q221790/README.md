---
layout: page
title: "Q221790: IIS Runs Out of Work Items and Causes RPC Failures"
permalink: /kb/221/Q221790/
---

## Q221790: IIS Runs Out of Work Items and Causes RPC Failures

{% raw %}

	Article: Q221790
	Product(s): Windows for Workgroups and Windows NT Networking Issues
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 31-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	In a Web farm environment, where one or more IIS Web servers are using a remote
	Windows NT or Windows 2000 file server to hold the content for the Web site (for
	example, the home directory or the virtual directories for the Web site are
	mapped to a UNC path), the IIS Web servers may run out of available work
	contexts at the redirector level. When this happens, the following symptoms can
	occur on your IIS Web servers:
	
	- IIS appears to stop responding. If you examine a process dump of
	  Inetinfo.exe, you will see that a large number of worker threads are waiting
	  to retrieve content from the remote file share. In a Performance Monitor log,
	  IIS appears largely idle during this time, as the majority of the threads are
	  in a wait state, waiting to access the remote server.
	
	- On the local desktop of one of the IIS Web servers, if you attempt to use the
	  client redirector to access the remote file share through Network
	  Neighborhood or My Network Places, or through Windows Explorer, it appears to
	  stop responding indefinitely. If a UNC path is mapped to a local drive letter
	  in Windows Explorer, and Windows Explorer is open, it appears to stop
	  responding as well. This can give the appearance that the entire operating
	  system has stopped responding, when in fact it has not.
	
	- The following error messages may occur when the maximum number of work
	  contexts are exhausted on a particular server:
	
	  RPC 1792 - The remote procedure call failed and did not execute.
	
	  Netlogon 5719 - Unable to find domain controller.
	
	  These error messages may occur when you attempt to make any additional RPC
	  connections to a server when the maximum number of work contexts is reached.
	
	
	CAUSE
	=====
	
	The server is running out of work contexts for a particular client. In Windows
	2000, there is a hard-coded upper limit of 125 work contexts for all types of
	clients (Windows NT, Windows 95, and Windows 98).
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	1. If you are running Windows 2000, install the post-SP1 hotfix described in the
	  following Microsoft Knowledge Base article to both the IIS servers and the
	  file server:
	
	  Q271148 MaxMpxCt and MaxCmds Limits in Windows 2000
	
	2. Increase the values of MaxCmds on the IIS Servers and MaxMpxCT on the File
	  Server by using the following registry scripts:
	
	   - Save the following registry script as Client.reg, and then run it on the
	     IIS servers:
	
	  Windows Registry Editor Version 5.00
	
	  [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\lanmanworkstation\parameters]
	  "MaxCmds"=dword:00000800
	
	   - Save the following registry script as Server.reg, and then run it on the
	     file server:
	
	  Windows Registry Editor Version 5.00
	
	  [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\lanmanserver\parameters]
	  "MaxMpxCT"=dword:00000800
	  "MaxWorkItems"=0x00002000
	
	  By default, these scripts specify a MaxCmds and MaxMpxCT of 2,048, which
	  should be sufficient for most situations. MaxWorkItems has been specified at
	  4x MaxMpxCt or 8,192. For more information on these settings, see the "More
	  Information" section of this article.
	
	3. Restart all of the IIS servers and the file server for these changes to take
	  effect.
	
	NOTE: Increasing these values consumes additional non-paged pool memory on the
	file server and the IIS clients. Non-paged pool memory has an upper limit of 256
	megabytes (MB). A large number of clients with a large number of connections can
	consume all of the non-paged pool memory on the file server. Use Performance
	Monitor to watch this counter and to make sure that it is not approaching the
	limit.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	After you apply the hotfix described in Q271148, the upper limit for MaxMpxCt
	(the server setting) changes from 125 to 65,535, and on the client, the upper
	limit for MaxCmds (the client setting) changes from 255 to 65,535.
	
	Additionally, the maximum number of concurrent SMB sessions that can be opened
	between the client and the server is the lower of MaxCmds and MaxMpxCT .
	However, if the connecting client is a Windows 95 or Windows 98 client, then the
	effective value of MaxMpxCt for that client is limited to 125.
	
	These limits become important when you use IIS in a Web-farm scenario where the
	content for the Web sites is stored on a remote UNC share, because IIS uses the
	ReadDirectoryChangesW API to receive file change notifications. This is done so
	that if files change, IIS can un-cache the old files, and then re-read the new
	files from the disk or share. When you use a UNC path as the home directory, a
	persistent SMB connection remains open between the IIS server and the file
	server, which consumes a work context. If the directory structure is large
	enough, it is possible to run out of work contexts and encounter the symptoms
	listed previously.
	
	A computer running IIS can have multiple virtual directories or Web sites
	pointing to shares on another Windows NT Server computer. The ASP Directory
	Monitor uses the ReadDirectoryChangesW API to monitor for any changes to those
	directories on the other server. Each pending ReadDirectoryChangesW requires a
	work context on the server, and there is only a limited number of work contexts
	available.
	
	The number of work contexts is passed from the server to the client when the SMB
	level is negotiated. The redirector on the client keeps an internal count of the
	number of work contexts that it is using on the server. The default number of
	work contexts is 50.
	
	The number of work contexts is limited to keep the server process from consuming
	all non-paged pool memory. This can be raised, but then there is a limit to how
	many work contexts a particular client can consume.
	
	This problem is not limited to IIS. Windows NT Explorer uses the same mechanism
	to monitor for directory changes.
	
	For additional information about the MaxWorkItems and MaxMpxCT settings, click
	the article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q232476 Terminal Server Connections and Logon Limited by MaxWorkItems
	
	  Q271148 MaxMpxCt and MaxCmds Limits in Windows 2000
	
	  Q216171 Server Performance Degrades During Work Item Allocation
	
	Additional query words: rdr
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500 kbiis400
	Version           : :4.0,5.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
