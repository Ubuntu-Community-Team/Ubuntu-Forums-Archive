---
title: "No display in xorg after first reboot"
date: 2005-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Grasshopper on 2005-07-28
Hi all,

I have installed Ubuntu 5.04 AMD64 3 times now and the same problem happens each time. The install works perfectly (as far as I can tell), after install is completed I get the user prompt at the desktop, can login and all is good.

However, after I shutdown and restart the PC and boot into Ubuntu (is dual-boot with WinXP64), when xorg tries to start I get a blank screen, I can hear the desktop startup sounds and if I type the user/pass in it seems to still be doing stuff (can see HDD activity and another sound plays after logging in). 

The only thing I can see on the (LCD) screen is there are some lit pixels across the very top of the monitor. If I try CTL-ALT-BKSPACE 

System specs:

AMD64-3500+ (Newcastle)
Gigabyte GA-K8NS Ultra-939 (NForce 3 250)
2 x 512MB Kingston PC3200
Nvidia 6600GT (Leadtek)
LG L1710B LCD Monitor

Has this happened to anyone else, or anyone know of a possible fix ? I tried rebooting into (diag?) mode and do get a text screen prompt but I'm not sure what to check for 

Cheers.

---

### Post by Grasshopper on 2005-07-30
Well, I seem to have fixed it by not selecting the highest res the monitor can display (1280x1024) during setup, just accepted the default settings (max 1024x768), now works OK after the first reboot so hopefully should be all OK now.

---

