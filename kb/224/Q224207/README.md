---
layout: page
title: "Q224207: S&amp;T 2000: Circles Around Direction Arrows Are Transparent"
permalink: /kb/224/Q224207/
---

## Q224207: S&amp;T 2000: Circles Around Direction Arrows Are Transparent

{% raw %}

	Article: Q224207
	Product(s): Microsoft Automap
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbenv kbprint kbimu
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Expedia Streets and Trips 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you use a black-and-white printer to print turn-by-turn maps for a route in
	Microsoft Expedia Streets and Trips 2000, the circles around the direction
	arrows on the turn-by-turn maps may be transparent. This can make it difficult
	to read or recognize the arrows on the map.
	
	CAUSE
	=====
	
	This behavior can occur if the following conditions are true:
	
	- You are running Expedia Streets and Trips 2000 on a Microsoft Windows
	  95/98-based computer.
	
	- You are not using a PostScript printer driver to print the map.
	
	RESOLUTION
	==========
	
	To resolve this issue, use one of the following methods.
	
	Install a PostScript Printer Driver
	-----------------------------------
	
	If your printer supports PostScript printing, install a PostScript driver for
	your printer. For information about how to install printer drivers in Windows,
	click Start, click Help, click the Index tab, type "printer setup" (without the
	quotation marks), and then click Display.
	
	Print the Map Using Raster Graphics
	-----------------------------------
	
	To print the map using raster graphics, use the following steps.
	
	NOTE: This method only changes the printer settings for one print job. To
	permanently change the printer settings, follow the instructions in the "More
	Information" section of this article.
	
	1. On the File menu in Expedia Streets and Trips 2000, point to Print, and then
	  click Map Or Driving Directions.
	
	2. Under Print, click Driving Directions, and then click With Turn-By-Turn Maps.
	
	3. In the Name box under Printer, click the printer you want to use, and then
	  click Properties.
	
	4. On the Graphics tab, click Use Raster Graphics, and then click OK.
	
	5. Click OK to print the map.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Expedia Streets and
	Trips 2000.
	
	MORE INFORMATION
	================
	
	To permanently configure the printer to print raster graphics, follow these
	steps:
	
	1. Click Start, point to Settings, and then click Printers.
	
	2. Right-click the printer you want to use, and then click Properties.
	
	3. On the Graphics tab, click Use Raster Graphics, and then click OK.
	
	4. Close the Printers window.
	
	Additional query words: multi media mm amap auto-map invisible missing
	
	======================================================================
	Keywords          : kbenv kbprint kbimu 
	Technology        : kbHomeProdSearch kbExpediaSearch kbExpediaStreets2000
	Version           : WINDOWS:
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
