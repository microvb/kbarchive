---
layout: page
title: "Q172221: How to Move One or More Zone Files to a New WinNT DNS Server"
permalink: /kb/172/Q172221/
---

## Q172221: How to Move One or More Zone Files to a New WinNT DNS Server

{% raw %}

	Article: Q172221
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 27-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses the steps involved when moving the zone files from one
	Windows NT 4.0 Domain Name Service (DNS) server to another Windows NT 4.0 DNS
	server.
	
	MORE INFORMATION
	================
	
	When you use the Microsoft DNS server, you have the option of starting the
	service using a boot file or using information that is stored in the registry.
	Use the appropriate section below:
	
	Starting DNS Using a Boot File
	------------------------------
	
	When you use a boot file to start your DNS server, follow these steps to move
	your zone file(s) from one Windows NT DNS server to another Windows NT DNS
	server:
	
	NOTE: The following steps assume that you have installed the Microsoft DNS server
	service on the new Windows NT-based server and have not configured any
	information for it.
	
	1. From Services in Control Panel, stop the Microsoft DNS server on both Windows
	  NT DNS servers.
	
	2. Manually copy the entire contents (subfolders included) of the
	  %Systemroot%\System32\DNS folder from the source server to the destination
	  server.
	
	3. Restart the Microsoft DNS server on the new Windows NT DNS server.
	
	Starting DNS Using the Registry
	-------------------------------
	
	When you are moving a single zone file, follow these steps:
	
	1. From Services in Control Panel, stop the Microsoft DNS server on both Windows
	  NT DNS servers.
	
	2. From the source DNS server, copy the desired zone file <zone name>.dns
	  from the following folder:
	
	     %Systemroot%\System32\DNS
	
	  to the same folder on the destination Windows NT DNS server.
	
	3. Create the new zone on the destination server using the DNS Service Manager.
	  Configure the zone as it was configured on the source server, either as a
	  Primary or Secondary zone. The new zone must be created using the same zone
	  file name as the original file.
	
	  For example, if Sample.com.dns was the original file copied from the source
	  server to the destination server, Sample.com.dns must be the name of the new
	  file.
	
	  NOTE: If the computer name is different on the new server, the SOA and NS
	  records in the reverse lookup zones may still have the old computer's name.
	  These records should be manually edited to reflect the computer name of the
	  new server.
	
	4. Restart the Microsoft DNS Server on the new Windows NT DNS server.
	
	When you are moving multiple zone files, follow these steps:
	
	WARNING: Using Registry Editor incorrectly can cause serious, system-wide
	problems that may require you to reinstall Windows NT to correct them. Microsoft
	cannot guarantee that any problems resulting from the use of Registry Editor can
	be solved. Use this tool at your own risk.
	
	Perform steps 1 and 2 on the destination Windows NT DNS server only:
	
	1. Using the DNS Manager create a sample primary zone, Sample.com. Creating the
	  sample zone ensures that the DNS server boot file information has been
	  written to the registry and the DNS server knows where the cache information
	  is located.
	
	2. Using DNS Manager, delete the sample zone that you created in step 1.
	
	3. From Services in Control Panel, stop the Microsoft DNS server on both Windows
	  NT DNS servers.
	
	4. From the source DNS server, copy the desired zone file <zone name>.dns
	  from the following folder:
	
	     %Systemroot%\System32\DNS
	
	  to the same folder on the destination Windows NT DNS.
	
	  Perform steps 5 through 8 on the source server only:
	
	5. Start Registry Editor (Regedt32.exe).
	
	6. Go to the following subkey:
	
	     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DNS
	
	7. Click Zones, click Registry, and click Save Key.
	
	8. Save this key to a location from where you can restore it to the destination
	  server and close Registry Editor.
	
	  Perform steps 9 through 14 on the destination server only:
	
	9. Start Registry Editor (Regedt32.exe).
	
	10. Go to the following subkey:
	
	      HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DNS
	
	11. Click Zones to verify that it is selected, click Registry, and click
	  Restore.
	
	12. Locate the registry key file that you exported in step 8.
	
	13. Click Yes to the confirmation dialog and close Registry Editor.
	
	14. Restart the Microsoft DNS Server on the new NT DNS server.
	
	NOTE: The information transferred in the registry key maintains the names of the
	zones and keeps you from re-creating the zone names in the DNS Manager for every
	zone file that was copied.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
