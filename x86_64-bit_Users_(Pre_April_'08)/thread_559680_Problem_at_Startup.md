---
title: "Problem at Startup"
date: 2007-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by fuji2086 on 2007-09-25
I'll start by letting you know I'm new to ubuntu.

Ok, now that you know that: I have a Dell Vostro 400. I just set it up to dual-boot with 7.04 and XP. Ubuntu recognized very little of my hardware, and thus far, I have only managed to install drivers for my wireless card (Linksys Wireless-N PCI - WMP300N) and my video card (nVidia GeForce 8600GT).

Since I installed Ubuntu, when I started it normally, the screen would go black after telling me the Kernel is alive, then come back on with the login screen. After installing my video drivers, it never actually made it that far. I started it in recovery mode to find where it ran into problems. Here it is:

```

ata1.00: cq timeout (cmd 0x27)
...
ata1.00: failed to set xfermode (err_mask=0x40)
ata1 failed to recover some devices, retrying in 5 secs

```

I don't really know where to start on this. Any help would be great.

Thanks

---

