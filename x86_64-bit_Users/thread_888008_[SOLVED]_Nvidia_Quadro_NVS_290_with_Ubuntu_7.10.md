---
title: "[SOLVED] Nvidia Quadro NVS 290 with Ubuntu 7.10"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by YMas on 2008-08-12
Hello all,
I'm trying to get the Nvidia Quadro NVS 290 to work with two monitors (Dell 2408 WFP) on a Precision T5400 with Ubuntu 7.10 (x86_64).

I downloaded the restricted drivers and the setup utility from Nvidia, followed the instructions and everything works.  

The monitors are correctly detected and the resolutions are fine.

The problem occurs when I restart the system (as in shutdown -r rather than alt-ctrl-backspace), all the settings are lost.  The "Nvidia XServer Settings" utility goes back to an older version.  Everything works fine again if I "re-install" the driver.  I have placed the:
```

nvidia-settings --load-config-only 

```

in my xinitrc file.  This doesn't seem to make any difference, I still have to install the drivers again on system re-start, but I don't need to configure anything (ie enable the second monitor and select Twinview).

Any pointers would be greatly appreciated, perhaps I have missed something in the man page for nvidia-settings, xorg.conf or xinit.

Thanks for your help.

Regards,
YMas

---

### Post by YMas on 2008-08-16
I manually removed the residual files remaining after I'd installed the drivers from the restricted-driver manager.

I deleted the following directories from /lib/linux-restricted-modules/[my kernel version]:
nvidia
nvidia_new
nvidia_legacy

Everything seems to be working fine, the Xorg.0.log file doesn't show any errors.  

Both panels detected, resolution is fine.

---

