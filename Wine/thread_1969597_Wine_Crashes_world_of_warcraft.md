---
title: "Wine Crashes world of warcraft"
date: 2012-04-30
forum: Wine
---

### Post by Smakone on 2012-04-30
Hello

I recently switched to ubuntu and I managed to get wow running on ubuntu with some help from the blizzard support

they assisted me with installations due to a bugged launcher that now runs smoothly without bugs and updates automaticly

I did not install the game thru wine but installed it on a windows computer and copied it over to my ubuntu computer with a extern harddrive usb 3.0

The game runs smoothly with one issue

Wine crashes, sometimes due to cinematics, sometimes when I change continents and sometimes when I switch characters. But also when I play regularly

This is what happens in the terminal when wine crashes


fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0055), starting debugger...
Can't attach process 0054: error 5
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
wine: Unhandled page fault on write access to 0x0000001c at address 0x598bbb (thread 0080), starting debugger...
jocke@jocke-K53SV:~$ Can't attach process 0025: error 5
^C
jocke@jocke-K53SV:~$ 

Any solution to this problem is more then welcome, I'm currently using opengl which fixed the graphic bugs that has been implemented in world of warcraft since the early versions and only visible on pirate realms

Also when I try to start the game after a crash without rebooting the system the terminal gives this information


"jocke@jocke-K53SV:~$ wine explorer
fixme:nstc:NSTC2_fnSetControlStyle2 mask & style (0x00000004) contains unsupported style(s): 0x00000004
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a003, 0, 0x32f4e4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a004, 1, 0x32f4e4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a003, 1, 0x32f4e4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a004, 1, 0x32f4e4)
fixme:shell:IExtractIconW_fnExtract (0x13e648) (file=0x7bcc24ab index=-35 (nil) 0x32f3b8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x141540) (file=0x7bcc218e index=-16 (nil) 0x32f3b8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x141838) (file=0x7bcc21b4 index=-235 (nil) 0x32f3b8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x140d68) (file=0x7bcc2205 index=-33 (nil) 0x32f3b8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x142c28) (file=0x7bcc222c index=-9 (nil) 0x32f3b8 size=00000014) semi-stub
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x13e990)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a003, 0, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a004, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a003, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a004, 1, 0x32ebe4)
fixme:shell:IExtractIconW_fnExtract (0x142de8) (file=0x7bcc2311 index=-35 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x140d68) (file=0x7bcc2337 index=-16 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x1400d0) (file=0x7bcc235d index=-235 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x141838) (file=0x7bcc2383 index=-33 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x140948) (file=0x7bcc23aa index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x147a58)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a003, 0, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a004, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a003, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a004, 1, 0x32ebe4)
fixme:shell:IExtractIconW_fnExtract (0x143820) (file=0x7bcc23d0 index=-35 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x141838) (file=0x7bcc23f6 index=-16 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x147ad0) (file=0x7bcc241c index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x148fe8) (file=0x7bcc2442 index=-235 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x1283b0) (file=0x7bcc2468 index=-33 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x140888) (file=0x7bcc248f index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x14b868)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a003, 0, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a004, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a003, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a004, 1, 0x32ebe4)
fixme:shell:IExtractIconW_fnExtract (0x1427c8) (file=0x7bcc21a6 index=-35 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x149498) (file=0x7bcc21cc index=-16 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x13fc20) (file=0x7bcc21f2 index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c518) (file=0x7bcc2218 index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x141838) (file=0x7bcc223e index=-235 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c9e8) (file=0x7bcc2264 index=-33 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14cd58) (file=0x7bcc228b index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x14b650)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a003, 0, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a004, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a003, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a004, 1, 0x32ebe4)
fixme:shell:IExtractIconW_fnExtract (0x13f760) (file=0x7bcc22b1 index=-35 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x140390) (file=0x7bcc22d7 index=-16 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c458) (file=0x7bcc22fd index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c2f8) (file=0x7bcc2323 index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c478) (file=0x7bcc2349 index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14b818) (file=0x7bcc236f index=-235 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c250) (file=0x7bcc2395 index=-33 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x1506a8) (file=0x7bcc23bc index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x14c7e8)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a003, 0, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a004, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a003, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a004, 1, 0x32ebe4)
fixme:shell:IExtractIconW_fnExtract (0x13f760) (file=0x7bcc246f index=-35 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x151950) (file=0x7bcc2495 index=-16 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c478) (file=0x7bcc24bb index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14c458) (file=0x7bcc2168 index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x13ed58) (file=0x7bcc218e index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x1492e8) (file=0x7bcc21b4 index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x152450) (file=0x7bcc21da index=-235 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x154258) (file=0x7bcc2200 index=-33 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x153fb0) (file=0x7bcc2227 index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x141188)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a003, 0, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1026, a004, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a003, 1, 0x32ebe4)
fixme:shell:IShellBrowser_fnSendControlMsg stub, 0x1365d0 (2, 1025, a004, 1, 0x32ebe4)
fixme:shell:IExtractIconW_fnExtract (0x153de0) (file=0x7bcc224d index=-35 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x152a18) (file=0x7bcc2273 index=-16 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x13fc40) (file=0x7bcc2299 index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x13f4a8) (file=0x7bcc22bf index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x13fc60) (file=0x7bcc22e5 index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x147a90) (file=0x7bcc230b index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x157778) (file=0x7bcc2331 index=-4 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x1575d0) (file=0x7bcc2357 index=-235 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x14be70) (file=0x7bcc237d index=-33 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IExtractIconW_fnExtract (0x1566b8) (file=0x7bcc23a4 index=-9 (nil) 0x32eab8 size=00000014) semi-stub
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x14eff0)
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:exec:SHELL_execute flags ignored: 0x0000000c
fixme:process:GetLogicalProcessorInformation (0x33e498,0x33ea98): stub
fixme:wbemprox:wbem_locator_ConnectServer 0x13a070, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e840)
fixme:wbemprox:wbem_locator_ConnectServer 0x139fc0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e7b4)
fixme:wbemprox:wbem_locator_ConnectServer 0x139ef0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e8c0)
fixme:wbemprox:wbem_locator_ConnectServer 0x13a2c8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e678)
fixme:wbemprox:wbem_locator_ConnectServer 0x13a2f0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e860)
fixme:shell:IShellBrowser_fnOnViewWindowActive stub, 0x1365d0 (0x14eff0)
fixme:exec:SHELL_execute flags ignored: 0x0000000c
fixme:process:GetLogicalProcessorInformation (0x33e498,0x33ea98): stub
fixme:wbemprox:wbem_locator_ConnectServer 0x13a070, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e840)
fixme:wbemprox:wbem_locator_ConnectServer 0x139fc0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e7b4)
fixme:wbemprox:wbem_locator_ConnectServer 0x139ef0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e8c0)
fixme:wbemprox:wbem_locator_ConnectServer 0x13a2c8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e678)
fixme:wbemprox:wbem_locator_ConnectServer 0x13a2f0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e860)
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8e on event 0
jocke@jocke-K53SV:~$ "

A solution to this would be nice aswell since Im new to ubuntu

---

### Post by Smakone on 2012-05-01
this is what the terminal says on startup of wow thru the launcher


fixme:win:EnumDisplayDevicesW ((null),0,0x33ed20,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ebe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f0c0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f008,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eec8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33efe8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eea8,0x00000000), stub!
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
archive data\enGB\agreements.mpq opened
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub


and this is when It crashes in orgrimmar due to my guess being something that makes wine unable to process or handle the framerate that the processor can acess thru ubuntu. wild guesses ofc, someone abit more experienced with programming might have another point of view to this problem.....

(side story, I've managed to level a gnome female warlock all the way to orgrimmar without crashes when wine decided to crash on the wolf (probably due to terrain textures not loading while framerates maxed out)

This also happens on cinematic intros except the goblin one.

fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
fixme:process:GetLogicalProcessorInformation (0x1afe340,0x1afe940): stub
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 0051), starting debugger...
Can't attach process 0050: error 5

and this is when I have to terminate the wow window

^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
wine: Unhandled page fault on write access to 0x0000001c at address 0x598bbb (thread 002b), starting debugger...
jocke@jocke-K53SV:~$ Can't attach process 0025: error 5
^C
jocke@jocke-K53SV:~$ 

and also when wine explorer crashes. So my newbie point of view would be that the problem is that wine has to emulate windows in order to run the game and the only logical solution from my point of view would be to get the game to run without wine. This is probably possible if someone has the willpower and the time to figure out a solution...

Still waiting on another point of view tho

would appreciate a protip on how to tweak my processor or framerate / fps in order to test this further

---

### Post by Smakone on 2012-05-01
I've been trying to acess applications thru the terminal in order to load an ubuntu based game to test the framerates but I cant find any commands for that occassion

Managed to find something called gprocessor or gnash tools which might allow a test of my thesis. These programs seems a bit to complicated for my basic computer knowledge but if someone with experience of similiar issues has the interest to test this and post in this thread this might get resolved

---

### Post by cwwilson721 on 2012-05-01
Maybe tell us your hardware? Wine version?

---

### Post by Smakone on 2012-05-02
using wine version 1.4

and

Processer Intel® CoreT i7 Mobile 2670QM
Intel®
Model SerieCoreT i7 Mobile
Model2670QM
Clockfrequens 2.2 GHz
Bus speed t5 GT/s
Core type Quad Core
L2
L3 6 MB
SocketSocket BGA988
Compatibility 64-bit SSE SSE2 SSE3 SSE4 Intel VT
Micron-technology 32 nm
Thermical effect 45 Watt

Graphic Card nVIDIA GeForce GT 630M 2 048 MB
Graphiccard processor nVIDIA GeForce GT 630M
Graphic card Ram memory 2 048 MB
Dedicated memory 2 048 MB
Ram 6 144 MB
Memory amount 6 144 MB
Max memory 8 192 MB
Memorytype SO-DIMM DDR III
Memoryspeed 1 333 MH

Harddrive 750 GB

Should be more then enough for world of playcraft
My other theory goes somewhere of the line of: The processor is fast enough to load more then windows can handle

---

### Post by cwwilson721 on 2012-05-02
Nine times out of ten, the issues you have are from Graphics Drivers.

You DID install the Nvidia Drivers from Additional Drivers, correct?

---

### Post by Smakone on 2012-05-02
Ok

this happens If I try to update to the latest version

[http://oi46.tinypic.com/2cwlcv6.jpg](http://oi46.tinypic.com/2cwlcv6.jpg)

this happens if I update to the version beneath it

[http://oi45.tinypic.com/fntyz8.jpg](http://oi45.tinypic.com/fntyz8.jpg)

this is what I've got installed

[http://oi49.tinypic.com/xm639h.jpg](http://oi49.tinypic.com/xm639h.jpg)

It's in swedish but I think it'll make sense anyway

If not

[http://oi50.tinypic.com/2lt32i8.jpg](http://oi50.tinypic.com/2lt32i8.jpg)

---

### Post by Smakone on 2012-05-02
I highly doubt that graphic drivers are the issue here

[http://oi50.tinypic.com/2a9xjlf.jpg](http://oi50.tinypic.com/2a9xjlf.jpg)

---

### Post by Smakone on 2012-05-03
found this

[http://bugs.winehq.org/show_bug.cgi?id=24193](http://bugs.winehq.org/show_bug.cgi?id=24193)

seems to be the same bug as I'm experiencing... but I'm using wine 1.3 and the status says status is fixed

also this:

[http://forum.winehq.org/viewtopic.php?t=9796&sid=e78ecbf809e2cfe8e6a0541abe9b82b7](http://forum.winehq.org/viewtopic.php?t=9796&sid=e78ecbf809e2cfe8e6a0541abe9b82b7)

and this:

[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/632206](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/632206)

Cant make any sense out of this atm since I just woke up. Some assistance would be most appreciated

---

### Post by Smakone on 2012-05-04
Update:

Made a ticket to blizzard asking them why wine crashes wow

Also refered them to this thread and showed them usage of sixaxis ingame

I also linked a screenshot to the program manager refering them to ryzom and asking them why their games werent accesibable thru the smartphone layer

Best of luck to blizzard solving this problem... I have no further ideas on this topic

Except if someone opened the blinds on the "wow window" cos it stays unresponsive

---

### Post by Smakone on 2012-05-04
I've sucessfully managed to throw some heals ingame using the sixaxis in world of warcraft but the wine problem remains. It crashes when I try to join instances or run around in the world in travelform

:KS

---

### Post by Smakone on 2012-05-08
Blizzard responed to another ticket refering me to other forums for this issue^

Gourgetiom
Customer Service Representative
Hello,

Unfortunately the last Game Master was correct we really do not support the game run on a system other than Windows or OSX.

However, there are good forums out there for help with just this type of issue;

[http://ubuntuforums.org/showthread.php?p=11890823](http://ubuntuforums.org/showthread.php?p=11890823)

This is always a good place to check, I use it a lot for my laptop when I have issues and while I admit, World of Warcraft crashes on my system too, you may find the answers you need here.

It is not a World of Warcraft site or a Blizzard site, so be careful about links you click.

I wish I could offer more information on this issue but the issue is it could be anything from software to hardware. If you find a soultion to this, let me know please!

Kind regards,

Game Master Gourgetion
Game Master Team
For quick help on topics
[http://www.youtube.com/blizzardtutorial](http://www.youtube.com/blizzardtutorial)


Currently troubleshooting this issue further and I also made a post here in the blizzard forums

[http://eu.battle.net/wow/en/forum/topic/3980428060](http://eu.battle.net/wow/en/forum/topic/3980428060)



Some more information about my issue:

Wine is set to windows 7. same as the installation of world of warcraft that I copied over to this ubuntu laptop

Wine version is the latest stable version which is 1.4.x.x.x.x or so

My current solution is that there's something wrong with the loading of the world or world textures which causes ubuntu to crash wine due to the fact that the "wow window" does not allow the textures to load

I've managed to almost be able to turn my character in orgrimmar 360 degrees by rebooting and logging back in I've also managed to sucessfully enter an instance from the looking for dungeon thingy but instantly when I entered the instance wine crashed......

Currently looking for different solutions then constantly logging in.... crashing.... rebooting... logging in.... getting a bit further..... crashing

My "gamepad" also works fine ingame and It is possible to bind all of the keys on the Gamepad to keys used to either cast spells or open bags

I will keep looking for a better solution if nothing else comes up!

---

### Post by Smakone on 2012-05-08
A new take on this issue

My Ubuntu is 32 bit and the windows installation was for windows 64 bit

This could very well be the reason that wine crashes

Looking further into this atm

[http://askubuntu.com/questions/74690/how-to-install-32-bit-wine-on-64-bit-ubuntu](http://askubuntu.com/questions/74690/how-to-install-32-bit-wine-on-64-bit-ubuntu)

Seems like this should not be an issue

---

### Post by Smakone on 2012-05-08
When The Game crashes the sound keeps looping in the background so this issue is probably Graphic related

Basicly the "Window" Just freezes and turns grey

---

### Post by Smakone on 2012-05-08
Found the issue

Using wrong graphic driver since I Have an Nvidia card

Yet I cant seem to make this work


Here's what I want to do but I cant find any way around it

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)


Here's my current graphic driver

[http://tinypic.com/view.php?pic=a9q1d&s=6](http://tinypic.com/view.php?pic=a9q1d&s=6)

What is a Sandybridge???

---

### Post by Smakone on 2012-05-08
Found this

[http://www.techlw.com/2012/03/install-nvidia-drivers-on-ubuntu-1204.html](http://www.techlw.com/2012/03/install-nvidia-drivers-on-ubuntu-1204.html)

---

### Post by Smakone on 2012-05-08
current location**

[http://oi48.tinypic.com/34sjln6.jpg](http://oi48.tinypic.com/34sjln6.jpg)

Now I just have to solve this

[http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-use-nvidia-x-driver-742118/](http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-use-nvidia-x-driver-742118/)

Cant seem to get those commands to work atm

Cant get "nvidixa xconfig" to run as root

Might have solved it
[http://oi49.tinypic.com/2afk2f5.jpg](http://oi49.tinypic.com/2afk2f5.jpg)

---

### Post by Tweak42 on 2012-05-10
I'm impressed that Blizzard actually tried to help you get Wow running on linux.

With the odd issues you are having getting the nvidia drivers running, I think it maybe something to do with the Nvidia Optimus hybrid graphics implimentation of your laptop.  

"Sandybridge" is the Intel i7 mobile cpu, which has a intergrated graphics controller. It can do 3D rendering, but not very well. 

Nvidia Optimus is a special video pipeline that when software detects certain 3D programs, Optimus will power up the GeForce GT 630M and take over video output from the Intel graphics. (by default the Geforce is turned off)  This software switch overworks fine on windows, but is a work in progress for linux.

Try googling for "nvidia optimus bumblebee" if you want to try linux hybrid graphics switching.

Alternatively on some laptops it's possible in the bios to set the nvidia video to always on, which should allow you to load the nvidia drivers from the PPA normally.  The trade off is battery life since the Nvidia chip consumes alot more power than the integrated intel.


NOTE: I have don't have any hands on experience with Optimus, but I've been following it since it will likely be on my next laptop purchase.

---

### Post by Smakone on 2012-05-10
Will try this when I have the opportunity

Ty for the answer

---

### Post by cwwilson721 on 2012-05-10
Dang.

Tweak42 got me again....Forgot about the "Hybrid"

---

### Post by Smakone on 2012-05-12
Currently got the nvidia drivers installed but I need to use some commands to start them

These commands seems to run randomly

I've sucesfully managed to open Optirun glxgears once but after that the terminal "locked" the command

Also having some trouble with finding the wow.exe file with wine thru Optirun wine wow.exe
Need to find a proper path to this folder but after that It will be up and running smoothly still some work in progress tho

useful link: [https://wiki.archlinux.org/index.php/Bumblebee](https://wiki.archlinux.org/index.php/Bumblebee)

managed to get optirun working properly

By using^

Optirun

in terminal

found some commands under optirun --help

and also 

optirun glxspheres

which provides this very graphic image:

[http://oi46.tinypic.com/2s8i5x3.jpg](http://oi46.tinypic.com/2s8i5x3.jpg)

and this is what the glxgears shows

[http://oi45.tinypic.com/2ef2vb7.jpg](http://oi45.tinypic.com/2ef2vb7.jpg)

still working on getting the wow.exe running but the graphiccard should be working fine atm

Updating when I've solved a proper path for the world of warcraft executable

bash: cd/home/world_of_warcraft/: Filen eller katalogen finns inte
jocke@jocke-K53SV:~$ optirun nautilus
jocke@jocke-K53SV:~$ optirun wow.exe
/usr/bin/vglrun: 296: exec: wow.exe: not found
jocke@jocke-K53SV:~$ optirun wine wow.exe
wine: cannot find L"C:\\windows\\system32\\wow.exe"
jocke@jocke-K53SV:~$ optirun wine 

atm I need to figure out a proper path for wine to take while skipping the windows part of the command trying to figure out where the file is located in ubuntu whilst it is located in my home file

---

### Post by Smakone on 2012-05-12
jocke@jocke-K53SV:~$ optirun bash
jocke@jocke-K53SV:~$ cd~
No command 'cd~' found, did you mean:
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdi' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdw' from package 'cdw' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
 Command 'cd5' from package 'cd5' (universe)
cd~: command not found
jocke@jocke-K53SV:~$ optirun cd~ wine wow.exe
/usr/bin/vglrun: 296: exec: cd~: not found
jocke@jocke-K53SV:~$ optirun wine cd~ wow.exe
wine: cannot find L"C:\\windows\\system32\\cd~.exe"
jocke@jocke-K53SV:~$ optirun wine 

:D

---

### Post by Smakone on 2012-05-12
seems like wine requested a wow.exe file in the windows system32 folder

so I added it and ran 

Optirun wine wow.exe

this happened

excitement reaching me atm while the odd bar is updating

[http://oi45.tinypic.com/dcbfo3.jpg](http://oi45.tinypic.com/dcbfo3.jpg)

---

### Post by Smakone on 2012-05-12
current status

[http://oi48.tinypic.com/15gb2w4.jpg](http://oi48.tinypic.com/15gb2w4.jpg)

2 soon???


[http://www.youtube.com/watch?v=SocqAdg_oP0](http://www.youtube.com/watch?v=SocqAdg_oP0)

---

### Post by Smakone on 2012-05-12
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
fixme:process:GetLogicalProcessorInformation (0x19fe300,0x19fe900): stub
fixme:process:GetLogicalProcessorInformation (0x19fe300,0x19fe900): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
fixme:wininet:URLCache_FindFirstFreeEntry Grow file
err:wininet:CommitUrlCacheEntryInternal no free entries
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
fixme:process:GetLogicalProcessorInformation (0x81be300,0x81be900): stub
err:wgl:internal_SetPixelFormat Invalid operation on root_window
ajocke@jocke-K53SV:~$ 

some login error atm trying to access the same way but with launcher instead of exe

---

### Post by Smakone on 2012-05-12
[http://oi50.tinypic.com/1z15gue.jpg](http://oi50.tinypic.com/1z15gue.jpg)

the dragon is not moving

[http://oi45.tinypic.com/18g7s3.jpg](http://oi45.tinypic.com/18g7s3.jpg)

here we go with launcher

[http://oi48.tinypic.com/zlt8jr.jpg](http://oi48.tinypic.com/zlt8jr.jpg)

and now to solve this I guess I just copy all the wow files from my world of warcraft folder on my ubuntu disc into the wine version of windows system 32

---

### Post by Smakone on 2012-05-12
my wow is now unfoldered in the system 32 folder

this happened when I moved it there

[http://oi46.tinypic.com/23kt0eh.jpg](http://oi46.tinypic.com/23kt0eh.jpg)

Translated "The window wine explorer is not responding"
                Cancel / Force quit


And now Optirun is giving me trouble again :D

[http://oi50.tinypic.com/1053cjp.jpg](http://oi50.tinypic.com/1053cjp.jpg)


almost there

this Op ti run 

****** Op

matter of a capital letter

[http://oi45.tinypic.com/wb9suc.jpg](http://oi45.tinypic.com/wb9suc.jpg)

---

### Post by Smakone on 2012-05-12
status 

[http://oi47.tinypic.com/6r7x4h.jpg](http://oi47.tinypic.com/6r7x4h.jpg)

got the repair to run and repair said that wow was repaired

now this happened


[http://oi50.tinypic.com/244d2jt.jpg](http://oi50.tinypic.com/244d2jt.jpg)

managed to run launcher with an internal error

---

### Post by Smakone on 2012-05-12
This is funny Now I managed to get autenticater login screen and this is what the login manager says

[http://oi50.tinypic.com/jht18y.jpg](http://oi50.tinypic.com/jht18y.jpg)

blizzard if you are reading this I signed up for 6 months

---

### Post by Smakone on 2012-05-12
the dragon is moving with optirun wine wow.exe but the launcher keeps crashing

I can update the game with other launchers saved on other folders of world of warcraft on my laptop but

still saying that I dont have a wow game attached to my account

Printscreen of the dragon

Deathwing..... you beaty

[http://oi45.tinypic.com/35c2786.jpg](http://oi45.tinypic.com/35c2786.jpg)

these graphics rules

---

### Post by Smakone on 2012-05-12
My repair switched me over to the enUS instead of enGB

Currently making a ghost account to have some fun until a solution appears

currently logged in under the name "Gamepad" on some realm

Playing with sixaxis bound to gnome in qtsixa wireless bluetooth but I just wish falk would update the possible binds to be able to bind mouse movement to arrow keeys since the "pads" or "axis" are a bit smoother to run around with... also the axises are pressable and I've found no such bind options

Best of luck to all of you that might have experienced similiar issues

Pad out



Will update when I hear from blizzard

---

### Post by Smakone on 2012-05-12
First crash with optirun


fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
wine: Unhandled page fault on read access to 0x00000008 at address 0x7e723a2a (thread 0024), starting debugger...
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.


Will test this further got a possibility to send a bug report but accidentally closed the terminal

might be because the downloader is downloading game content in the background

here's a print

[http://oi49.tinypic.com/24exohc.jpg](http://oi49.tinypic.com/24exohc.jpg)

If wow crashes again I will document the issues

Graphic looks better then ever and I managed to get all the way thru the intro movie which usually crashed it with the sandybridge driver thru just wine

---

### Post by Smakone on 2012-05-12
Crashed again while exiting 0-5 belf area

Here's the info


Unhandled exception: page fault on read access to 0x93e1bd6c in 32-bit code (0x7e738a04).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e738a04 ESP:016fa490 EBP:016fa4f8 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:00000002 EBX:7e76bff4 ECX:00000000 EDX:93e1bd6c
 ESI:263c6108 EDI:000020a4
Stack dump:
0x016fa490:  016fa5ec 263c61cc 000020a4 00000000
0x016fa4a0:  00000000 23a99080 7bca6ff4 23a99070
0x016fa4b0:  22f03000 016fa504 7bc46923 016fa5ec
0x016fa4c0:  00000002 016fa514 00000000 263c61a0
0x016fa4d0:  00000000 b755aa80 00000200 00000000
0x016fa4e0:  00110000 00000000 7bc3512f 7e76bff4
Backtrace:
=>0 0x7e738a04 in wininet (+0x18a04) (0x016fa4f8)
  1 0x7e73906f in wininet (+0x1906e) (0x016fa578)
  2 0x7e74c026 InternetReadFileExA+0x65() in wininet (0x016fa5c8)
  3 0x007b47d8 in wow (+0x3b47d7) (0x016fe94c)
  4 0x007df595 in wow (+0x3df594) (0x016fe980)
  5 0x007e393a in wow (+0x3e3939) (0x016fe994)
  6 0x00a12a8e in wow (+0x612a8d) (0x016fe9cc)
  7 0x00a12b36 in wow (+0x612b35) (0x016fe9d8)
  8 0x7bc71da0 call_thread_func_wrapper+0xb() in ntdll (0x016fe9e8)
  9 0x7bc7485d call_thread_func+0x7c() in ntdll (0x016feab8)
  10 0x7bc71d7e RtlRaiseException+0x21() in ntdll (0x016fead8)
  11 0x7bc7a738 in ntdll (+0x6a737) (0x016ff328)
  12 0xb750fd4c start_thread+0xcb() in libpthread.so.0 (0x016ff428)
0x7e738a04: movl	0x0(%edx),%ecx
Modules:
Module	Address			Debug info	Name (150 modules)
PE	  400000- 10dc000	Export          wow
PE	3c910000-3cbc4000	Deferred        battle.net
ELF	7b800000-7ba15000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba15000	\               kernel32
ELF	7bc00000-7bcc3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ce79000-7ce91000	Deferred        libresolv.so.2
ELF	7ce91000-7ceda000	Deferred        libdbus-1.so.3
ELF	7ceda000-7ceec000	Deferred        libp11-kit.so.0
ELF	7ceec000-7cf71000	Deferred        libgcrypt.so.11
ELF	7cf71000-7cf83000	Deferred        libtasn1.so.3
ELF	7cf83000-7cfab000	Deferred        libk5crypto.so.3
ELF	7cfab000-7d07a000	Deferred        libkrb5.so.3
ELF	7d5ec000-7d5f5000	Deferred        librt.so.1
ELF	7d5f5000-7d5fe000	Deferred        libkrb5support.so.0
ELF	7d5fe000-7d610000	Deferred        libavahi-client.so.3
ELF	7d610000-7d6d4000	Deferred        libgnutls.so.26
ELF	7dbaa000-7dbaf000	Deferred        libgpg-error.so.0
ELF	7dbaf000-7dbbd000	Deferred        libavahi-common.so.3
ELF	7dbbd000-7dbfb000	Deferred        libgssapi_krb5.so.2
ELF	7dbfb000-7dc4e000	Deferred        libcups.so.2
ELF	7dc54000-7dc67000	Deferred        gnome-keyring-pkcs11.so
ELF	7dc67000-7dc9b000	Deferred        uxtheme<elf>
  \-PE	7dc70000-7dc9b000	\               uxtheme
ELF	7dd67000-7dd6d000	Deferred        libxfixes.so.3
ELF	7dd6d000-7dd78000	Deferred        libxcursor.so.1
ELF	7dd78000-7dd7c000	Deferred        libkeyutils.so.1
ELF	7dd7c000-7dd81000	Deferred        libcom_err.so.2
ELF	7ddf1000-7de1b000	Deferred        libexpat.so.1
ELF	7de1b000-7de4f000	Deferred        libfontconfig.so.1
ELF	7de4f000-7de5f000	Deferred        libxi.so.6
ELF	7de5f000-7de63000	Deferred        libxcomposite.so.1
ELF	7de63000-7de6c000	Deferred        libxrandr.so.2
ELF	7de6c000-7de76000	Deferred        libxrender.so.1
ELF	7de76000-7de7c000	Deferred        libxxf86vm.so.1
ELF	7de9d000-7df30000	Deferred        winex11<elf>
  \-PE	7deb0000-7df30000	\               winex11
ELF	7df30000-7dfca000	Deferred        libfreetype.so.6
ELF	7dfca000-7dfe9000	Deferred        libtinfo.so.5
ELF	7dfe9000-7e00b000	Deferred        libncurses.so.5
ELF	7e024000-7e04c000	Deferred        msacm32<elf>
  \-PE	7e030000-7e04c000	\               msacm32
ELF	7e04c000-7e0f9000	Deferred        winmm<elf>
  \-PE	7e050000-7e0f9000	\               winmm
ELF	7e0f9000-7e133000	Deferred        winspool<elf>
  \-PE	7e100000-7e133000	\               winspool
ELF	7e133000-7e19a000	Deferred        setupapi<elf>
  \-PE	7e140000-7e19a000	\               setupapi
ELF	7e19a000-7e20f000	Deferred        rpcrt4<elf>
  \-PE	7e1b0000-7e20f000	\               rpcrt4
ELF	7e20f000-7e317000	Deferred        ole32<elf>
  \-PE	7e230000-7e317000	\               ole32
ELF	7e317000-7e333000	Deferred        dinput8<elf>
  \-PE	7e320000-7e333000	\               dinput8
ELF	7e333000-7e365000	Deferred        ws2_32<elf>
  \-PE	7e340000-7e365000	\               ws2_32
ELF	7e365000-7e45d000	Deferred        comctl32<elf>
  \-PE	7e370000-7e45d000	\               comctl32
ELF	7e45d000-7e66e000	Deferred        shell32<elf>
  \-PE	7e470000-7e66e000	\               shell32
ELF	7e66e000-7e6d8000	Deferred        shlwapi<elf>
  \-PE	7e680000-7e6d8000	\               shlwapi
ELF	7e6d8000-7e6fe000	Deferred        mpr<elf>
  \-PE	7e6e0000-7e6fe000	\               mpr
ELF	7e6fe000-7e714000	Deferred        libz.so.1
ELF	7e714000-7e783000	Dwarf           wininet<elf>
  \-PE	7e720000-7e783000	\               wininet
ELF	7e783000-7e7a5000	Deferred        imm32<elf>
  \-PE	7e790000-7e7a5000	\               imm32
ELF	7e7a5000-7e8d9000	Deferred        wined3d<elf>
  \-PE	7e7b0000-7e8d9000	\               wined3d
ELF	7e8d9000-7e912000	Deferred        d3d9<elf>
  \-PE	7e8e0000-7e912000	\               d3d9
ELF	7e912000-7e92c000	Deferred        libice.so.6
ELF	7e92c000-7e935000	Deferred        libsm.so.6
ELF	7e935000-7e939000	Deferred        libxinerama.so.1
ELF	7e939000-7e94e000	Deferred        hid<elf>
  \-PE	7e940000-7e94e000	\               hid
ELF	7e94e000-7ea08000	Deferred        opengl32<elf>
  \-PE	7e970000-7ea08000	\               opengl32
ELF	7ea08000-7ea68000	Deferred        advapi32<elf>
  \-PE	7ea10000-7ea68000	\               advapi32
ELF	7ea68000-7eb25000	Deferred        gdi32<elf>
  \-PE	7ea70000-7eb25000	\               gdi32
ELF	7eb25000-7ec65000	Deferred        user32<elf>
  \-PE	7eb40000-7ec65000	\               user32
ELF	7efc0000-7efcd000	Deferred        libnss_files.so.2
ELF	7efcd000-7efe7000	Deferred        libnsl.so.1
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	ae6c2000-ae720000	Deferred        dbghelp<elf>
  \-PE	ae6d0000-ae720000	\               dbghelp
ELF	ae720000-ae758000	Deferred        winhttp<elf>
  \-PE	ae730000-ae758000	\               winhttp
ELF	ae758000-ae810000	Deferred        crypt32<elf>
  \-PE	ae760000-ae810000	\               crypt32
ELF	ae810000-ae83b000	Deferred        msvcr80<elf>
  \-PE	ae820000-ae83b000	\               msvcr80
ELF	aeafb000-aeb19000	Deferred        libgcc_s.so.1
ELF	af91d000-af9aa000	Deferred        msvcrt<elf>
  \-PE	af930000-af9aa000	\               msvcrt
ELF	afbaf000-afbd1000	Deferred        iphlpapi<elf>
  \-PE	afbc0000-afbd1000	\               iphlpapi
ELF	afbd1000-afc00000	Deferred        msvcr90<elf>
  \-PE	afbe0000-afc00000	\               msvcr90
ELF	b471c000-b4894000	Deferred        libvorbisenc.so.2
ELF	b4894000-b48e2000	Deferred        libflac.so.8
ELF	b48e2000-b4954000	Deferred        libsndfile.so.1
ELF	b4954000-b4a46000	Deferred        libasound.so.2
ELF	b4a46000-b4b38000	Deferred        oleaut32<elf>
  \-PE	b4a60000-b4b38000	\               oleaut32
ELF	b4d54000-b4db9000	Deferred        libpulsecommon-1.1.so
ELF	b4eba000-b4ece000	Deferred        psapi<elf>
  \-PE	b4ec0000-b4ece000	\               psapi
ELF	b4ece000-b4ed6000	Deferred        libogg.so.0
ELF	b4ed6000-b4f01000	Deferred        libvorbis.so.0
ELF	b4f01000-b4f08000	Deferred        libasyncns.so.0
ELF	b4f08000-b4f56000	Deferred        libpulse.so.0
ELF	b4f56000-b4f82000	Deferred        winealsa<elf>
  \-PE	b4f60000-b4f82000	\               winealsa
ELF	b5087000-b50aa000	Deferred        mmdevapi<elf>
  \-PE	b5090000-b50aa000	\               mmdevapi
ELF	b540b000-b5412000	Deferred        libasound_module_pcm_pulse.so
ELF	b541c000-b5423000	Deferred        libnss_dns.so.2
ELF	b5423000-b5427000	Deferred        libnss_mdns4_minimal.so.2
ELF	b5427000-b5431000	Deferred        libwrap.so.0
ELF	b5431000-b5439000	Deferred        libjson.so.0
ELF	b5442000-b5448000	Deferred        libuuid.so.1
ELF	b544a000-b5451000	Deferred        libxdmcp.so.6
ELF	b5451000-b5455000	Deferred        libxau.so.6
ELF	b5455000-b5476000	Deferred        libxcb.so.1
ELF	b5476000-b70ac000	Deferred        libnvidia-glcore.so.295.40
ELF	b70ac000-b70b0000	Deferred        libnvidia-tls.so.295.40
ELF	b70b1000-b70dd000	Deferred        libm.so.6
ELF	b70dd000-b70ef000	Deferred        libxext.so.6
ELF	b70ef000-b7223000	Deferred        libx11.so.6
ELF	b7223000-b7229000	Deferred        libxv.so.1
ELF	b7229000-b7286000	Deferred        libturbojpeg.so
ELF	b7287000-b728c000	Deferred        libdl.so.2
ELF	b728c000-b7364000	Deferred        libgl.so.1
ELF	b7364000-b7509000	Dwarf           libc.so.6
ELF	b7509000-b7524000	Dwarf           libpthread.so.0
ELF	b7527000-b7533000	Deferred        libnss_nis.so.2
ELF	b7533000-b753c000	Deferred        libnss_compat.so.2
ELF	b753d000-b767f000	Dwarf           libwine.so.1
ELF	b7680000-b771d000	Deferred        librrfaker.so
ELF	b771d000-b7720000	Deferred        libdlfaker.so
ELF	b7722000-b7744000	Deferred        ld-linux.so.2
ELF	b7744000-b7745000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\system32\wow.exe
	0000004e    0
	00000027    0
	0000004d    0
	0000002a    0
	00000067    0
	0000004c    0
	0000004b    0
	0000004a    0
	00000049    0
	00000048    0
	0000000d    0
	0000000b    0
	00000047    0
	00000046    0
	00000045    0
	00000044    0
	00000043    0
	00000042    0
	00000041    0
	00000040    0
	0000003f    0
	00000038    1
	00000037    1
	00000035    0
	00000034    0
	00000033    0
	00000032    2
	00000031   15
	00000030    0
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
	00000029    0
	00000028    0
	00000025    0 <==
	00000009    0
0000000e services.exe
	00000020    0
	0000001f    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001d    0
	0000001a    0
	00000014    0
	00000013    0
0000001b plugplay.exe
	00000021    0
	0000001e    0
	0000001c    0
00000022 explorer.exe
	00000023    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-24-generic-pae


Someone might get something out of this

Posting this at wine hq aswell thru their bugreport

and some prints

[http://oi50.tinypic.com/2pt5g89.jpg](http://oi50.tinypic.com/2pt5g89.jpg)

The program wow.exe has encountered a critical error and has to be terminated
We apologize for any inconvienence

This could have been due to a bug in wine or a bug in the program
More Details.

Thats what the box says

[http://oi47.tinypic.com/2nal5j9.jpg](http://oi47.tinypic.com/2nal5j9.jpg)

My theory is still based on something with the background downloader due to the green circle showing that the game is downloading

Altho I copied my entire folder into the system 32 some files might not have followed and some files might have been damaged to the point of where they had to be re downloaded

Waiting on blizzard and wine hq with other point of views or explinations

And no I dont know alot about computers



:D

---

### Post by Smakone on 2012-05-12
[http://bugs.winehq.org/show_bug.cgi?id=30662](http://bugs.winehq.org/show_bug.cgi?id=30662)

updated on winehq

continueing testing with zoneing and big cities with crowded areas

---

### Post by Smakone on 2012-05-12
Currently in orgrimmar without crashes or lags

[IMG]http://oi45.tinypic.com/axi5as.jpg[/IMG]

Altho this might not be crowded enough but the computer and wine handled the flight and the new continent without crashing

This game is playable on ubuntu and I would rate it 10/10 for being "a very enchanting game"

Regards

Pad Paddington

The

[IMG]http://shinzikatoh.shop2.multilingualcart.com/ori/50054/goods_img/goods_648_1.jpg[/IMG]




Bonus: [http://www.youtube.com/watch?v=fWucPckXbIw](http://www.youtube.com/watch?v=fWucPckXbIw)


Spacedoor out
//

spacedoor.tumblr.com

---

### Post by Smakone on 2012-05-12
Installed steam exactly the same way to play CoD MW3 and it also works as good as wow

Proof: [http://oi45.tinypic.com/21dlz9.jpg](http://oi45.tinypic.com/21dlz9.jpg)

Peace

---

### Post by Smakone on 2012-05-12
Glad to announce that the launcher is fixed

Problem was when you copy or move big files in whine the little "roller" on wine explorer works as a loading bar that is turned in this direction | instead of - so when it freezes just wait for wine to load until crash when it crashes all the files are moved

Here's the launcher

[IMG]http://oi48.tinypic.com/2mcycns.jpg[/IMG]


One might claim that the game should be working flawlessy now but you never know with windows based or windows cloned software

Resolved

---

### Post by Smakone on 2012-05-13
Hello Joakim,

Thank you for letting me know how you got it to work on your system, I will infact try your steps myself too when I get home to see if it helps on mine.

I have sent you a little gift for you hard work and I hope it puts a smile on your face, for a few seconds.

I look forward to your next ticket and being popsted on the foums again :) My 1st ever posting on a forum ^^

Kind regards,

Game Master Gourgetion - a fellow ubuntu user!
Game Master Team
For quick help on topics
[http://www.youtube.com/blizzardtutorial](http://www.youtube.com/blizzardtutorial)




Gift waiting to be recieved guessing some sort of pet



Sucess.... recieved.... cake


[IMG]http://oi49.tinypic.com/e6vz84.jpg[/IMG]

[IMG]http://oi48.tinypic.com/1jninq.jpg[/IMG]



If someone wants to add this to howto its more then welcome

I'm gunna play!!!

---

### Post by Smakone on 2012-05-13
Update

Enjoyed my delicious cake from blizzard

The Game is working perfectly thru wine

[IMG]https://lh6.googleusercontent.com/-_HUQa4m1C-g/T69tvckNXtI/AAAAAAAAAQ4/zfM6yaH6cgM/w497-h373/DSC_0047.JPG[/IMG]


And found this on the way to the gym

Pad AB

Enjoy

[IMG]https://lh6.googleusercontent.com/-JAg3MONwd80/T6-XVPz-ZKI/AAAAAAAAARU/GS0akPg5PGY/w497-h373/DSC_0048.JPG[/IMG]

---

### Post by Fantasies on 2012-05-16
Hey!
I have read the thread and have a similar problem, I'm totally new to ubuntu btw :p
When i start the launcher it begins to download the updated tool, but it never finishes, just stops. Either halfway, or right away after its starts and then dissapears. If it comes halfway it stands there forever and doesn't go further.

Tried also to lauch wow.exe(by using wine) but it crashed right away, didn't come to the inlogging screen. Maybe because i haven't updated it at all since it never came that far :p 

hoping that somebody can give me some help to fix it :)

---

### Post by Smakone on 2012-05-16
Did you check this thread

[http://ubuntuforums.org/showthread.php?t=1963204](http://ubuntuforums.org/showthread.php?t=1963204)

there's a fix to the launcher tool issue

---

### Post by Fantasies on 2012-05-16
No, i hadn't found that thread. Tried it and its downloading now! Thank you so much :D

---

