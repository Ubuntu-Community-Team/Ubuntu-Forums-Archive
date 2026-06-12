---
title: "ATI cards + wine"
date: 2008-07-19
forum: Wine
---

### Post by Akingboy on 2008-07-19
Has anyone gotten one of these work with ATI card yet?:

1. Diablo 2 higher fps than 10 with Direct3D mode.
2. Steam games freezing after few minutes of play. (Half Life 1 + mods) (Haven't tested source games)
3. Warcraft 3 FT has corrupted main menu. Some textures missing in the background animation thing that plays there.
[http://www.uploadhouse.com/viewfile.php?id=2234544&PHPSESSID=ea2196a5b6a62dde9207d010503e974a](http://www.uploadhouse.com/viewfile.php?id=2234544&PHPSESSID=ea2196a5b6a62dde9207d010503e974a)
There is a picture of it

I have:
ATI HD3850
Wine 1.1.1 and I use ALSA

And yes I have tried reinstalls, updates. I haven't tried any patches for wine to fix these though. Because haven't found em.

---

### Post by OpposingForce on 2008-07-19
Counter Strike 1.6 also completely freezes my computer after a few minutes of play, this doesn't happen on my other computer which has an Nvidia GeForce 6800.  Also in morrowind, I have all kinds of graphical glitches like water not rendering.  I have a Radeon X1200.

---

### Post by daniel7860 on 2008-07-19
same problem here, with CS 1.6 freezing.
Hasn't happened to me before.
I tried using different Drivers like OSS. 
I am using ATI Mobility Radeon X300.

---

### Post by Akingboy on 2008-07-20
bump

---

### Post by dmn_clown on 2008-07-20
> **Akingboy said:**
> 
3. Warcraft 3 FT has corrupted main menu. Some textures missing in the background animation thing that plays there.
[http://www.uploadhouse.com/viewfile.php?id=2234544&PHPSESSID=ea2196a5b6a62dde9207d010503e974a](http://www.uploadhouse.com/viewfile.php?id=2234544&PHPSESSID=ea2196a5b6a62dde9207d010503e974a)
There is a picture of it

I have:
ATI HD3850
Wine 1.1.1 and I use ALSA

And yes I have tried reinstalls, updates. I haven't tried any patches for wine to fix these though. Because haven't found em.

That looks more like a driver issue than a wine issue.  Are you using the latest drivers from AMD (they own ATi now)?

---

### Post by HokeyFry on 2008-07-20
I was sick of ATI to begin with, in both Windows and Linux. I would suggest using an NVidia card if at all possible. I do know that the latest ATI driver is a piece of crap so that might be the issue as well. You may want to wait for the next driver to be released (but who knows when that will be?)

---

### Post by poofyhairguy on 2008-07-20
It is a driver issue. Make sure you try everything here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

---

### Post by ebichu on 2008-07-21
> **HokeyFry said:**
> I was sick of ATI to begin with, in both Windows and Linux. I would suggest using an NVidia card if at all possible. I do know that the latest ATI driver is a piece of crap so that might be the issue as well. You may want to wait for the next driver to be released (but who knows when that will be?)drivers are released monthly, and getting better by every release.
i have source games running just fine with decent fps, also world of warcraft and others.

OP: have you tried opensource drivers? i remember getting cs 1.6 working with them, on my old computer, with r9200.

---

### Post by Akingboy on 2008-07-21
Yeah maybe source works. And I have wow working fine too.
But cs 1.6 and other hl1 mods keep freezing.

---

### Post by The Tronyx on 2008-07-21
> **Akingboy said:**
> Yeah maybe source works. And I have wow working fine too.
But cs 1.6 and other hl1 mods keep freezing.

Have you tried installing the newest ATI driver?  I know they put out a new one on the 18th but I haven't had enough time as of late to install it and try it out.

---

### Post by Akingboy on 2008-07-21
Haven't tried newest. I just installed the ones from the menu in the system->moderation->driver thing.

I think I could test those new ones if I can just download them without easy-use UI's :P

EDIT: There isn't HD 3xxx series there supported??? :(

---

### Post by Akingboy on 2008-07-21
Well got some new drivers installed now.

I got new problem. When I start a game the screen is really "streched" or strangely corrupted. Hard to see where menu buttons are. When I can quit the game the desktop is like the game too.

Anyone know the command of wine (used in terminal) to open the uninstall window? I don't have those shortcuts in my start menu for some reason =/ After I installed patched version it didn't appear there.
I will try to uninstall steam.

---

### Post by andlinux on 2008-07-21
> **Akingboy said:**
> Well got some new drivers installed now.

I got new problem. When I start a game the screen is really "streched" or strangely corrupted. Hard to see where menu buttons are. When I can quit the game the desktop is like the game too.

Anyone know the command of wine (used in terminal) to open the uninstall window? I don't have those shortcuts in my start menu for some reason =/ After I installed patched version it didn't appear there.
I will try to uninstall steam.
I have the same problem. I installed Dungeon Keeper 2 and when I start it with wine I get a weird desktop, all big blocks. I'm using an old ati card, the 9700 that's in my laptop.

---

### Post by Akingboy on 2008-07-22
Bump

---

### Post by Melcar on 2008-07-22
I can't even install games.  As soon as I try to open something, the whole screen becomes corrupted, making everything hard to see.

---

### Post by Akingboy on 2008-07-23
bump

---

### Post by Akingboy on 2008-07-24
bump

---

### Post by Spydr4590 on 2008-07-24
Okay, this is why I bought a Nvidia card. However I still use ATI cards in my other systems.

Texture corruption while using wine is a common issue introduced in ATI 8.6 Drivers and is still prevalent in ATI 8.7 drivers. Please visit [http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19) for a wider range of support. ATI Developers post here.

Also please make sure to install the drivers correctly using this wiki. [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by Vakman on 2008-07-24
I have the screen stretch problem with some of the drivers or I get an unrecoverable graphics error with others.

---

### Post by Akingboy on 2008-07-28
bump

---

### Post by Spydr4590 on 2008-07-28
> **Akingboy said:**
> bump

Read my post.

---

### Post by Akingboy on 2008-07-31
I read that. And posted in the ATI forums but no one answered there.
Does anyone know fix to this? Or do we have to wait for better drivers?

---

### Post by Vakman on 2008-07-31
Akingboy, I seriously wish I knew. I know that I will never buy an ATI card again. But now I am stuck with one. Hopefully they fix this soon...

---

### Post by SarcasmMonster on 2008-07-31
Playing TF2 with fglrx crashes the entire system after about 10 minutes of play. If I only knew about ATI's awfulness before I got my computer. Can't wait till the open source driver's support 3d for my x1300.

---

### Post by Vakman on 2008-08-01
> **SarcasmMonster said:**
>  Can't wait till the open source driver's support 3d for my x1300.
I myself have a Radeon Xpress 1200. And any idea about when it will be out for your card?

---

### Post by Akingboy on 2008-08-20
Bump.
Any news?

---

### Post by Melcar on 2008-08-20
If you want to use Wine, revert to the 8.5 drivers.  The newer ones (even the recent 8.8 ) do not work with Wine.

---

