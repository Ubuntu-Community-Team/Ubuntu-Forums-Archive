---
title: "How to access nVidia &quot;raid&quot; drive?"
date: 2007-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aethor on 2007-12-31
Hello,

first time Linux user here. (fair amount of Windows experience though, so I understand the general concepts).

Can anyone help me with this problem?

my setup: 
- Kubuntu 7.10 64-bit version.
- existing and working Windows XP 64
- AMD 4400 x2, Asus SLI Deluxe motherboard, nForce 4, nVidia sort-of-raid.
- 4 Gb memory, GeForce 8800 GTX, Audigy 4
- 2 disks of 200 Gb each and another 2 of 300. First 2 were RAIDed, and to simplify the installation, I backed up the partition, made that raid array into 2 separate disks, 1 for Windows and 1 for Linux. The remaining 2x300 are still in a raid array, 600 Gb disk, working under Windows and should keep working that way.

I installed Kubuntu on the non-raided disk. It assigned the raided disks as /dev/sda and /dev/sdb, non raided as sdc (Linux) which I partitioned into 3 partitions - 100 Gb for root, 20 for swap, 80 for /home, and the remaining non raided disk as sdd.

The installation works (after removing splash and fixing GRUB a bit), I can boot into Kubuntu and also into Windows. Kubuntu recognizes ext3 partitions on /dev/sdc and ntfs partition on /dev/sdd and mounts them correctly.

However, in its file manager (Dolphin) I see the raid array as a 600 Gb disk - unmounted. And it cannot be mounted, I get an error message if I try.
"hal-storage-fixed-mount-all-options refused uid 1000".

Note that dmraid is NOT installed. Here's the interesting part: if I install dmraid, next boot drops me at the BusyBox prompt. I cannot see all of the error messages, but those I do see say that mounting /dev/sdc1 (which is my Linux root) failed because the mount point was locked. And the mount point is /root. 

Before these messages, I saw some error from /dev/mapper/something, the rest scrolled off. I tried to find it in the logs but couldn't. (As I said, I'm a Linux newbie)
(there is a bunch of error messages about accessing sda and sdb, which are normally part of the raid array)

At this point, the only way I could fix the situation was to revert to an old initfs image. Currently I work on a totally reinstalled Kubuntu (reformatted ext3 partitions). As long as dmraid is not installed, everything works - except mounting that raid array.

I have found a number of tutorials about fake raids, but they mostly deal with situations where people need to >>install<< Linux on such a raid.

I do not need to install it. It works off a normal, non raided disk, and it works well. I cannot use Linux software raid,since the raided disks also need to work from Windows. I do not need to change partitioning. I just need a way to set up dmraid so that it does not stop the boot sequence, and to make it mount the raid array.

Note that the raid array works correctly when accessed from Windows, all the files are there, so there is no error in the raid array itself.

Any help is appreciated. If any additional info is needed, feel free to ask and I will post it here.

---

### Post by foolsh on 2007-12-31
```
refused uid 1000
```

says you dont have permission 

```
sudo dolphin
```

then try to mount it 
hope this helps

---

### Post by Aethor on 2008-01-01
Doesn't help, I get the same error message when running as root.

---

