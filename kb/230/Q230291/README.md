---
layout: page
title: "Q230291: Index Server 2.0 Release Notes"
permalink: /kb/230/Q230291/
---

## Q230291: Index Server 2.0 Release Notes

{% raw %}

	Article: Q230291
	Product(s): Internet Information Server
	Version(s): winnt:2.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 31-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Index Server version 2.0 
	- Microsoft Windows NT version 4.0 Option Pack 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the Index Server 2.0 Release Notes included with
	the Windows NT 4.0 Option Pack. It is listed here so that the issues it covers
	are included in queries that are performed against the Knowledge Base.
	
	The file containing these Release Notes is located at
	<%SystemRoot%>\Help\Iis\Htm\Core\Ixreadme.htm.
	
	NOTE: Knowledge Base articles may be distributed in either ASCII-text or HTML
	form. If you are viewing the ASCII-text version of this article, some formatting
	may have been lost when it was converted from the original HTML form of
	Ixreadme.htm.
	
	MORE INFORMATION
	================
	
	Microsoft Index Server Release Notes
	Thank you for installing Microsoft(R) Index Server version 2.0 for Microsoft(R) Internet Information Server (IIS) version 4.0 running on Microsoft(R) Windows NT(R) Server. This topic supplements information contained in the online documentation.
	
	This page contains:
	
	Visit the Index Server Home Page 
	Changes to the Documentation 
	Your Guide to Technical Support 
	
	--------------------------------------------------------------------------------
	
	Visit the Index Server Home Page
	For more information about Index Server and related features, see the Index Server home page:
	
	http://www.microsoft.com/ntserver/search
	
	--------------------------------------------------------------------------------
	
	Changes to the Documentation
	This section updates the Index Server documentation for the following topics:
	
	Indexing a Newly Created Web Site 
	Running Webhits Out of the IIS Process 
	Indexing a Newly Created Web Site
	When you create a new Web site through Internet Information Server (IIS), the site is not indexed by default, and therefore you cannot search documents on that site with Index Server.
	
	To index a new Web site
	
	In left pane of Microsoft Management Console (MMC), right-click the newly created Web site. 
	Click Properties on the menu. 
	On the Home Directory property sheet, select Index this directory. 
	Click OK. 
	Next, you must add a catalog for the new site. To learn how to add a catalog, see Creating Catalogs in the main documentation.
	
	Running Webhits Out of the IIS Process
	The Index Server sample query forms configure the Webhits ISAPI application to run out of the IIS process, because ISAPI applications are generally configured to run out of process when they are untrusted. It's better to run untrusted applications out of process so that IIS is not affected if the application crashes. Webhits is configured in the Index Server samples to run out of process because it uses text filters (IFilter) to display query hits in files. Because text filters come from many companies, it's hard to guarantee they are all robust.
	
	The filters that ship with Index Server have been thoroughly tested. These include the HTML, Microsoft Office, and text filters. If you haven't installed any third party filters, it's safe (and more efficient) to run Webhits in the IIS process on your Web server.
	
	Internet Service Manager can configure virtual directories for running in or out of the IIS process. To configure Webhits to run in or out of process, edit the properties of the virtual directory in which the .htw files reside. Then, in the Directory property sheet, set the Run in separate memory space (isolated process) check box appropriately. By default, Index Server installs .htw file samples in the /IISsamples/ISsamples/Oop virtual directory.
	
	If you cannot run Webhits in the IIS process, limitations in IIS impose restrictions on Webhits. For example, files in virtual directories on computers other than the Web server cannot be displayed using Webhits when Webhits is running out of the IIS process. Also, files with extensions not associated with an IFilter cannot be displayed with Webhits when Webhits is running out of the IIS process and when the registry parameter WebhitsDisplayScript is not set to 2.
	
	You can work around these limitations, but the workaround compromises security for the Web server. Use this workaround only if security is not a significant concern for your installation. The workaround requires the administrator to do the following:
	
	Enable anonymous access to the directory through Internet Service Manager. 
	Configure an account that has administrative access as the default user for the directory. 
	To configure a user account
	
	Click Start, point to Windows NT 4.0 Option Pack, point to Microsoft Transaction Server, and click Transaction Server Explorer. 
	In MMC, double-click the Microsoft Transaction Server folder. 
	Open the Computers folder. 
	Open My Computer (or the folder representing your Web server). 
	Open Packages Installed. 
	Right-click the package representing Iissamples/Issamples/Oop and click Properties on the menu to open the property sheet. 
	On the Identity property sheet, type a user name and password in the User and Password boxes, and click OK. 
	This account must have administrative privileges on the local computer.
	
	--------------------------------------------------------------------------------
	
	Your Guide to Microsoft Technical Support
	If you have a technical question about Microsoft Index Server, use this online documentation or consult Help by clicking Help during a procedure. If you still have a question, Microsoft offers technical support and services ranging from self-help tools to direct assistance with a Microsoft Technical Support Engineer. Note: The services and prices listed here are available in the United States and Canada only (see Technical Support Worldwide below).
	
	Self-Help Tools to Find Answers Yourself
	Microsoft Technical Support Online: This innovative site uses the cutting-edge technology of Microsoft to help you access the most relevant technical information and resources to answer your support questions. Use the Troubleshooting Wizards to easily diagnose and answer technical questions. Or select technical articles, programming aids, or commonly asked questions from the Microsoft Knowledge Base of over 75,000 articles. Visit http://www.microsoft.com/support/ today and see how easy it is to find the answers you need.
	
	Direct Assistance with a Microsoft Technical Support Engineer
	Pay-Per-Incident Support: If you still need answers to your technical questions, you can purchase Pay-Per-Incident Support. In the U.S. and Canada, for a fee of $195US per incident, please call (800) 936-5900, 24 hours a day, seven days a week, including holidays.
	
	Note: Support fees for the (800)# calls will be billed to your VISA, MasterCard, or American Express credit card.
	
	Priority Annual Support: If you anticipate a high volume of support incidents, or need priority access to Microsoft Technical Support Engineers, you can purchase a Priority Annual Comprehensive Account. In the U.S. and Canada, for more information or to purchase an annual account at a cost of $1,695US per 10 incidents, call (800) 936-3500, 24 hours a day, 7 days a week, including holidays. To submit an incident against an existing account, call (800) 936-4900, 24 hours a day, 7 days a week, including holidays.
	
	Submitting questions via the Internet: In the U.S. and Canada, you can also submit your Pay-Per-Incident or Priority Annual support questions via the Internet with Microsoft Online Assisted Support. For more details, visit the following Microsoft Web site: http://support.microsoft.com/support/webresponse.asp 
	
	Priority Plus: Microsoft Technical Support also offers special accounts for medium-sized businesses that require priority incident resolution, including business-critical support and access to targeted information to assist information-technology and Help desk professionals in support planning for smoother product deployment. For more information, in the U.S. and Canada, please call (800) 936-3500, 24 hours a day, seven days a week, including holidays.
	
	Priority Consult Line: Receive hourly consulting for support questions that fall outside of the traditional technical support realm. These include designing or planning for deployment, software development, code review, and implementation planning. The Consult Line covers all Microsoft products, including those Microsoft products used for developing Internet and Intranet solutions. For more information or to purchase hourly consulting services at $195US per hour (minimum one hour), please call (800) 936-5200, Monday through Friday, excluding holidays, 6:00 A.M. to 6:00 P.M. Pacific time.
	
	Additional Support Options
	Professional Programs and Services: Microsoft Technical Support also offers professional support programs and services for large businesses that require a direct relationship with Microsoft. For more information, see the Technical Support section of the Help file, or visit Microsoft Technical Support Online at http://www.microsoft.com/support/.
	
	Text Telephone: Microsoft text telephone (TTY/TTD) services are available for the deaf or hard-of-hearing. In the United States, using a TTY/TTD modem, dial (425) 635-4948. In Canada, using a TTY/TTD modem, dial (905) 568-9641.
	
	Technical Support Worldwide: Support services and prices may vary outside the United States and Canada. For information on support available outside the U.S. and Canada, contact the local Microsoft subsidiary in your area. For a list of worldwide Microsoft subsidiaries, see the Technical Support section of the Help file, or visit Microsoft Technical Support Online at http://www.microsoft.com/support/.
	
	Note: The services and prices listed here are available in the United States and Canada only. Support services may vary outside the U.S. and Canada. For more information on support in other locations, contact your local Microsoft subsidiary.
	
	Microsoft's support services are subject to Microsoft's then-current prices, terms, and conditions, which are subject to change without notice. 
	
	--------------------------------------------------------------------------------
	
	Copyright Information
	(C) 1997 Microsoft Corporation
	
	These materials are provided "as-is," for informational purposes only.
	
	Neither Microsoft nor its suppliers makes any warranty, express or implied with respect to the content of these materials or the accuracy of any information contained herein, including, without limitation, the implied warranties of merchantability or fitness for a particular purpose. Because some states/jurisdictions do not allow exclusions of implied warranties, the above limitation may not apply to you.
	
	Neither Microsoft nor its suppliers shall have any liability for any damages whatsoever including consequential, incidental, direct, indirect, special, and lost profits. Because some states/jurisdictions do not allow exclusions of implied warranties, the above limitation may not apply to you. In any event, Microsoft?s and its suppliers? entire liability in any manner arising out of these materials, whether by tort, contract, or otherwise shall not exceed the suggested retail price of these materials.
	
	--------------------------------------------------------------------------------
	
	Additional query words: iis kbreadme readme ixreadme.htm ixreadme akz
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbIdxServSearch kbAudDeveloper kbIdxServ200 kbWinNT400OptionPack
	Version           : winnt:2.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
