---
title: "Counter Strike Source Problems (PLEASE HELP!)"
date: 2007-12-17
forum: Wine
---

### Post by chris062689 on 2007-12-17
I'm getting very aggravated with WINE + Half Life 2 mods.
I am running 7.10 x64.  Using WINE.

Wine 0.9.51 - I can launch Counter Strike Source; but when I join a game, hl2.exe freezes right when it enters the game (at the message of the day)

Wine 0.9.50 (and below) - It works, but I randomly get freezes after entering the games.

I can't even launch anything else other than Counter Strike Source (HL2, HL2 Ep 1, Portal, HL1:S, etc.)

I don't know why I'm having all of these problems?  Would it be the x64 architechure that's screwing things up?  I'm using an Nvidia, with the drivers that were downloaded in the Restricted Drivers Manager.  I never had these problems when I was using Ubuntu about a year ago!

Specs : Intel Core 2 Duo @ ~2.4GHz, 2GB Ram Nvidia GeForce Go 7600

---

### Post by lswest on 2007-12-17
yea, my 0.9.50 and below also randomly freezes my CSS in (so far) seemingly random intervals.  Haven't tried it in 0.9.51, however my wine runs Dreamweaver 8 just fine...i have reason to believe it has to do with either sound (try using OSS if you're using ALSA) or with the dxlevel, try reducing it to 70 or so...

---

### Post by chris062689 on 2007-12-17
Whenever I use the OSS drivers, I don't get any sound at all.
How do I set my Direct X level?  I remember it having something to do with creating a Desktop Shortcut, and editing it?

---

### Post by lswest on 2007-12-17
you can append -dxlevel XX (70,80,90=XX [choose one]) to the game in steam (right-click properties and startup commands, where you can add "-console")  you can probably append it to whatever command you use to run CSS too

---

### Post by karth on 2007-12-17
Some people solved this issue by setting wine's compatibility mode to Windows 98 (in winecfg, in the relevant wineprefix). Be sure to do the switch between WinXP  and Win98 compatibility mode AFTER having Steam up and running.
This is my case (also valid for other MP source games like HL2DM)

---

### Post by lswest on 2007-12-18
That fix no longer works, as Steam doesn't support win98 anymore, and so doesn't run.

---

### Post by karth on 2007-12-18
As I said before, launch and get Steam running under XP compat mode, and then launch winecfg and check Win98 compat mode. Then go back into the steam window, double click on CounterStrike Source and then play.... YMMV, though.

> Be sure to do the switch between WinXP and Win98 compatibility mode AFTER having Steam up and running.

---

