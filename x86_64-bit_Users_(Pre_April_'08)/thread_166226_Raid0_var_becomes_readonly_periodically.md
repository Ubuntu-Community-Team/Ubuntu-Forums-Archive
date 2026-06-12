---
title: "Raid0 /var becomes readonly periodically?"
date: 2006-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsottwallace on 2006-04-26
Colleagues,

I have 3 servers with 5.10, all identical hardware (except for the amount of ram).  I set up raid0 on a squid-proxy server (now I've learned that squid is faster without raid0!).  The overall setup looks like this:

Disk 1
   part1, /boot, 50megs (non raid)
   part2, raid0, swap, 1gb (part 1 of raid0 swap)
   part3, raid0, /, 5gb (part 1 of raid0 /)
   part4, raid0, /var, 74gb (part 1 of raid0 /var)

Disk 2
   part1, /balance, 50megs (non raid; keeps disks symmetrical)
   part2, raid0, swap, 1gb (part 2 of raid0 swap)
   part3, raid0, /, 5gb (part 2 of raid0 /)
   part4, raid0, /var, 74gb (part 2 of raid0 /var)

The problem I am having is that every once in a while (1 to 2 times per week) the /var directory becomes read-only.  Rebooting fixes this, but I see fsck errors, which are never the same twice.  Anyone know how to diagnose and/or solve what is going on?  I think it might have to do with squid, which keeps its cache in the /var dir.  I am not a complete newbie, but the raid thing and the ubuntu distro is new to me.  And I am really burning out on this (sympathy plea)...

Cordially,
J

---

### Post by jsottwallace on 2006-04-26
Let me add that the other 2 servers, which do not run squid but do have raid arrays, have not had any problems (yet).

---

### Post by jsottwallace on 2006-05-13
Resolution::KS 

   I tired everything I could think of; changing to 32 bit ubuntu, using PCI SATA cards (adaptec 1210), different filesystems, BIOS upgrades and configurations, moving equipment around in case of interference, cooling the hard drives...  Nothing worked.  

   After having read some stuff about how some kernels have trouble with SiS chips (my servers have North Bridge SiS 760 GX & South Bridge SiS 964), I decided to use a newer kernel.  So I wiped my systems with DBAN and **installed the Dapper AMD64 server distro** (still beta as of May).  Then I did a **apt-get dist-upgrade**.  As of yet (about a week) there have been no problems with my servers, including using more advanced filesystems like raid1.  

Ignore the following list of data for the web crawlers to find to help other poor souls like myself:

sis 964 sis 760 UNEXPECTED INCONSISTENCY BUFFER I/O ERROR ON DEVICE MD2, LOGICAL BLOCK ERROR READING BLOCK (ATTEMPT TO READ BLOCK FROM FILESYSTEM RESULTED IN SHORT READ) WHILE DOING INODE SCAN. kernel SATA freeze read-only read only readonly

---

