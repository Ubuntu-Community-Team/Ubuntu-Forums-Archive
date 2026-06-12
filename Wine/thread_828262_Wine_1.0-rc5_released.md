---
title: "Wine 1.0-rc5 released"
date: 2008-06-13
forum: Wine
---

### Post by cogadh on 2008-06-13
[http://www.winehq.org/?announce=1.0-rc5](http://www.winehq.org/?announce=1.0-rc5)
Lot's of fixes, also, all pending 1.0 bugs that have not been deferred to 1.0.1 or 1.2.0 have been fixed. Nothing but regression testing left to do before 1.0. List of the deferred bugs:

1.0 bugs deferred to 1.0.1 since May 27th:[list]
    [*] 11584 Multiple games crash with stack overflow error
    [*] 12307 firefox 3 crash on some web pages [dogfood]
    [*] 13143 XIM patch prevents wine-0.9.60 and later to run
    [*] 13740 winebrowser gets wrong URL, problem with unicode[/list] 

1.0 bugs deferred to 1.2.0 since May 27th:[list]
    [*] 124 Review of Wine Server Protocol
    [*] 3023 Orcad - "Place Part" never tries to put down a part
    [*] 5163 Office XP 2002 crashes on installation
    [*] 5402 Trying to run PhotoStitch 3.1
    [*] 5535 Planescape:Torment doesn't work
    [*] 6095 MOTD in counter-strike 1.6 and counter-strike source does not render
    [*] 6519 Wine blacks out rotated font bitmap
    [*] 7404 ShowWindow(SW_MINIMIZE) should not generate a WM_PAINT message
    [*] 8439 Visual Studio .NET (7) install fails
    [*] 8783 USB serial ports do not work
    [*] 9771 Steam Friends doesn't work (fails to render correctly or refresh)
    [*] 9787 Warcraft3 Battle.net Doesn't work (Needs AcceptEx)
    [*] 9916 "make test" usually fails
    [*] 10147 Word Viewer 2003 - Tab behavior differs from Windows
    [*] 10288 wine_gecko download hangs sometimes
    [*] 11281 CJK input many issues
    [*] 12005 Regression in pressure sensitivity with wizardpen tablet driver and Photoshop 7
    [*] 12074 The conformance tests fail on Windows
    [*] 12730 gdi32: some tests fail when X is run in 16 bit mode, but not 32 bit
    [*] 13071 Flashplayer crashes in a quartz bug[/list]

---

### Post by kevin11951 on 2008-06-13
cant wait for it to hit the ubuntu wine repos

---

### Post by insane_alien on 2008-06-13
this is supposedly the last one before wine 1.0! its been fun watching wine improve so fast these last few years, i hope such rapid development continues post 1.0.

---

### Post by kevin11951 on 2008-06-13
USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1! USB Support For Post 1!

---

### Post by cogadh on 2008-06-13
Um, wha? :confused:

---

### Post by Kronie on 2008-06-13
's there any way to update right now, or do we have to wait till it hits repos?
--------------
nvm its already there 0_o
_______________
oh noes!!! T_T 
> 1.0 bugs deferred to 1.2.0 since May 27th:
9771 Steam Friends doesn't work (fails to render correctly or refresh)
steam is pretty much the only reason i have wine, and it doesnt work the way it should T_T

---

### Post by kevin11951 on 2008-06-13
> **cogadh said:**
> Um, wha? :confused:

i wish they would add usb support to wine after 1.0 comes out!

---

### Post by cogadh on 2008-06-13
> **kevin11951 said:**
> i wish they would add usb support to wine after 1.0 comes out!
Wine does have USB support (I use my USB gamepad all the time), it just doesn't have support for USB serial devices, like ROM chip programming devices. That functionality has been deferred to 1.2.0 for now.

> **Kronie said:**
> 's there any way to update right now, or do we have to wait till it hits repos?
--------------
nvm its already there 0_o
_______________
oh noes!!! T_T 

steam is pretty much the only reason i have wine, and it doesnt work the way it should T_T
Do you actually use the Steam Friends functions? Other than that, the rest of Steam does work fine.

---

### Post by kevin11951 on 2008-06-14
> **cogadh said:**
> Wine does have USB support (I use my USB gamepad all the time), it just doesn't have support for USB serial devices, like ROM chip programming devices. That functionality has been deferred to 1.2.0 for now.

well, like itunes and ipod... no worky. (i need to restore on of my old ipods)

---

### Post by cogadh on 2008-06-14
That's not a USB problem, that's an iTunes problem. It requires a service to be running for iPod connection to work (iPodService.exe). I suppose there could be a way to launch that service in the wineserver first, then run iTunes, but since I don't own an iPod or use iTunes, I can't test it myself.

---

### Post by Kronie on 2008-06-14
yea i actually (used to) use steam friends as my primary messenger, so.. i guess i just have to wait T_T any ideas when 1.4 be coming out?

---

### Post by cogadh on 2008-06-14
It's taken 15 years for 1.0 to come out and while I wouldn't expect another 15 to pass before 1.4 is released, it will probably be quite a while before we see it. The Wine devs haven't announced any kind of definitive release schedule, as far as I know.

---

### Post by RESID3NT on 2008-06-14
> **cogadh said:**
> 
Do you actually use the Steam Friends functions? Other than that, the rest of Steam does work fine.

Other than crashing all the time when I try to download and install Counter Strike through steam. Downloading CSS works. Performace could be better

---

### Post by Kronie on 2008-06-14
wow, typo here..i meant to say 1.2, but i think that doesnt make any difference.. guess gotta pack the bags and move back to windows T_T i mean, the steam friends issue existed ever since steam came out.. and there are a lot of people who are looking for cure for it. wine crew should have fixed it by 1.0 T_T 

offtop: i dont think it would take THAT long for them to update wine.. it took them 15 years to make a software from scratch! now they have the software ready. all they have to do is fix some stuff in it.. also, windows 7(which will be coming out in about 2010) will use vista kernel, so as soon as they make vista-only games/software to work, theyll be loaded up till 2014 :P

---

### Post by thefishki345 on 2008-06-14
I have a question, what is wine 1.0s real aim? Is it to make every platinum application work in wine? or is it to get those now 4 programs (word,powerpoint etc) working flawlessly?

---

### Post by kevin11951 on 2008-06-14
> **thefishki345 said:**
> I have a question, what is wine 1.0s real aim? Is it to make every platinum application work in wine? or is it to get those now 4 programs (word,powerpoint etc) working flawlessly?

the latter

---

### Post by Sleaka J on 2008-06-14
I think the Wine devs would be surprised at how many Steam users actually use (and want to use under Linux) the friends chat system.

---

### Post by YokoZar on 2008-06-14
> **thefishki345 said:**
> I have a question, what is wine 1.0s real aim? Is it to make every platinum application work in wine? or is it to get those now 4 programs (word,powerpoint etc) working flawlessly?
The point of a stable release (as opposed to just doing continual beta releases) is to fix all known regressions.  The Wine team itself can only personally test a few applications (those four), however fixing any regression bug that users find was also a major part of the release.  That's why Wine had things like the Platinum Regression Hunt.

Additionally, when the *next* stable release of Wine comes out, users will have some assurance that there will be no regressions between them.


The question, then, is how often to do this freezing and regression-hunting.  As of now there is no set plan, though as an Ubuntu developer I would prefer a time-based release system for Wine so each new Ubuntu release could have a new stable Wine.  For 1.0, Wine decided on what is essentially an arbitrary date - Wine's 15th birthday.  For 1.2, we're still deciding whether to pick another arbitrary date, to start a consistent cycle, or to just wait until we have "enough" new features and do it ad-hoc.

---

