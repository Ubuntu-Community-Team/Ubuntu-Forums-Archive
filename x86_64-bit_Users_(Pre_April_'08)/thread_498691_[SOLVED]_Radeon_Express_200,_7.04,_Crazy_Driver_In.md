---
title: "[SOLVED] Radeon Express 200, 7.04, Crazy Driver Install"
date: 2007-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-11
I have the below listed system.  First I had 32bit U installed - ATI Drivers worked fair.  Then I decided to do a clean install of 64bit U.

All was good except wireless (now fixed), and Video Driver.  I downloaded and tried to install as per the ATI website and it was something like this    sh ./driverlocation/name.run

This didn't work at all.  The command line returned no results.  I tried many things but heres what got it moving.

sudo -i drivername.run

I've never read anywhere that I should do this but it seemd to work in that it launched the installer and it completed without any errors reported.  I've done this on my other machine (different specs/card) it seems to work very well for the most part.

I installed OpenArena and when I launch the game the screen goes black, then the desktop resets and I have to login again.  On my other machine with the x800 card, the game plays awesomly.

How do I clear out any bad drivers on the machine with the xpress 200 card, and what is the PROPER/WORKING method of installing these drivers?
[B]
MSI-Motherboard (ATI Chipset)
Athlon 64 3200+
512MB Memory
ATI xpress 200 (128mb shared memory)
Segate 100GB IDE[/B]

---

### Post by Kilz on 2007-07-11
Here are a few links that may help you.

[Feisty page at the unofficial ATI Linux Driver wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

[the ATI Binary install page of the Ubuntu wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by crjackson on 2007-07-11
> **Kilz said:**
> Here are a few links that may help you.

[Feisty page at the unofficial ATI Linux Driver wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

[the ATI Binary install page of the Ubuntu wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Thanks kilz - I looked them over.  I can do the 1st one but it doesn't give me 3D as it should.  The second one is WAY to advanced for me at this point.

Is it not possible for ATI to make click/install drivers, or is simply just that they don't want too.  This really shouldn't be so damnd complicated...:mad:

---

### Post by crjackson on 2007-07-11
Is there some particular reason that the command:

**sh ./ati-driver-installer-8.38.6.run** that is provided on the ATI website won't work on ubuntu?

---

### Post by crjackson on 2007-07-13
> **crjackson said:**
> Is there some particular reason that the command:

**sh ./ati-driver-installer-8.38.6.run** that is provided on the ATI website won't work on ubuntu?

ANYBODY?

---

### Post by Kilz on 2007-07-13
> **crjackson said:**
> Is there some particular reason that the command:

**sh ./ati-driver-installer-8.38.6.run** that is provided on the ATI website won't work on ubuntu?

the driver installer isnt setup to automaticly create Ubuntu debs. IMHO its because of the very frequent Ubuntu releases (something nice for us) that would have the redesigning the interface constantly. It will make deb's, but its all through the terminal. I have a radon express 200. Last time I tried Feisty I was able to get acceleration with the Ubuntu drivers and never used the Unofficial site. But it was the one I used for Dapper.
Are you using method 2?

---

### Post by crjackson on 2007-07-13
> **Kilz said:**
> the driver installer isnt setup to automaticly create Ubuntu debs. IMHO its because of the very frequent Ubuntu releases (something nice for us) that would have the redesigning the interface constantly. It will make deb's, but its all through the terminal. I have a radon express 200. Last time I tried Feisty I was able to get acceleration with the Ubuntu drivers and never used the Unofficial site. But it was the one I used for Dapper.
Are you using method 2?

I've tried both methods.  I think I'm just plain screwing up method 2 somehow.  I invented a 3rd method just by experimenting and by dumb luck it worked (perfectly when I was running 32bit U), but it under 64bit (on this particular machine) it only works sometimes and only partially I think.  It brings up the ATI installer, it runs without errors, but the CCC doesn't always work after the install.  3D settings are present and seem to function as far as CCC goes, but 3D gaming won't (Open Arena) run.

I think I've screwed it up so much I need to wipe out all parts of the ATI downloaded driver and start from scratch.  I would just wipe the partion and reinstall, but it took me 3 weeks and approx. 100 posts to get the wireless card working.  I'd rather walk through hell than work on making the wireless driver work again.

I just want this damned thing to play Open Arena.

---

### Post by crjackson on 2007-07-17
Okay, so I downloaded some updates as notified by the update manager, re-enabled the restricted driver selection, and now Open Arena works fine...

---

