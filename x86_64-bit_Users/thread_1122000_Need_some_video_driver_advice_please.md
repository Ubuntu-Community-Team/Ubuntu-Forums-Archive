---
title: "Need some video driver advice please"
date: 2009-04-10
forum: x86 64-bit Users
---

### Post by tristeng on 2009-04-10
I am running 8.04 and have an Radeaon x1600 AGP card installed but I am only using a default driver (no 3D graphics). 

I want to try to install the ATI catalyst driver (9.3), but I want to make sure I don't mess up my system.

Anyone have tips on how I can avoid this (backup my xorg.conf I assume, but what else)?

Basically, worst case scenario, if I attempt the driver installation and upon reboot get a blank screen (no login), what can I do to revert to the default driver?

I have no experience with Xorg but I've heard that I can just restore my backup xorg.conf (after booting into safe mode) and everything will be back to normal...is this true?

Thanks,

Tristen

---

### Post by Jimmyfj on 2009-04-11
If you mess up your graphics when installing the ATI 9.3 driver you can roll back to the Vesa-driver/default driver by using this simple command once you are logged in:


```
sudo dexconf
```

---

