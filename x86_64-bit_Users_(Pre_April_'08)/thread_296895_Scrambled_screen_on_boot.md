---
title: "Scrambled screen on boot"
date: 2006-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by 2tall2hide on 2006-11-10
I installed Ubuntu 6.10 edgy on my 4400 Athlon X2, after the loading screen ubuntu loads with an unreadable scrambled screen,
On the installation CD I could change the resolution on the boot menu to get past that problem.  I need to know how to change the resolution before my installation boots. Using SLI nvidia 7600

---

### Post by kuja on 2006-11-10
I recommend you boot into recovery mode, and install nvidia-glx. I doubt the open source drives have *proper* support for an SLI setup. 

```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

Then reboot and see how things work out.

---

