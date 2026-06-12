---
title: "hfs+ (mkfs.hfsplus and fsck.hfsplus)"
date: 2006-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by BoneKracker on 2006-05-20
I am trying to compile the diskdev_cmds from darwinsource, because I want to use Apple's **newfs_hfs** and **fsck_hfs** (as **mkfs.hfsplus** and **fsck.hfsplus**).

I got mkfs.hfsplus (haven't tested it yet) but wasn't able to compile the other.  Has anybody got this working? I'm using dapper (gcc 4.0).

Thanks.

---

### Post by slux on 2006-05-23
There's a patch for an older version available. It seems to work well, sorry I can't give a straight link but I tried to search the forums for the old posts to no avail. It is somewhere here though. Actually seems like googling for diskdev_cmds gives plenty of resources with the patch...

---

### Post by BoneKracker on 2006-05-24
Actually I discovered that the newfs_hfs compiled and seems to work fine (so I now have a "mkfs.hfsplus") but no such luck with fsck.  Thanks for the tip.

---

### Post by slux on 2006-05-25
Well, something like that was the problem back when I tried it too but the one I really wanted was fsck so I just downloaded the older version and the patch so I could fsck my HFS+ partitions properly. Didn't bother looking whether I could've made the patch work for the newer version since the older one seemed to work fine.

---

### Post by E5o on 2006-07-13
Greetings fellow hfsplus sufferers

I'd just chime inn with my solution to this problem.

To make a long story short, I had to repartition the hfsplus HDD WITHOUT installing the Mac OS9 drivers-option that is checked by default in Disk Utility in OSX when you partition a new HFS-drive.

After doing this, I can write to the hfs+ drive without problems.

cheers

E5o

---

