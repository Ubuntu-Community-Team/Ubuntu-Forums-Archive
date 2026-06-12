---
title: "Two Xorg and two gdm"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by Jokimoto on 2008-07-10
Two Xorg processes and two gdm processes?
I saw several threads in the archive detailing this same issue, and several bug reports elsewhere (all going back several versions), none of which came to a solution.
There seems to be a bit of debate over whether this is a "bug" or a "feature" lol. From my pov it's definitely a bug, as my OS is now using 1Gb of RAM just to show my desktop.
For the record, I only have one monitor, and an ATI HD2600. I tried uninstalling the fglrx driver and reverting to the default vesa, but my card isn't supported and I can't get a resolution above 800x600 so I went back to the proprietary driver.
Everything's working fine, emerald etc. Still, I'd sure like to have more than just half of my meagre 2Gb of RAM available.
Any suggestions?

---

### Post by soxs on 2008-07-11
i don't think it's the reason your system covers up 1gb of mem (Note: unused RAM is wasted RAM). My PC has the same thing and the easiest way to make sure you only have 1 xserver running at a time, would be to a kill one process of these xservers (always do the second one), I allready tried this, but the second one will remain as <defunct> in your processlist and will still cover the same amount of RAM as xserver1 does (I still believe they are one and the same, and processmanager shows 2 refernces to it.)
Note: check your system usage always with "top" in terminal

If you fear a lack of memory, get another stick of 2gb and you're fine.. don't expect amd/ati to fix it in the near future/at all... I am now 3 years running ubuntu, and nothing happened.

---

### Post by AusIV4 on 2008-07-11
If you have a multi-core processor, the process list may show multiple instances of certain processes that take advantage of all the cores.

As far as memory consumption: Linux uses a lot of shared libraries. As a result, even if you are running two copies of Xorg and gdm, they'll be using a lot of the same data in memory. That memory will be reflected twice in the process list, but it will only be subtracted from your available memory once.

---

### Post by Jokimoto on 2008-07-12
Thanks for the quick replies :)
soxs: I tried the same thing, killing the "inactive" one, and suffered no ill effects. Sorted them by dependencies and saw a tree like this:
gdm
  gdm
    xorg
      xorg
I'm not really worried about it tho, was mainly curious. 

AusIV4: no dual-core, and I appreciate the simple explanation.

---

