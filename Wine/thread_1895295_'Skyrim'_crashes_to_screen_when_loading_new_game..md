---
title: "'Skyrim' crashes to screen when loading new game."
date: 2011-12-14
forum: Wine
---

### Post by Chris . on 2011-12-14
Hey guys ! :)
I am not sure where to post this in this forum :D
So , my problem is with a game which is The Elder Scrolls V Skyrim.
And here's my problem and i hope that Ubuntu user have a fix.

So when i open Skyrim, i click 'new game', then klick 'yes'
And it starts loading.
The text on the bottom right, fog coming from down and a big dragon statue in the middle,left.
And it slowly zooms out and in...
And then, after some loading, it just crashed to my desktop.

See, my os is Linux Ubuntu(11.10), but Skyrim does work on Linux. A lot  of people have this problem that i have, but i haven't found the  solution.

Do i need to put some Updates, patches or what ? If so, then please give me the link also.

Specs:

Processor: AMD Athlon II X2 P340
Video card: Ati Mobility Radeon HD 4250
Hard disk: 320 GB HDD
RAM: 3GB DDR3 Memory

So please give me solutions how to solve this .
I have also read that i have to change the sound to 44.1Hz or something  like that, but i can't find a place to change that in Linux.
There is some sound place but there are dB's or whatever.

Thanks ahead ! [IMG]http://static.zenimax.com/forums/public/style_emoticons/default/smile.gif[/IMG]

---

### Post by Dlambert on 2011-12-14
DO you have your ATI drivers installed? What detail are you trying to run skyrim on? On a laptop of that magnitude I would stick to low.

---

### Post by Dlambert on 2011-12-14
Straight from WINE's APPDB :


> **Audio**

If sound doesn’t work, installing DirectX10 (from directory of game) helps atleast here.
No other dll overrides present, *though* I do have maybe tons of those dlls at system32 or wherever they are installed to.
Pulseaudio is reported to need to run the in windows xp mode, changeable with winecfg or winetricks.
Some people are saying installing xact is required to get audio working. I haven’t confirmed this one myself.
**Crashes, texture bugs etc..**

These  happens for Windows users too, so quite likely bugs in actual game.  Some may not, but it’s mostly crashes about out of memory or such  specific Wine issues, maybe. Or maybe the game just leaks. Anyway, until  few patches (now the version is 1.1.22 or similar) are out, correctly  deducing Wine bugs is a bit hard.
[IMG]http://appdb.winehq.org/images/blank.gif[/IMG]
[IMG]http://appdb.winehq.org/images/blank.gif[/IMG] HOWTORunning game for 1.3.32: 
 winetricks d3dx9_42 vcrun2008 xact 
 Remove Intro video in "Skyrim/Data/Video" 
 If using pulseaudio set Win7 mode. 
 
 Another way:
 winetricks vcrun2008
 installing DirectX10/DXSETUP.exe

---

### Post by Chris . on 2011-12-15
I should have my ATI drivers installed i think, maybe not the right ones?
If you'd be so kind and give me the link to the right one :)


When i click 'default' then it detects on what settings i should run the game on.
Low - Medium - High - Ultra.
For me it says High settings, and changes them to high.

---

### Post by Dlambert on 2011-12-15
Just try low for debugging purposes. And to use "Ubuntu's" latest hit additional drivers in the unity dash and activate the driver (if not already done so)

---

