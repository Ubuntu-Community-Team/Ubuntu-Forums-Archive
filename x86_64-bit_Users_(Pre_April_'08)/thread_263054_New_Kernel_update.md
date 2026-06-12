---
title: "New Kernel update"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-09-22
This update seems to have really upset  things. I now notice if I add a program from synaptic the console comes up about overwriting a number of files in the vmplayer directory. After installation completes vmware is gone and I have to go through an install again. Really messy I wished I had let the upgrade pass by.

---

### Post by thoffland on 2006-09-30
It doesn't prompt you to run /usr/src/vmware-config.pl (or something like that)??? 

I just did the upgrade and had to reinstall my kernel headers then ran that and it's working with my original XP installation (need it for school work :roll:) 

The only thing is that I had to rename or "mv" the "linux-headers-2.XXX-amd-generic" to just "linux" in order to get it to work. You'll know if you come across this when running the config.pl.

---

