---
title: "Call of Duty 2 - 1.3 punkbuster"
date: 2007-07-25
forum: Wine
---

### Post by feest on 2007-07-25
I've managed to run call of duty 2 1.3 patch with wine... But now i'm getting kicked from server due to a punkbuster error.... Now on wine appdb they said they could fix it with an alternative punkbuster inatall 

> 
What works

Multiplayer works good.

**Punkbuster works by adding the official linux punkbuster files for linux ([http://www.evenbalance.com/](http://www.evenbalance.com/)).**

Singleplayer works with no-cd crack.

Patching to version 1.3 works but needs another no-cd crack to let singleplayer working.


What does not

The end of the installer (not important).

The background images of the installer aren't displayed.


What was not tested
I tested everything and everything works except the two things in the installation process.


Additional Comments


Owyeah, call me a complete noob but the even balance thing asked me to select the install directory... What directory is it? I've use /home/sven/.wine/drive_c/activision/call of duty 2/ is this the right one?

---

### Post by t3ch on 2009-03-30
use default directory:
c:\\Program Files\Activision\Call of Duty 2 ..

I have installed game but it give error almost on end of installation..

The game installs even thoung that error appeared. Only registers missing if you check **wine regedit**: 
**HKEY_LOCAL_MACHINE->Software->Activision->Call of Duty 2**

So I have export register from installed game in win xp and imported in linux:
**wine regedit cod2-registers.reg**

When you make that then you can install patch 1.3. In my case was that the only way to install patch 1.3...

-------------------------------------------------------------------------

But now I have problems with punkbuster. It kick me out if I install linux pb or win pb, i have tested that the win pb was installed and then i have rewrite it with linux pb... and THAT CRAP kick me out in all ways... :)

Have anyone any clue what is wrong?
pb errors: Unknown Windows API Function..
           131131,
           131124 ... etc.. :)

I have tested that on wine version 1.17 and 1.18

SUMMARY:
I still have problems with PUNKBUSTER :) jej

P.S.:
Single player work perfect! :frown:

---

### Post by asdfoo on 2009-03-30
> **t3ch said:**
> 

Have anyone any clue what is wrong?
pb errors: Unknown Windows API Function..
           131131,
           131124 ... etc.. :)

I have tested that on wine version 1.17 and 1.18

SUMMARY:
I still have problems with PUNKBUSTER :) jej


PB will not work because it compares internal Windows code against known good values and will abort if it does not match, eg you are running Wine.

PB will only work on Windows unless you use the same hacks that cheaters use to trick PB into working while using mods that give unfair advantages.

---

