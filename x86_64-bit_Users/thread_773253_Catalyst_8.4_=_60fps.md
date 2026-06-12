---
title: "Catalyst 8.4 = 60fps?"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by shadowplane676 on 2008-04-28
i have an ATI 200m graphics chipset on my HP zv6000 laptop, i just upgraded from Gutsy to Hardy (x86_64 Kubuntu) and went to re-install the ATI drivers. I tried EnvyNG (failed) and then tried the manual install wiki (make .deb packages and install). found the redirect fix for the xorg-driver, but now glxgears only shows 60fps. WTH? my screensaver looks fluid like before. any ideas or places to look?

---

### Post by Kilz on 2008-04-28
> **shadowplane676 said:**
> i have an ATI 200m graphics chipset on my HP zv6000 laptop, i just upgraded from Gutsy to Hardy (x86_64 Kubuntu) and went to re-install the ATI drivers. I tried EnvyNG (failed) and then tried the manual install wiki (make .deb packages and install). found the redirect fix for the xorg-driver, but now glxgears only shows 60fps. WTH? my screensaver looks fluid like before. any ideas or places to look?

Make sure that you have the ati drivers working. If flgrxinfo returns mesa instead of ati you dont. [This guide is what I used for Hardy.]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method")

---

### Post by shadowplane676 on 2008-04-28
fglrxinfo returns ATI for drivers. ive had to do this a few times, but ive always been able to get better FPS, 2000+fps in feisty, 1500-1700fps in gutsy, now 60fps in Hardy...

```
[19:49:18]:/usr/lib$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7415 Release

```

---

### Post by ASULutzy on 2008-04-28
This is an easy fix.

60 fps sounds like a very specific number to me, one that hints that you have vsync forced on. (ie your fps is exactly set to always match your monitor's refresh rate)

Turn off vsync and that'll probably shoot right up!

---

### Post by shadowplane676 on 2008-04-28
thanks, went into the ATI control panel, put the slider to full performance, 1600fps now. Hadnt had to do that before, but thanks for pointing that out, ill remember this :)

---

