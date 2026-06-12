---
title: "Metro 2033 Keyboard input"
date: 2014-06-08
forum: Wine
---

### Post by theangryspider2k on 2014-06-08
I am trying to get Metro 2033 working in wine. It seems to be working fine (with xact, physx and d3dx9 installed with winetricks) except for one problem, the keyboard doesn't work in menus. That makes it impossible to change controls or buy equipment and ammunition at metro stations. I've tried setting dinput8 to native in winecfg but that broke mouse input completely and the keyboard was still the same. One of the comments on the winehq page for the game said that keyboard input worked fine in wine 1.5.4 but for me it crashes on any version below 1.5.11. Does anyone know how to fix the keyboard issue?

My PC:
Intel i3 2100
EVGA GT630 2GB - driver version 331.67
4GB RAM
Xubuntu 14.04

---

### Post by adec2 on 2014-06-08
[http://wiki.winehq.org/winecfg](http://wiki.winehq.org/winecfg)

Under the Graphic>Window Settings on that page have you tried unchecking

"[B]Allow the window manager to control the windows" ?

That has helped me gain keyboard input in the past


[/B]

---

### Post by theangryspider2k on 2014-06-09
Deactivating that setting doesn't appear to have made a difference. Is there a way to capture keyboard input in wine?

---

### Post by theangryspider2k on 2014-06-16
Bump. Any ideas on how to fix this?

---

### Post by adec2 on 2014-06-17
It may be better to post your problem on the wine forums, they have specific people who could help

[http://forum.winehq.org/viewforum.php?f=2](http://forum.winehq.org/viewforum.php?f=2)

---

