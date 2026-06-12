---
title: "Kernel upgrade creating uniterruptible processes?"
date: 2007-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by immanueloffice on 2007-07-27
Last week I began having problems with my Crossover (Wine) installation, specifically Word. Word would lock up and become an uniterruptible process. It would then make my Nautilus uniterruptible, and then I would lose file system access and things went downhill until I rebooted.

I contacted Codeweavers, reinstalled Crossover, etc. but haven't seen any improvement. It is now uninstalled, and the system seems stable without it.

In searching the internet, it seems that uniterruptible processes are due to kernel issues. When I looked at my update history in Synaptic, there was a new kernel installed on Thursday. So, that seems like a worthwhile avenue to pursue.

I am using 6.06 LTS on AMD 64. My kernel upgrade was: linux-image-2.6.15-28-amd64-generic (2.6.15-28.55) to 2.6.15-28.57.

My questions: 1. Is there a way to roll back my kernel to the one that seemed to work to test?
2. Any one else have problems like I am experiencing?
3. If I wanted to get a later kernel (they are available for Feisty, etc.), how do I do so within 6.06?

Thanks!
Crystle

---

### Post by madmetal on 2007-07-28
hey :)
1) when you boot you can choose to boot into the older kernel from grub menu ;) (maybe you have to hit enter to enter grub menu)
2) dont know .. :(
3) you have to compile it your own..  
some how-to's about kernel compilation..
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by immanueloffice on 2007-07-31
My history says I went from 2.6.15-28.55 to 2.6.15-2.57 and in /boot I only have 2.6.15-27 and then 2.6.15-28, so does that mean I can't boot from 2.6.15-28.55, which is where I think everything was okay.

---

