---
title: "Starcraft - Half of the tittle screen stays on the screen"
date: 2014-02-09
forum: Wine
---

### Post by Jeff Morris on 2014-02-09
I just installed the original StarCraft from CD, and patched it to 1.16.1. The installation and patching both ran without any problems.

However, when I run StarCraft, the initial splash screen and sound plays correctly, but then the top half of the splash screen remains and never changes, i.e. only the bottom half of the screen updates. This appears to be the exact same problem described in this thread: [http://ubuntuforums.org/showthread.php?t=1906118](http://ubuntuforums.org/showthread.php?t=1906118), however that thread was closed without any responses, so no joy there. Even the screenshot that Krasus posted in that thread looks just like mine (except of course he has the Starcraft Broodwar splash screen while I have the original Starcraft splash screen.)

I'm running:

Ubuntu 12.04.4 LTS
Wine 1.4
eMachines E725 laptop

lspci output for my video card:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0212
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 50f0 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 3
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
        Subsystem: Acer Incorporated [ALI] Device 0212
        Flags: bus master, fast devsel, latency 0
        Memory at 93400000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [d0] Power Management version 3
```

I've tried the "Cure for Slowness" registry tweaks listed here:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149). I did not see any change in behavior.

I've tried enabling the Wine virtual desktop. That actually works and the game plays normally, but in a 640x480 window of course. I'd like it to run fullscreen.

---

### Post by Jeff Morris on 2014-02-09
Update: I tried switching the default Wine renderer from OpenGL to GDI (i.e. the opposite of what the instructions in the above linked WineHQ page say to do - I read through the comments on that page and found that the Wine default had been changed from GDI to OpenGL some time ago, so the instructions are out of date.) That fixed the game for me, it runs fine now. The opening splash screen and video don't seem to work now, but I can live with that.

While this is a workaround that works for me, I'm curious as to why the OpenGL renderer is having problems on my system? Something to do with this laptop's crappy Intel video I'm sure?

---

