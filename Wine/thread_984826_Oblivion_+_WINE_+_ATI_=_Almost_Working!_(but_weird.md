---
title: "Oblivion + WINE + ATI = Almost Working! (but weird glitches)"
date: 2008-11-17
forum: Wine
---

### Post by Progressive on 2008-11-17
Thanks to the 8.10 Catalyst driver being available on Intrepid, I was able to get Oblivion running but with some funky graphical glitches.

I posted my experiences at WineHQ's AppDB [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506&iTestingId=33658")

Since then, I have added new dlls, new texture overhaul mods, new polygon reducers, new INI tweaks, script optimizers, turned off all anti-aliasing, and still I am unable to get the problem resolved.

The problem is very clear in the screenshots below, though the screen has looked even trippier than that on many occasions, and the game is simply unplayable until this is resolved.

As the cell loads longer, the problems sometimes calm down, especially in smaller cells like inside the imperial city. I notice that much of the problems stem from vegetation, especially bushes, but even buildings and rocks can cause it.

A lot of the colorful streaks emanate from the crosshair, and depending on which way I turn, it can get better or worse.

I am guessing this is simply a driver issue, but does anybody have an idea of any other possible workarounds? 

Does anyone know what specifically could be causing this? My hardware is fine, and I am having no troubles in open source games... and indoor cells are working great in Oblivion.

UPDATE: Same story with Catalyst 9.2 and Wine 1.1.17. By the way, I used Oldblivion to downgrade to DirectX 8 throughout all my attempts. I recently used [niftoaster]("http://www.bethsoft.com/bgsforums/index.php?showtopic=890860") to optimize all my meshes, but it didn't fix the problem. Just for fun, I tried to run Timeslip's exe optimizer for Morrowind.exe on Oblivion.exe to no avail. I've been scouring the web for any sorts of other tweaks I could try. Any other suggestions would be welcomed.

---

### Post by Progressive on 2008-11-27
EDIT: This fix seems to help a bit, but nothing major. It made the menus run faster for me.

[http://ubuntuforums.org/showpost.php?p=6246894&postcount=6](http://ubuntuforums.org/showpost.php?p=6246894&postcount=6)

---

### Post by Progressive on 2008-12-01
Perhaps GEM in combination with developments in the open source driver will do the trick. I hear it vastly improved performance in the open source intel drivers before, and that currently the open source ATI drivers are the only ones that support it.

Maybe when Jaunty Alpha 2 comes out I will devote a partition to it and play around with it.

---

### Post by donwest on 2008-12-16
I'm having the exact same problem. I'm using Ibex with an ATI Raedeon X700 PCI-E P4 3.0 GHz Hyper Threaded w/ 2 GB DDR. I just downloaded the new ATI 8.12 driver from the ATI site 2 days ago, the one released 12/11/08... I have Wine 1.1.10, compiled from scratch on my system, with the above mentioned registry changes and a few other recommended changes. I am having this very same issue to a T. I'll keep trying to see if there is some kind of work around or fix. I will say, I get great frame rate and moments of playability that are on par with Windows performance when using backbuffer as my OffScreenRenderingMode option in the wine registry.

---

### Post by lingnoi on 2008-12-17
> **Progressive said:**
> I hear it vastly improved performance in the open source intel drivers before, and that currently the open source ATI drivers are the only ones that support it.

Correct me if I am wrong however I thought the open source ATI driver could only do 2D right now.

---

### Post by Progressive on 2008-12-18
The Open Source ATI Drivers can do 3D incredibly well. In fact, they support DRI2.

The problem is that they do not support OpenGL 3 or even 2, and do not support GLSL. They can play most open source games like Nexuiz, but for anything more complex you still need Catalyst :(

However, there is a barebones Gallium3D ATI driver out there somewhere, and once that is complete it will be able to have drop-in support for any new graphics protocols.

Here is a screenshot from my desktop:

---

### Post by Progressive on 2008-12-18
One reason I care so much about this bug is because I think there is a good possibility for Fallout 3 to work once this bug is fixed, since they use the exact same engine.

If I can get Fallout 3 working on linux with freakin ATI, my friends will have absolutely no excuse not to switch to linux.

---

