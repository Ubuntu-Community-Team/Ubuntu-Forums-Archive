---
title: "Wine + ati = problems. Whose fault is it?"
date: 2008-08-03
forum: Wine
---

### Post by cristo-father on 2008-08-03
Hi.
I have been having terrible performances when i mix these 2.
What i want to know is...who's fault is it? wine's? ati's? or both?.
Will this ever change? Should i just trade mine for an nvidia? 
Thanks.

---

### Post by Akingboy on 2008-08-04
First of all. Its not that damn simple that ATI is bad.
I have myself ATI HD 3850 and I have 100-400 fps in wow.
Constant 125 locked fps in enemy territory.
Warcraft 3 runs also with good fps no problem.

You have installed/configured something wrong or haven't at all.
The fault? Its yours!
Try to be more specific...

---

### Post by aoanla on 2008-08-04
> **Akingboy said:**
> First of all. Its not that damn simple that ATI is bad.
I have myself ATI HD 3850 and I have 100-400 fps in wow.
Constant 125 locked fps in enemy territory.
Warcraft 3 runs also with good fps no problem.

You have installed/configured something wrong or haven't at all.
The fault? Its yours!
Try to be more specific...

Sigh.
The thread starter almost certainly has problems in Source-engine games.
It is well known that ATI's current drivers interact badly with Source-engine games under Wine - the Wine devs pretty much insist that this is an issue with the ATI drivers, and not with their code. (Although, of course, it might be an issue with the Source engine doing something odd...)

---

### Post by Melcar on 2008-08-04
> **aoanla said:**
> Sigh.
The thread starter almost certainly has problems in Source-engine games.
It is well known that ATI's current drivers interact badly with Source-engine games under Wine - the Wine devs pretty much insist that this is an issue with the ATI drivers, and not with their code. (Although, of course, it might be an issue with the Source engine doing something odd...)


It's funny that nearly every single game developer blames something else, like drivers.  I have grown to distrust game developers after a few certain games "magically" started working under the ATI drivers after they released a major update, despite the drivers not having changed that much in terms of openGL support.
In the case of Wine, fglrx used to work "well", with the last couple of releases being problematic.  The driver itself hasn't changed much, with only Wine doing major updates.  Still, if you rollback your driver to 8.5 or earlier, compatibility with Wine seems much better.  I think the fault lies with both parties; fglrx is known to have "incomplete" openGL (holes in their code), while Wine is known to break stuff with nearly every major upgrade.

---

### Post by aoanla on 2008-08-04
True, but Wine hasn't broken anything with nVidia or Intel cards in the same updates. This suggests that their "improvements" leverage bits of OpenGL which the ATI driver is particularly bad at - and that the newer ATI drivers are *worse* at those bits than the older ones.

---

