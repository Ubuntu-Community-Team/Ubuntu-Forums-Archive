---
title: "Update rendered system unbootable"
date: 2007-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by anand78 on 2007-04-12
Update today 4/12 has rendered my system un bootable. I am currently on Kernel 2.6.20-14-generic. One odd behavior I saw related to update of linux-restricted-modules-common_2.6.20.5-14.19_all.deb where my kernel remained the same @ 2.6.20-14-generic. The booting process hangs at ohci detecting 3ports.  I have a zv5000 laptop, I would appreciate any help

---

### Post by stmiller on 2007-04-13
Ack! I have the same problem with 2.6.20-14-low-latency. I'm booting into an older kernel at the moment. Hopefully a fix will come soon.

See this thread:
[http://ubuntuforums.org/showthread.php?t=408057](http://ubuntuforums.org/showthread.php?t=408057)

---

### Post by rvbhute on 2007-04-13
I guess my problem is similar - [http://ubuntuforums.org/showthread.php?t=408174](http://ubuntuforums.org/showthread.php?t=408174)

I'm using 2.6.20-13 with vesa driver for now.

---

### Post by Aenea on 2007-04-13
I had the same problem... I fixed it by using the .bak version of /boot/initrd.img-2.6.20-14-generic...

Aenea

---

### Post by Aenea on 2007-04-13
And eh I should've read the threads from your links since someone else thought of the same solution :)

---

### Post by hopefull on 2007-04-13
Hi

I am glade to find this thread I thought I had done something stupid: I installed Beryl at the same time as the latest updates were loading and I could not reboot using 2.6.20-14, but I could using 2.6.20-12. So it is a question of waiting for a fix. 
One of the most important things about this community is that one is left isolated to deal with problems.

Hopefull

---

### Post by Kilz on 2007-04-13
Isnt that kernel from Feisty?

---

### Post by nbound on 2007-04-13
Yep, it was an update to the feisty kernel

---

