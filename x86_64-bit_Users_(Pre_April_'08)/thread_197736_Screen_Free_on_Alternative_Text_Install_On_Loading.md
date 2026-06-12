---
title: "Screen Free on Alternative Text Install On Loading Grub"
date: 2006-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by TJInc. on 2006-06-16
Hi All,

I've followed some advice and decided to install 6.06 using the Alternative CD with a text based install.

I've setup RAID 0 using the instructions from this forum on [www.ubuntuforums.org/showthread.php?t=193434](www.ubuntuforums.org/showthread.php?t=193434).

The screen freezes when running the Grub during the install process. 

I've set up the partitions for the two drives as follows equally the same: 
ie. both disks have the same partitions as follows:

90 GB RAID primary (boot)
100 GB RAID logical
100 GB RAID logical
10 GB RAID logical 

during the install process in the partioning program after setting up the array (joining the matching partitions together) you can then set the file type, at which point I selected each raid partition, which is now double in size after joining in an array and set the following:

180GB ext3 /boot
200GB ext3 /
200GB ext3 /home
20GB swap

My question is where does one set the BOOT parameter to ensure that Grub will boot. Maybe that's why the system hangs at that point.

Is there anything I'm missing...

Regards,

---

### Post by TJInc. on 2006-06-16
Just one more point which may help, the screen freezes at this point:
Header says "Installing GRUB boot loader" at 50% complete and the detail says Running "grub-install (hd0)"...

Hope that helps. I think it's something to do with the boot partition.

Regards.

---

