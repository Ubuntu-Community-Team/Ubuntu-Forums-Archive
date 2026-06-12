---
title: "OpenSUSE bootsplash."
date: 2008-01-28
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Jimmey on 2008-01-28
I selected the VESA graphics mode while I was installing OpenSUSE 10.3 thinking that it would use the vesa driver on the default install instead of the NV driver, which doesn't render the desktop properly on my screen.

It still loaded the NV driver, but there was no bootsplash, and the fancy graphics I got on the TTYs have gone.

I tried fixing the problem with YAST by re-enabling slash in the run-level thingie majig, but trying to enable it only got me a "this program is not installed" type error. By changing which runlevels it operates on (I can't remember which, it says something similar to B, 1, 2, 3, 4, 5, S), I was able to enable it, but I've still not managed to get the bootsplash to show. 

Anyone know how to resolve that?

Thanks

---

### Post by 67GTA on 2008-02-10
Open Yast. Go to SYSTEM>/etc/sysconfig Editor. On the left expand SYSTEM and then BOOT. There is a SPLASH section. Check to see if it is set to yes or no.

---

