---
title: "Weird Display issue after install"
date: 2005-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by bigern78 on 2005-12-18
HI Everyone,

I just installed the 5.10 AMD64 distro without any visible issues on my HP zv6201 lappy. When I boot into the default is get a blurry grey then blue cross hatched screen (login screen?). Anyone have any idea's where to start? Anyone know the fix?

Here are my specs

15.4" widescreen monitor with brightview
AMD 64 3200+
512MB RAM (one stick)
ATI Radeon Xpress 200M w/128MB RAM
Wireless B/G combo card (Broadcom chip)
4 USB 2.0 ports and 1 firewire port
60GB HDD
DVD +-R/RW (DL)
digital media reader.

Ubuntu 5.10 AMD64

Thanks for the help
BigErn

---

### Post by arctic on 2005-12-18
I am not 100% sure what you want to describe in detail (screenshot would be nice). But try booting with different video/framebuffer settings. You might want to test the system with vga=771 at bootup or with the nofb option. Take a look at the advanced settings and play around bit. If nothing helps, boot as normal, let it go wild, then reboot into an init 3 environment (no GUI) and check your /home/user/xsession-errors file (cat /home/user/xsession-errors). Any hints in there? Or in the /var/log folder?

---

