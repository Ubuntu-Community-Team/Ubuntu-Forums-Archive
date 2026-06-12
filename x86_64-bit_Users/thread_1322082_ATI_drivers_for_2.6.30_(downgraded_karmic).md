---
title: "ATI drivers for 2.6.30 (downgraded karmic)"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by gfxmonk on 2009-11-10
I had to downgrade my kernel (in karmic) to 2.6.30 to avoid a kernel bug. I noticed compiz and other shiny things weren't working, so I checked the "Hardware Drivers" dialog.

It says I have a "ATI/AMD proprtietary FGLRX graphics river" to install, but when I click "activate", nothing much happens. When I do so, the following appears in my "jockey.log":

2009-11-10 23:05:39,121 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2009-11-10 23:05:39,172 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"fglrx"\n']})
2009-11-10 23:05:39,203 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:39,204 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:39,215 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:39,215 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:39,222 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:39,222 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:39,232 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:39,233 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:55,085 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:55,085 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:55,146 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:55,146 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:55,161 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:05:55,161 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:06:04,295 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:06:04,296 DEBUG: XorgDriverHandler(fglrx, xorg-driver-fglrx, fglrx): xorg.conf driver matches
2009-11-10 23:06:06,959 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

here's my kernel info:
# uname -a:
Linux 2.6.30-020630-generic #020630 SMP Wed Jun 10 09:04:38 UTC 2009 x86_64 GNU/Linux

any idea what I need to do to get this working?

---

### Post by Ayuthia on 2009-11-10
How did you downgrade the kernel?  If you compiled it yourself, you will need to download the ATI driver from ATI and use the installer to install it.  If I remember correctly, the ATI driver in jockey is precompiled for the Karmic kernel so it will not work with 2.6.30.

---

### Post by jocko on 2009-11-11
> **Ayuthia said:**
> How did you downgrade the kernel?  If you compiled it yourself, you will need to download the ATI driver from ATI and use the installer to install it.  If I remember correctly, the ATI driver in jockey is precompiled for the Karmic kernel so it will not work with 2.6.30.
I'm pretty sure it should work fine with any kernel. The driver is compiled automatically by dkms when it's installed (and on every kernel install/upgrade).

---

### Post by gfxmonk on 2009-11-18
Thanks, (sorry for the slow response).

I couldn't find an ATI package, so ended up using the ATI installer. I then had a bunch of issues relating to compiz not working, X resolution being messed up, and other stuff that seemed to be sporadically working.

I've since decided that the standard kernel is the least work (despite the bug), so I've had to reinstall ubuntu fresh (it got to the opint where GDM would not display at all on boot). So I think I'll stay away from this area for now...

---

