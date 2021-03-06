---
layout: page
title: "Q317627: XWEB: Troubleshooting HTTP 401.x Errs in Outlook Web Access 5.5"
permalink: /kb/317/Q317627/
---

## Q317627: XWEB: Troubleshooting HTTP 401.x Errs in Outlook Web Access 5.5

{% raw %}

	Article: Q317627
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook Web Access, version 5.5 
	- Microsoft Outlook Web Access, version 5.5 Service Packs 1, 2, 3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes some of the various reasons that you may receive a "401
	Unauthorized" error message when you are using Microsoft Outlook Web Access
	(OWA). This article also provides some common methods that you can use to try to
	resolve such an error. This article contains the following sections:
	
	- Microsoft Windows NT Server 4.0
	
	   - 401.1 - Unauthorized: Logon Failed
	
	   - 401.3 - Unauthorized Due to ACL on Resource
	
	- Microsoft Windows 2000 Server
	
	   - 401.1 - Unauthorized: Logon Failed
	
	   - 401.3 - Unauthorized Due to ACL on Resource
	
	MORE INFORMATION
	================
	
	Microsoft Windows NT Server 4.0
	-------------------------------
	
	401.1 - Unauthorized: Logon Failed:
	
	This error may occur for the following reasons:
	
	- Local security policies. Every OWA user requires access to two local security
	  policies:
	
	   - The first local security policy is "Log On Locally." To make sure that
	     your users have this setting enabled:
	
	     1. Start User Manager for Domains.
	
	     2. On the Policies menu, click User Rights.
	
	     3. In the User Rights dialog box, click "Log on Locally".
	
	     4. In the Grant To box, add a domain group that your users belong to.
	        Typically, this group is the Domain Users group. Adding such a domain
	        group ensures that your users have access to log on locally.
	
	   - The second local security policy is "Access This Computer From the
	     Network." To make sure that your users have this setting enabled:
	
	     1. Start User Manager for Domains.
	
	     2. On the Policies menu, click User Rights.
	
	     3. In the User Rights dialog box, click "Access This Computer From the
	        Network".
	
	     4. In the Grant To box, add a domain group that your users belong to.
	        Typically, this group is the Domain Users group. Adding such a domain
	        group allows your OWA users access through this policy.
	
	- Basic authentication and the Windows NT domain name. OWA supports two
	  authentication methods. Those methods are "Basic" and "Windows NT Challenge
	  Response (NTLM)". If you use the Basic authentication method in OWA and you
	  do not supply a default domain name, you may receive this error message
	  because the domain is omitted in the credentials dialog box.
	
	  To determine whether or not you are experiencing this issue, after you type
	  your mailbox name in OWA, look at the credentials dialog box. If two boxes
	  are displayed ("User name" and Password), you are probably using Basic
	  authentication. If three boxes are displayed ("User name", Password, and
	  Domain), you are probably using NTLM authentication.
	
	  The exception to this rule is Microsoft Internet Explorer 6. If you use
	  Internet Explorer 6, only the "User name" and Password boxes are displayed in
	  the credentials dialog box, even if you are using NTLM authentication.
	
	  After you determine that you are using Basic authentication, try using the
	  following format for your logon information:
	
	   - "User name":
	
	  <Windows_NT_domain_name>\<user_name> (for example,
	  microsoft\user1)
	
	   - Password:
	
	  <user's_password>
	
	If you can use the preceding format to log on without receiving the 401.1 error
	message, to avoid this issue in the future, either:
	
	   - Instruct your users to log on by using that format.
	
	-or-
	
	   - Add a default domain in the Basic authentication section of Internet
	     Information Services (IIS) for OWA:
	
	     1. On the OWA server, start Internet Services Manager.
	
	     2. Expand the Web site in which OWA is installed, right-click the Exchange
	        virtual directory, and then click Properties.
	
	     3. Click the Directory Security tab, and then click Edit next to
	        "Anonymous access and Authentication Control".
	
	     4. Click Edit next to "Basic authentication".
	
	     5. Use one of the following steps, as appropriate:
	
	         - If all of your user accounts exist in one Windows NT domain, type
	           that domain name in the Default Domain box.
	
	-or-
	
	         - If your user accounts are spread among multiple domains, it is
	           easier to type "\" (without the quotation marks) in the Default
	           Domain box. If you type "\" (without the quotation marks) in the
	           Default Domain box, OWA searches all of the trusted domains for the
	           user name.
	
	After you add a default domain, the users can gain access to OWA by just
	supplying their user name and password, instead of typing
	<domain>\<user_name>.
	
	- File-level antivirus scanning software. A file-level antivirus scanning
	  utility that is actively scanning the Exchsrvr folder on the hard disk can
	  also cause this error. This issue can also manifest itself as a blank screen
	  in the Web browser, instead of as an error message.
	
	  At a minimum, exclude the Exchsrvr\Mdbdata, Exchsrvr\Webdata, and
	  Exchsrvr\Webtemp folders from file-level antivirus scans. If you do not
	  exclude these folders, issues may occur with both OWA and MAPI clients. Refer
	  to your antivirus software's documentation for instructions about how to
	  exclude files and folders.
	
	  If you are concerned about mail-related viruses in Microsoft Exchange Server,
	  obtain antivirus software which is "Exchange Server-aware". Exchange
	  Server-aware antivirus software uses scanning methods for the Exchange Server
	  store that are not damaging. Exchange Server-aware antivirus software uses
	  the antivirus application programming interface (API) that is built into
	  Exchange Server.
	
	401.3 - Unauthorized Due to ACL on Resource:
	
	This error is usually the result of not having the required NTFS security
	permissions on a file or registry key. To determine if this error is the result
	of not having the required NTFS security permissions:
	
	1. Confirm that the Everyone group has at least the minimum permissions that are
	  required on the folders in the following table. To view the permissions on a
	  folder, open the properties of the folder, and then click the Security tab.
	  If the Security tab is missing, the folder resides on a file allocation table
	  (FAT) partition. There are no specific file-level permissions on a FAT
	  partition. If the folder is on a FAT partition, skip to step 2 (registry
	  permissions).
	
	  +----------------------------------+
	  | Folder              | Permission | 
	  +----------------------------------+
	  | X:\Exchsrvr         | Read       | 
	  +----------------------------------+
	  | X:\Exchsrvr\Webdata | Change     | 
	  +----------------------------------+
	  | X:\Exchsrvr\Webtemp | Change     | 
	  +----------------------------------+
	  | X:\Exchsrvr\Bin     | Read       | 
	  +----------------------------------+
	  | X:\Exchsrvr\Res     | Read       | 
	  +----------------------------------+
	  | X:\Winnt            | Read       | 
	  +----------------------------------+
	  | X:\Winnt\System32   | Read       | 
	  +----------------------------------+
	
	2. Confirm that the Everyone group has at least the minimum permissions required
	  on the registry keys in the following table. To view security settings on
	  registry keys:
	
	  1. Click Start, and then click Run.
	
	  2. In the Run dialog box, type "regedt32.exe" (without the quotation marks).
	
	  3. Click the registry key that you want to view the security settings for,
	     and then click Permissions on the Security menu.
	
	  +---------------------------------------------------------------------------------+
	  | Registry key                                                       | Permission | 
	  +---------------------------------------------------------------------------------+
	  | HKEY_LOCAL_MACHINE\system\currentcontrolset\services\MSExchangeWeb | Read       | 
	  +---------------------------------------------------------------------------------+
	  | HKEY_LOCAL_MACHINE\system\currentcontrolset\services\W3svc         | Read       | 
	  +---------------------------------------------------------------------------------+
	
	Microsoft Windows 2000 Server
	-----------------------------
	
	401.1 - Unauthorized: Logon Failed:
	
	This error may occur for the following reasons:
	
	- Local security policies. Every OWA user requires access to two local security
	  policies:
	
	   - The first security policy is "Log On Locally." To make sure that your
	     users have this setting turned on:
	
	     1. Start the Local Security Policy snap-in.
	
	        NOTE: If OWA is installed on a Windows 2000-based computer that is a
	        domain controller, start the Domain Controller Security Policy snap-in.
	
	     2. Expand Local Policies, and then expand User Rights Assignment.
	
	     3. In the right pane, click "Log on Locally".
	
	     4. In the Assign To box, add a domain group that your users belong to.
	        Typically, this group is the Domain Users group. Adding such a domain
	        group ensures that your users have access to log on locally.
	
	   - The second Local Security Policy is "Access This Computer From the
	     Network." To make sure that your users have this setting turned on:
	
	     1. Start the Local Security Policy snap-in.
	
	        NOTE: If OWA is installed on a Windows 2000-based computer that is a
	        domain controller, start the Domain Controller Security Policy snap-in.
	
	     2. Expand Local Policies, and then expand User Rights Assignment.
	
	     3. In the right pane, click "Access This Computer From the Network".
	
	     4. In the Assign To box, add a domain group that your users belong to.
	        Typically, this group is the Domain Users group. Adding such a domain
	        group allows your OWA users access through this policy.
	
	- Basic authentication and the Windows NT domain name. OWA supports two
	  authentication methods. Those methods are "Basic" and "Windows NT Challenge
	  Response (NTLM)." If you use the Basic authentication method in OWA and you
	  do not supply a default domain name, you may receive this error message
	  because the domain name is omitted in the credentials dialog box.
	
	  To determine whether or not you are experiencing this issue, after you type
	  your mailbox name in OWA, view the credentials dialog box. If two boxes are
	  displayed ("User name" and Password), you are probably using Basic
	  authentication. If three boxes are displayed ("User name", Password, and
	  Domain), you are probably using NTLM authentication.
	
	  The exception to this rule is Internet Explorer 6. If you use Internet
	  Explorer 6, only the "User name" and Password boxes are displayed in the
	  credentials dialog box, even if you are using NTLM authentication.
	
	  After you determine that you are using Basic authentication, try using the
	  following format for your logon information:
	
	   - "User name":
	
	  <Windows_NT_domain_name>\<user_name> (for example,
	  microsoft\user1)
	
	   - Password:
	
	  <user's_password>
	
	  If you can use the preceding format to log on without receiving the 401.1
	  error message, to avoid this issue in the future, either:
	
	   - Instruct your users to log on by using that format.
	
	-or-
	
	   - Add a default domain in the basic authentication section of IIS for OWA:
	
	     1. On the OWA server, start Internet Services Manager.
	
	     2. Expand the Web site in which OWA is installed, right-click the Exchange
	        virtual directory, and then click Properties.
	
	     3. Click the Directory Security tab, and then click Edit next to
	        "Anonymous access and Authentication Control".
	
	     4. Click Edit next to Basic authentication.
	
	     5. Use one of the following steps, as appropriate:
	
	         - If all your user accounts exist in one Windows NT domain, type that
	           domain name in the Default Domain box.
	
	-or-
	
	         - If your user accounts are spread among multiple domains, it is
	           easier to type "\" (without the quotation marks) in the Default
	           Domain box. If you type "\" (without the quotation marks), OWA
	           searches all of the trusted domains for the user name.
	
	After you add a default domain, the users can gain access to OWA by just
	supplying their user name and password, instead of typing
	<domain>\<user_name>.
	
	- File-level antivirus scanning software. A file-level antivirus scanning
	  utility that is actively scanning the Exchsrvr folder on the hard disk can
	  also cause this error. This issue can also manifest itself as a blank screen
	  in the Web browser, instead of as an error message.
	
	  At a minimum, exclude the Exchsrvr\Mdbdata, Exchsrvr\Webdata, and
	  Exchsrvr\Webtemp folders from file-level antivirus scans. If you do not
	  exclude these folders, issues may occur with both OWA and MAPI clients. Refer
	  to your antivirus software's documentation for instructions about how to
	  exclude files and folders.
	
	  If you are concerned about mail-related viruses in Exchange Server, obtain
	  antivirus software that is "Exchange Server-aware." Exchange Server-aware
	  software uses scanning methods for the Exchange Server store that are not
	  damaging. Exchange Server-aware antivirus software uses the antivirus
	  application programming interface (API) that is built into Exchange Server.
	
	- OWA is installed on Windows 2000. Users who log on to OWA from a computer
	  that is running any Microsoft Windows operating system other than Windows
	  2000 can gain access to OWA, but users who log on to OWA from a computer that
	  is running Windows 2000 may receive a 401.1 error message.
	
	  This issue can occur if OWA is installed on a computer that is running Windows
	  2000 Server with Integrated Windows Authentication turned on as one of the
	  authentication methods on the Exchange Server virtual directory.
	
	  To resolve this issue, on the server that OWA is installed on, edit the
	  Constant.inc file in the Exchsrvr\Webdata\Usa folder:
	
	  1. Use Notepad to open the Constant.inc file.
	
	  2. Under '--Other Strings--', locate the following line:
	
	  bstrAuthTypesAccepted = "_BasicNTLMDPAMBS_BASIC"
	
	  3. Change the line to read:
	
	  bstrAuthTypesAccepted = "_BasicNTLMDPAMBS_BASICNegotiate"
	
	  4. On the File menu, click Save.
	
	  5. On the File menu, click Exit.
	
	  If you use a computer that is running either Microsoft Windows 2000 Server and
	  Internet Explorer 5 or Microsoft Windows 2000 Professional and Internet
	  Explorer 5 to try to log on to Internet Information Service (IIS) 5.0, and
	  Integrated Windows Authentication is enabled, a negotiation is performed to
	  determine if the Kerberos protocol or Windows NT Challenge/Response will be
	  used for authentication.
	
	  If you use a computer that is running either Windows 2000 Server and Internet
	  Explorer 5 or Windows 2000 Professional and Internet Explorer 5, the server
	  variable AUTH_TYPE is set to Negotiate. When you use a computer that is
	  running any other Windows operating system, the server variable is set to
	  NTLM. OWA checks what this variable returns against the bstrAuthTypesAccepted
	  value that is modified. This check ensures that the authentication type is
	  acceptable before OWA allows a user to log on.
	
	401.3 - Unauthorized Due to ACL on Resource:
	
	This error is usually the result of not having the required NTFS security
	permissions on a file or registry key. To determine if this error is the result
	of not having the required NTFS security permissions:
	
	1. Confirm that the Everyone group has at least the minimum permissions that are
	  required on the folders in the following table. To view the permissions on a
	  folder, open the properties of the folder, and then click the Security tab.
	  If the Security tab is missing, the folder resides on a FAT partition. There
	  are no specific file-level permissions on a FAT partition. If the folder is
	  on a FAT partition, skip to step 2 (registry permissions).
	
	  +----------------------------------+
	  | Folder              | Permission | 
	  +----------------------------------+
	  | X:\Exchsrvr         | Read       | 
	  +----------------------------------+
	  | X:\Exchsrvr\Webdata | Change     | 
	  +----------------------------------+
	  | X:\Exchsrvr\Webtemp | Change     | 
	  +----------------------------------+
	  | X:\Exchsrvr\Bin     | Read       | 
	  +----------------------------------+
	  | X:\Exchsrvr\Res     | Read       | 
	  +----------------------------------+
	  | X:\Winnt            | Read       | 
	  +----------------------------------+
	  | X:\Winnt\System32   | Read       | 
	  +----------------------------------+
	
	2. Confirm that the Everyone group has at least the minimum permissions that are
	  required on the registry keys in the following table. To view security
	  settings on registry keys:
	
	  1. Click Start, and then click Run.
	
	  2. In the Run dialog box, type "regedt32.exe" (without the quotation marks).
	
	  3. Click the registry key that you want to view the permissions for, and then
	     click Permissions on the Security menu.
	
	  +---------------------------------------------------------------------------------+
	  | Registry key                                                       | Permission | 
	  +---------------------------------------------------------------------------------+
	  | HKEY_LOCAL_MACHINE\system\currentcontrolset\services\MSExchangeWeb | Read       | 
	  +---------------------------------------------------------------------------------+
	  | HKEY_LOCAL_MACHINE\system\currentcontrolset\services\W3svc         | Read       | 
	  +---------------------------------------------------------------------------------+
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbOWASearch kbOWA550 kbOWA550SP1 kbOWA550SP2 kbOWA550SP3
	Version           : :5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
