---
layout: page
title: "Q181696: XCLN: Configuring E-Mail Clients for Multiple Local Users"
permalink: /kb/181/Q181696/
---

## Q181696: XCLN: Configuring E-Mail Clients for Multiple Local Users

{% raw %}

	Article: Q181696
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:4.0,5.0; :8.0,8.01,8.02,8.03
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows NT client, versions 4.0, 5.0 
	- Microsoft Outlook 97, versions 8.0, 8.01, 8.02, 8.03, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to configure the Microsoft Exchange and Microsoft
	Outlook Windows NT clients so that more than one person can use the clients on
	the same computer.
	
	MORE INFORMATION
	================
	
	To configure the Microsoft Exchange or Microsoft Outlook Windows NT client so
	that more than one person can use the client on the same computer, follow these
	steps:
	
	1. In Control Panel, double-click Mail. If a Show Profiles button appears in the
	  dialog box that is displayed, click it. If a Show Profiles button does not
	  appear, proceed to step 2.
	
	2. Click Add.
	
	3. Click Manually Configure Information Services and then click Next.
	
	4. Type a name for the profile in the Profile Name box, and then click Next.
	
	5. Click Add, click Microsoft Exchange Server in the list of available
	  information services, and then click OK.
	
	6. Type the name of the Microsoft Exchange Server computer to which you want to
	  connect in the Microsoft Exchange Server box, type a mailbox name in the
	  Mailbox box, and then click Next. Note that you can click Check Name before
	  you click OK to verify the server and mailbox names.
	
	7. Click Add, click Personal Address Book in the list of available information
	  services, and then click OK.
	
	8. Type the full path and file name of the personal address book (PAB)
	  associated with the mailbox that you specified in step 6, and then click OK.
	  Note that you can click Browse to locate the PAB instead of typing the full
	  path and file name manually.
	
	9. Click Add, click Personal Folders in the list of available information
	  services, and then click OK.
	
	10. Type the full path and file name of the set of personal folders associated
	  with the mailbox that you specified in step 6, click Open, click OK, and
	  then click OK again. Note that you can also locate the set of personal
	  folders in the Create/Open Personal Folders File dialog box instead of
	  typing the full path and file name manually.
	
	  NOTE: To prevent people from reading other people's messages, each person
	  should use a different password-protected set of personal folders. If more
	  than one person uses the same set of personal folders, both people are able
	  to read the other person's messages. In addition, if you do not assign a
	  password to a set of personal folders, anyone who uses the client on that
	  computer may be able to access that set of personal folders.
	
	  If you specify an existing set of personal folders in the Create/Open
	  Personal Folders File dialog box, you can specify a new password by clicking
	  Change Password in the Personal Folders dialog box. If you do not know the
	  current password, contact your network or system administrator. For
	  additional information about lost or forgotten passwords for a set of
	  personal folders, please see the following article in the Microsoft
	  Knowledge Base:
	
	  Q189126 Microsoft's Policy Regarding Missing or Invalid Passwords
	
	  If you specify a new set of personal folders, you can specify a password on
	  the Create Microsoft Personal Folders dialog box.
	
	11. If you want to run Microsoft Exchange or Microsoft Outlook automatically
	  when you start Windows NT, click "Add Outlook to the Startup group", and
	  then click Next. If you do not want to run Microsoft Exchange or Microsoft
	  Outlook automatically, verify that "Do not add Outlook to the Startup group"
	  is selected, and then click Next.
	
	12. Click Finish.
	
	13. Repeat steps 2-12 for each additional person that you want to be able to use
	  the client.
	
	After you perform the above steps, the profile that appears in the "When starting
	Windows Messaging, use this profile" box is used when you start Microsoft
	Exchange or Microsoft Outlook. To cause Microsoft Exchange or Microsoft Outlook
	to prompt you for the profile to be used when it starts, follow these steps:
	
	1. In the client, click Options on the Tools menu.
	
	2. Click the "Prompt for a profile to be used" option in the When Starting
	  Microsoft Exchange area, and then click OK.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbExchangeSearch kbExchangeClientSearch kbZNotKeyword2 kbOutlook97Search kbZNotKeyword3
	Version           : WINDOWS:4.0,5.0; :8.0,8.01,8.02,8.03
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
