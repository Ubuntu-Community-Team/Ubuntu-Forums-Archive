---
title: "Command-line: Disable Restricted Driver Usage"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by The Broodwich on 2007-12-27
Hi everyone,

I just enabled the ATI Restricted Driver in Gutsy -- and I'm now booting into the black screen of death. GRUB has no "safe graphics" option for me, so I was wondering if anyone knew the code I can use in recovery mode to disable the use of the driver.

Thanks,
Broodwich

---

### Post by Yellow Pasque on 2007-12-28
Which driver? The ATI fglrx driver?
Try: ```
sudo apt-get remove xorg-driver-fglrx
```

Or, you can go into your xorg.conf (sudo nano /etc/X11/xorg.conf) and manually change the Driver option to "vesa"

---

### Post by The Broodwich on 2007-12-29
Would the apt-get line provided remove the driver as well as change the xorg.conf file back to the default vesa, or would it just delete it and then have the system try to access a package that doesn't exist?

---

### Post by Yellow Pasque on 2007-12-29
I'd imagine that the driver removal wouldn't touch the config file and then the Xserver would revert back to failsafe VESA values the next time the system is booted

---

