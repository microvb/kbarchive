---
layout: page
title: "Q87134: Setting Up a 3Station to Remote Boot"
permalink: /kb/087/Q87134/
---

## Q87134: Setting Up a 3Station to Remote Boot

{% raw %}

	Article: Q87134
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SUMMARY
	=======
	
	Microsoft supports LAN Manager on 3Com 3Server 400/500/600 models. Other models
	use an 80186 and cannot be configured as LAN Manager servers. Both LAN Manager
	versions 2.0 and 2.1 should run equally well on all three types of machines. The
	LAN Manager 2.0 Value Pack does not provide any documentation on RIPL, and
	therefore is not a supported service for the 3Server.
	
	In LAN Manager 2.1, 3Com 3Station support is provided with the standard remote
	boot features. See Chapter 13 in the "Microsoft LAN Manager Administrator's
	Guide" for details on setup and possible problems.
	
	It is not necessary to create a special profile for the 3Station; just use the
	"DOS 5.00 Default" option from the RPL Manager drop menu selections, which
	appear as follows:
	
	  ===>  DOS 5.00 Default
	        DOS 5.00 3Com Etherlink
	        DOS 5.00 3Com Etherlink II
	        DOS 5.00 3Com Etherlink Plus
	        DOS 5.00 3Com Etherlink MC
	        DOS 5.00 IBM Ethernet
	        DOS 5.00 NOVELL NE 2000
	
	The DOS 5.00 Default profile option for the 3Station should cause it to start up
	correctly. If there are problems, you may have to manually edit the RPL.MAP file
	in the \LANMAN\RPL directory to change the acknowledge setting for 3Stations.
	
	Use an editor to search for the text string "3Station" in the RPL.MAP file. This
	should bring you to line 59, which should appear as follows:
	
	  yyyyyyyyyyyy BBLOCK\NETBEUI\E3STAT\DOSBB.CNF 2 6 F ~ DOS~3Com~3Station
	...
	
	Change line 59 to appear as follows:
	
	  yyyyyyyyyyyy BBLOCK\NETBEUI\E3STAT\DOSBB.CNF 2 6 A ~ DOS~3Com~3Station
	
	...
	
	                                                   ^
	                                                   |
	                                             Change is here
	
	This should eliminate problems with packet acknowledgement.
	
	Other issues to consider when troubleshooting a 3Station are as follows:
	
	- Check the net address of the 3Station. It should begin with 02608C in order
	  to be recognized by the DOS 5.00 Default profile.
	
	- 3Com 3Stations with new PROMs will have addresses out of the 20608C range and
	  will therefore require a change to the RPL.MAP to reflect use of the newer
	  PROM.
	
	- Make sure the two hidden system files are in the MS-DOS 5.0 directory.
	
	- Make sure the system file attributes are removed (no hidden or system
	  attribute).
	
	- Make sure 3Start is not running on the local net. 3Start assumes that no
	  other RPL server is on the local area network and will respond to all START
	  requests. Because 3Start and LAN Manager RPL use the same socket, RPL will
	  also try to respond to the request.
	
	- Make sure the 3Station is set up to use the correct transceiver. Press
	  CTRL+ALT+SHIFT+DEL to access the Setup program.
	
	Additional query words: 2.00 2.10 LM2.1 RPL
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
