---
title: "error when running wine:("
date: 2011-12-19
forum: Wine
---

### Post by refmac5 on 2011-12-19
Hi all, I am newbie here. I was trying to use wine to install orbit downloader.  It keeps failing. Here is the error message.
Anyone can help me? thanks in advance!!

melody@work:~/Desktop$ chmod 755 OrbitSetup4.1.02.exe 
melody@work:~/Desktop$ wine OrbitSetup4.1.02.exe 
fixme:msg:ChangeWindowMessageFilter c055 00000001
fixme:win:DisableProcessWindowsGhosting : stub
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption Unhandled dwOption 4
fixme:wininet:INET_QueryOption Unhandled dwOption 5
fixme:win:WINNLSEnableIME hwnd 0x100d6 enable 0: stub!
fixme:win:WINNLSEnableIME hwnd 0x100d6 enable -1: stub!
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 1e on event 0
fixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
fixme:console:CONSOLE_DefaultHandler Terminating process 20 on event 0
err:ole:CoUninitialize Mismatched CoUninitialize

fixme:win:WINNLSEnableIME hwnd 0x100d6 enable -1: stub!

---

### Post by oldos2er on 2011-12-19
Moved to Wine.

---

### Post by mbuell on 2011-12-19
I want to ask you to move a step ahead. You are trying to install and run a particular program - "orbit downloader" - using Wine, yes? 

Ok - my first suggestion is to look for an alternative program that will manage downloads and works with Linux. Downthemall is a firefox plugin that manages this just fine in linux or windows. Look at what your requirements are - what do you NEED DONE?  

My reason to suggest using alternatives? Some stuff works using Wine - some doesn't. Way too many reasons - but I find stuff doesn't work more often than I find stuff that does work with Wine. 

If you still decide to pursue using "Orbit Downloader" - I suggest you post this question on the Wine forums. I think you would be more likely to find an answer there - rather than in the Ubuntu forums. 

Good luck.

---

