---
title: "xorg file almost empty!!"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by Mazen on 2009-04-29
my xorg.conf file is ```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```
I wonder why it's so short!!
My system sometimes freezes for no reason, and the picture breaks, is it related?
Thanks,

---

### Post by cariboo on 2009-04-29
That's normal, mine looks exactly the same on both Jaunty and Karmic. You will have to look elsewhere, check your ram. At the grub menu select memtest.

---

