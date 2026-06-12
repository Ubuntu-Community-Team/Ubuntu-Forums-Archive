---
title: "mdadm segfaults, random segfaults..."
date: 2007-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by remi_2 on 2007-10-29
I have a new machine with an Intel Bad Axe 2 mobo with latests BIOS firmware, a Q6600 CPU and 4*2 gigs of Corsair ram, nvidia 6200A graphics. It has a 80Gigs system disk, and two 320Gigs disks in soft RAID-0 with /home on it. 

The machine was running Feisty and now Gutsy.

I systematically have the following line in dmesg : 

[   29.686083] mdadm[2604]: segfault at 0000000000000004 rip 000000000041724c rsp 00007fff475ff700 error 4

which is strange because my RAID-0 array is mounted and assembled just fine.

Also, I experience random freezes and segfaults of other programs. 

I suspected the RAM so I've run a memtest from the ubuntu CD overnight, with came out clear,

I'm out of ideas now :confused:

---

### Post by kuja on 2007-11-01
I vote for running fsck on all partitions.

---

### Post by netbandit on 2007-11-01
cat /proc/mdstat

check it out
-nb

---

