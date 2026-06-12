---
title: "adding Windows XP x64 to Grub menu.lst"
date: 2005-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ckr on 2005-01-16
Hi,

After finally getting Ubuntu amd 64 to install, I've been having a bit of trouble getting  grub to boot my xp64 system.  Here's some info on my system.

HD0 ide 40 GB
Partition 0 is xp6 4
Partition 1 is Ubuntu 64
Partition 2 is Linux swap

HD1 sata 120 GB
Partition 0 is xp pro
Several more partition for data etc.

Grub did not automatically set up either of the windows systems.  I was able to get grub to run xp pro on the sata drive by using:

title                   Windows XP
root                   (hd1,0)
rootnoverify       (hd1,0)
map                   (hd0) (hd1)
map                   (hd1) (hd0)
chainloader +1

Since I have grub installed in the mbr of disk 0, where ubuntu and winxp64 are located, I assume that I do not need the maping lines.  At present, I have it listed manually as:

title                        Windows XP 64
root                       (hd0,0)
rootnoverify           (hd0,0)
makeactive
chainloader +1

I've tried various conbinations using the example given in the menu.lst file.  This is just where I stand at the moment.

I do notice that using third party partitioning software (Paragon Partition Manager) that the free space of hd0 is being reported incorrectly.  I'm not sure if this would cause problems only with the xp64 system though.  Ubuntu works great.

I'm fairly new at configuring grub in a multi boot situation, so any help you can give would be great.  Thanks for putting up with my long winded post!

Brian.

---

### Post by Benyman on 2005-01-17
hi Brian.Your menu.lst must view :

title Windows XP 64
root (hd0,0)
savedefault
makeactive
chainloader +1


i think so ;)

---

### Post by ckr on 2005-01-17
Thanks for your reply.

I still get an error message as follows:

        Booting  Windows XP 64
root (hd0,0)
     Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

As far as I can tell, the partition shouldn't be damaged.  I can access it fine from my regular XP Pro OS on the other HD.

Any other ideas?  :-( 

Brian.

---

### Post by ckr on 2005-01-18
[QUOTE=ckr]Thanks for your reply.

I still get an error message as follows:

        Booting  Windows XP 64
root (hd0,0)
     Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

As far as I can tell, the partition shouldn't be damaged.  I can access it fine from my regular XP Pro OS on the other HD.

Any other ideas?  :-( 

Brian.[/QUOTE]
 Just wanted to post that my problem was due to drive geometry.  Switching the drive to LBA in  BIOS allowed Winxp64 to boot with Benyman's menu.lst.

Now I have to decide whether it's worth trying to fix my winxp64 and ubuntu partitions being invalid (according to Paragon Partition Manager and Partition Magic).  Everything is booting fine now, but I can't edit those partitions as they are (resize etc.).  I can only delete them.

Brian.

Thanks for your help.

---

