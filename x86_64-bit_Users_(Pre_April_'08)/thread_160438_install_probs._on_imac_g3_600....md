---
title: "install probs. on imac g3 600..."
date: 2006-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by imacQ on 2006-04-14
i formated a new 120gb maxtor using osX. did clean installs of os9 and osX on separate partitions; also have 25 gb free space partition for ubuntu (ubuntu to be on the first of the 3 partitions). however, when i try to install ubuntu partitioning  with use largest freespace, install hangs on, "install the base system", and when i try to install base system again it goes back to partitioning and then comes up with "no newworld boot partition was found. the yaboot loader requires an apple_bootstrap partition at least819200 bytes in size. the first time it told me to "check /target/var/log/bootstrap.log." how can i create this apple_bootstrap now? ](*,) must i start over? :-k 

help, suggestions, splain it to me lucy, all appreciated. 
now i hear thunder and should probably get off the computer. damn.

---

### Post by dpny on 2006-04-15
I had a similar problem when I tried to install Ubuntu on my PIsmo. I had formatted the partition meants for Ubuntu with HFS+, so the Ubuntu installer wasn't seeing it as free space. I don't remember exactly where, but if you choose the option for manually configuring the partition process, you can remove a partition. I did this to the partition meant for Ubuntu, and the installer was able to recognize it as free space.

---

### Post by jdp on 2006-04-15
I would start again and delete the Ubuntu partitions.  Of course be carfeful to not delete the other parts that you want to keep. ;)  Then try the "Use largerst continous free space" option again.  You are using the easy install, ie **not** typing "expert" at the boot prompt?

---

### Post by imacQ on 2006-04-15
that's exactly what i did, and the install went smoothly. then i dealt with the "oh so slow problem," as in couldn't even use terminal in gnome, and where is my cursor now. got out that by hitting the restart button, and at the boot prompt opened terminal window using <control> <F1>, did sudo nano to get  to put #  by the load dri module. YES, :mrgreen:  ZOOMING along now.

---

