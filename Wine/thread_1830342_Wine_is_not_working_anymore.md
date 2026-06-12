---
title: "Wine is not working anymore?"
date: 2011-08-21
forum: Wine
---

### Post by mystictartlet2012 on 2011-08-21
Hi, I am running Ubuntu 11.04. I had no internet so I connected the ethernet cable to the modem on my other PC. Thus, getting internet connection, I installed Wine. I was able to open .exe files on Wine yesterday but after I took off the ethernet cable, no internet connection anymore, I couldn't run any .exe files on Wine.

Before disconnecting the internet, though, I was able to run Rainmeter. It worked but after the internet disconnection, it just would run anymore. It was the same with all my other .exe files. 

It kept giving me the error 
```
Title: Program Error 
Description At The Top: The program winemenubuilder.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. 
Description At Bottom: This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.  

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org](http://bugs.winehq.org)
```Also, every time I click to open Wine, it shows a white box and a smaller rectangle that is also white. It seems to be frozen there, as it won't load anymore. I can right-click on the .exe file and choose to open it in Wine, it goes to the installation of the .exe file but when you click 'Finish' of the .exe file installation wizard, it shows the code above. 

Is it that I  have to be connected to the internet to be able to use Wine?

---

### Post by BlinkinCat on 2011-08-21
If you don't get an answer here you may also try -

[http://forum.winehq.org/viewforum.php?f=2](http://forum.winehq.org/viewforum.php?f=2)

---

### Post by snip3r8 on 2011-08-21
Wine does not require an Internet connection to work,i think your troubles are unrelated to the Internet connection and related to the fact that wine is buggy and doesn't always work.I find it is better to find Linux alternatives than to run wine.

---

### Post by kyletstrand on 2011-08-21
What specific programs have you been trying to run?  What version of Wine are you using?

---

### Post by blade4 on 2011-08-21
Try running the exe file with wine from terminal and post the output here .... that may help clarify the error .

---

### Post by mystictartlet2012 on 2011-08-21
> **kyletstrand said:**
> What specific programs have you been trying to run?  What version of Wine are you using?

The programs I've been trying to run are Rainmeter, Windows down-loadable games, and ObjectDock. The version of Wine I am using is Wine 1.3.26 


> **blade4 said:**
> Try running the exe file with wine from terminal and post the output here .... that may help clarify the error .  

In terminal, I typed 
```
wine '/home/shikiti/RAINmet/Rainmeter.exe'
```I get these results
```
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
^[0Afixme:win:EnumDisplayDevicesW ((null),0,0x32f3a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x32f05c, 0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",1,0x32f05c, 0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),1,0x32f3a4,0x00000000), stub!
fixme:shell:IQueryAssociations_fnGetString 00000020: unimplemented flags!
fisme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fisme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:mscoree:_CorDllMain (0x780000), 1, (nil)): stub
wine: Unhandled page fault on read access to 0x06000003 at address 0x6000003 (thread 0009), starting debugger...
```It stops there, then a 'Program Error' box pops out saying:
The program Rainmeter.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. 

This can be caused by a problem in the program or a deficiency in Wine. You may want to check  [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been reported yet, you can report it at  [http://bugs.winehq.org](http://bugs.winehq.org).

---

### Post by uRock on 2011-08-21
Moved to *Wine*.

---

### Post by mystictartlet2012 on 2011-08-21
> **uRock said:**
> Moved to *Wine*.

Link..?

---

### Post by uRock on 2011-08-22
> **mystictartlet2012 said:**
> Link..?

I moved the thread to the Wine sub-forum.> Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Wine > Wine is not working anymore?

---

### Post by thatguruguy on 2011-08-22
Wow, that small font is really hard to read.

---

### Post by thatguruguy on 2011-08-24
It seems as though your installation of Wine may have been corrupted.  Have you tried removing it completely and reinstalling?

As an aside, have you considered trying the program "conky" which is available in the software center?  It provides all the functionality that Rainmeter apparently provides, but runs natively on Linux.

---

