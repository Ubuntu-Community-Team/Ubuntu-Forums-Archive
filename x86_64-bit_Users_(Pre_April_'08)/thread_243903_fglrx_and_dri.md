---
title: "fglrx and dri"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by relux on 2006-08-25
I have a ATI Radeon Xpress 200G in my machine. I am trying to get the fglrx drivers to work correctly so I can ultimately play World of Warcraft. I have gotten the drivers to install and to work with what appears to be correctly. When I run glxgears I get about 200fps. 

With the "ati" driver I get the following error:
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.

With the "fglrx" driver I get:
(EE) AIGLX error: dlopen of /usr/lib/dri/fglrx_dri.so failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __glXFindDRIScreen)
(EE) AIGLX: reverting to software rendering

I am using 64-bit edgy. Can anyone shed some light on this?

---

