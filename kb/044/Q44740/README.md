---
layout: page
title: "Q44740: INFO: General Information About Windows WM_TIMER Messages"
permalink: /kb/044/Q44740/
---

## Q44740: INFO: General Information About Windows WM_TIMER Messages

{% raw %}

	Article: Q44740
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): kb16bitonly kbSDKPlatform kbGrpDSUser kbWndw
	Last Modified: 06-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Timers in the Windows environment are not synchronous; that is, when a timer
	"goes off," Windows does not stop processing and send a WM_TIMER message or call
	the timer event procedure. Instead, Windows sets some bits internally, to ensure
	that the task that "owns" the timer will run (as soon as the current task does
	something to yield control). When this task does eventually run and eventually
	calls GetMessage() or PeekMessage(), and there are no other messages available
	for this task, Windows will scan the timer list to see if any timers for this
	task have "gone off." If they have, Windows returns a WM_TIMER message or calls
	the timer event procedure. The following are two important facts that must be
	considered:
	
	1. The WM_TIMER message and timer-event process ONLY happen when an application
	  is sitting on a GetMessage() or PeekMessage(). They do not happen at timer
	  interrupt time.
	
	2. Only timers for the task that is currently active are scanned when looking
	  for messages. A PARTICULAR TIMER IS OWNED BY THE TASK THAT WAS ACTIVE WHEN
	  THE TIMER WAS CREATED.
	
	MORE INFORMATION
	================
	
	The following is an example of the incorrect use of timers:
	
	An application sets a keyboard hook. Inside the keyboard hook, a timer is set. It
	is important to realize that the keyboard hook is called from within
	GetMessage() or PeekMessage() whenever a task is pulling keys out of the system
	queue (the place where keyboard and mouse events go at interrupt level). The
	task that is active at the time the keyboard hook is called is completely
	random. Basically, it is the task that owns the windows with the focus.
	
	Because a timer is owned by the active task at the time it is created, and any
	task may be the active task when the keyboard hook is called, the timer created
	in this manner will be owned by some random task. This, combined with the
	following facts, results in inconsistent, random behavior for this timer.
	
	1. Timers are only scanned for the active task.
	
	2. Timers are retrieved at message level.
	
	3. All applications handle messages differently.
	
	The basic rule is that a timer MUST NEVER be created from within a hook such as a
	keyboard hook.
	
	Additional query words:
	
	======================================================================
	Keywords          : kb16bitonly kbSDKPlatform kbGrpDSUser kbWndw 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK300 kbWinSDK310
	Version           : WINDOWS:3.0,3.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
