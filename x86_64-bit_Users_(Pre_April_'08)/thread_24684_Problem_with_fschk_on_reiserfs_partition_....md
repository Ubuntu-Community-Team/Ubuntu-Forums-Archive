---
title: "Problem with fschk on reiserfs partition ..."
date: 2005-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by steled on 2005-04-08
When running fsck on a reiserfs partition.
The command prints out that everything went
right. But the  returncode is 8 !!??
This is very annoying as it interrupts the boot process and requires me to press CNTRL+D to
continue booting.

Did annyone experience the same problem ???

---

### Post by lao_V on 2005-04-08
Can't say I've had that problem. Was the system shut inappropriately last time?

---

### Post by steled on 2005-04-09
[QUOTE=lao_V]Can't say I've had that problem. Was the system shut inappropriately last time?[/QUOTE]

No it appeared from a fresh install of ubuntu on. 
I repartitioned my drive during the installation.
sdb1 /boot
sdb5 /
sdb6 /home

and the first  boot process and consecutive ones where always interrupted by a
file system check failure. 
Executing the  manually check: 
 fsck /dev/sdb6 
Displays messages that all whent right. Althought the return code is 8.

---

### Post by warpengi on 2005-04-09
I have the same problem.  I thought it might be related to my RAID configuration but you are having the same issue without raid.  Could it be the separate /boot partition?   I am using sata drives too, perhaps another source of the problem??

My partitions:

md0 /boot
md1 /
md2 /home

I get an fsck error on md0 and md2 during boot.  Despite the error message, simply doing Ctrl-d will continue the boot process.  I don't see anything in my  log files to indicate an fsck error during boot.

---

### Post by Trograin on 2006-03-24
Annoying, I am running a sata HD as my backup and I am allso forced to click CTRL+D to get the startup to go on becouse of the FSCHK saying that it cant find partition table on teh sata drive. funny enough it is partitioned and when ubuntu is upp and running I can mount the HD and use it properly with no problems at all. The CTRL+D is though very annoying and very bad for me when i sometimes am forced to remotley restart the server. I cant do that becouse of FSCHK. 

Does anyone know how to tell ubuntu NOT to run fschk on a specific HD??

---

