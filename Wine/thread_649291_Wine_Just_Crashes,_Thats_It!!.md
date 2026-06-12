---
title: "Wine Just Crashes, Thats It!!"
date: 2007-12-24
forum: Wine
---

### Post by maniheer on 2007-12-24
Hi, my first post:

I installed WINE and it went perfectly (from Synaptic) but whenever I click the application launcher, whether notepad they give at the beginning or the configuration thing, my whole computer will just freeze, I have to press the reset button for anything to work.

Specs
704MB RAM
64MB Shared RAM for VIA K4M800 Graphics Card (Onboard)
Intel P4 Processor 2.66 Gigahertz
VIA P4M800 PRO Motherboard
Ubuntu 7.10 (Gutsy Gibbon)

P.S. I am new to Linux (Installed this morning)


THANKS

---

### Post by Faud on 2007-12-24
Hello, maybe someone else can give me some clarity here on what is going on. You installed WINE from the repos and then you are opening notepad ? Whenever I have setup wine I have never had anything in notepad open. I simply open a terminal and type "winecfg" and a screen comes up with tabs at the top for graphics, audio etc. Is that what you mean is crashing ?

---

### Post by Giradman on 2007-12-24
Well, I'm using Ubuntu 7.10 and have not installed WINE - just wondering why after a GUSTY installation that you needed WINE immediately w/o exploring the many software programs installed w/ the Ubuntu package - e.g. GEDIT is basically a Notepad replacement.  Mainly for my own information, I guess - new to Ubuntu myself (just 2 months now & learning more each day!) - good luck w/ resolving this issue - :(

---

### Post by hikaricore on 2007-12-24
**The problem at hand is not that the OP is trying to use Notepad instead of Gedit.  The problem is that no matter what program they attempt to run via WINE, even Notepad, crashes their system entirely.  This issue has been seen before and is often related to video drivers, however I don't have any further input to offer as to a solution.  :/**

---

### Post by maniheer on 2007-12-25
Hi,

Sorry I didn't explain it properly but what hikaricore said is what I meant, I don't want Notepad, it's useless, I just can't start anything even related to wine.

---

### Post by cogadh on 2007-12-25
Do a complet uninstall/purge/reinstall of Wine, including deleting your .wine directory:
```
sudo apt-get remove --purge wine
rm -rf ~/.wine
sudo apt-get install wine
winecfg
```
If the problem still occurs, then as hikari said, it is likely some hardware conflict. However, I would suspect sound before video, there have been a number of instances where the lock/crash goes away after disabling the sound hardware.

---

