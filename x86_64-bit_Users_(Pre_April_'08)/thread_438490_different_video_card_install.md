---
title: "different video card install"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by paulmac on 2007-05-09
Does changing the video card call for a reinstall of Ubuntu?  I switched out a Nvidia card for a ATI 900 last night and reinstalled 6.10 to get it working.  Is there an easier way than reinstall?

---

### Post by Ken_Lewis81 on 2007-05-17
The command to reconfigure any installed package is 'dpkg-reconfigure'.  The graphics card setup is controlled by xserver-xorg, so running ```
sudo dpkg-reconfigure xserver-xorg
``` will allow you to reconfigure the setup.

take care.
Ken.

---

### Post by kuja on 2007-05-17
> **paulmac said:**
> I switched out a Nvidia card for a ATI 900 last night Why on earth would you do that?

---

