---
layout: page
title: "Q130079: Err Msg: Dial-Up Networking Could Not Negotiate Compatible..."
permalink: /kb/130/Q130079/
---

## Q130079: Err Msg: Dial-Up Networking Could Not Negotiate Compatible...

{% raw %}

	Article: Q130079
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): kberrmsg dun msnets win95 kbDialUp
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 98 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Dial-Up Networking client included with Windows 95/98 to
	connect to a Windows 95/98 or Windows NT remote access server, you may receive
	the following error message:
	
	  Dial-Up Networking could not negotiate a compatible set of network protocols
	  you specified in the Server Type settings. Check your network configuration
	  in the Control Panel then try the connection again.
	
	CAUSE
	=====
	
	This error message can be caused by any of the following situations:
	
	- The network protocols used by the server do not match the protocols used by
	  the Dial-Up Networking client.
	
	- The protocol used by the Dial-Up Networking client is not available.
	
	- The line protocols may not match.
	
	- You may be using a PAP or CHAP login and a clear-text terminal login is
	  needed. PAP and CHAP authentication uses the user name and password you type
	  in the Connect To dialog box when you dial. A terminal login occurs after
	  modem negotiation.
	
	- Your computer name is duplicated on the network.
	
	- The connection you are using is damaged.
	
	- Your port settings are incorrect.
	
	- Your modem is physically damaged.
	
	- Dial-Up Networking is missing driver files.
	
	RESOLUTION
	==========
	
	To work around this problem, use the appropriate method:
	
	Method 1
	--------
	
	If the protocols used by the server and the Dial-Up Networking client do not
	match, modify the protocols used by the client so that at least one protocol
	matches.
	
	Method 2
	--------
	
	If a protocol used by the Dial-Up Networking client is not available, install the
	protocol from Control Panel and bind it to the Dial-Up Networking adapter.
	
	Method 3
	--------
	
	Make sure you have the correct server type selected in the connection's
	properties (PPP, SLIP, or RAS).
	
	Method 4
	--------
	
	Perform the following steps to enable a terminal login:
	
	1. Click the Start button, point to Programs, point to Accessories, and then
	  click Dial-Up Networking.
	
	2. Use the right mouse button to click the connection, and then click Properties
	  on the menu that appears.
	
	3. On the General tab, click Configure.
	
	4. On the Options tab, click "Bring up terminal window after dialing."
	
	5. Click OK until all dialog boxes are closed.
	
	When you connect, enter your user name and password as prompted by your
	provider.
	
	Method 5
	--------
	
	If a network adapter is installed, try removing the binding for TCP/IP from the
	network adapter. Try this method only after trying all the other methods listed
	in this article. If this works, and you have other protocols installed, you can
	leave TCP/IP unbound from the network adapter. If this is the only protocol you
	have installed, you must bind the TCP/IP protocol to the network adapter before
	you can use the network.
	
	Method 6
	--------
	
	Make sure there are no duplicate computer names on the network.
	
	Method 7
	--------
	
	Delete the damaged connection and then re-create it.
	
	Method 8
	--------
	
	Verify your port settings are correct. To do so, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Modems.
	
	3. Click the modem you are using for this connection, click Properties, and then
	  click the Connection tab.
	
	4. Verify that the settings under Connection Preferences are correct, click OK,
	  and then click Close.
	
	Method 9
	--------
	
	Verify that your modem is not damaged by testing a known good modem in your
	computer.
	
	Method 10
	---------
	
	1. Rename the *.386 files located in the Windows\System folder.
	
	2. Reinstall Windows on top of your existing installation with the /P F switch.
	
	  For more information about Windows 98 Setup switches see the following article
	  in the Microsoft Knowledge Base:
	
	  Q186111 Description of the Windows 95, Windows 98, and Windows Me Setup
	  Switches
	
	MORE INFORMATION
	================
	
	Dial-Up Networking can bind up to three protocols. The NetBEUI, IPX/SPX, and
	TCP/IP protocols are used by default for a Dial-Up Networking connection.
	However, the fact that these protocols are used by a Dial-Up Networking
	connection does not necessarily mean that these protocols are available. Each
	protocol must be installed from Control Panel and then bound to the Dial-Up
	Networking adapter.
	
	
	Note that the symptom described in this article can also occur if there is a
	duplicate computer name on the subnet to which the remote access server is
	connected.
	
	The symptom described in this article can also occur if you are trying to use
	Dial-Up Networking to connect to your CompuServe account but the connection is
	not configured properly. For information about using Dial-Up Networking to
	connect to CompuServe, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q142490 How to Connect to the Internet Using DUN and CompuServe
	
	Additional query words: corrupt dial up
	
	======================================================================
	Keywords          : kberrmsg dun msnets win95 kbDialUp 
	Technology        : kbWin95search kbWin98search kbZNotKeyword3 kbWin98
	Version           : 95
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
