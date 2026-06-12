---
title: "Trouble installing Ubuntu 7 x64 on IDE controller card"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thomas Bags on 2007-06-03
Whats wrong is that I have been trying to install **Ubuntu 7.04 Feisty Fawn x64** onto one of my hard drives that is on a **RAID Card/IDE Controller Card**.  Now first off I'll admit I do not know much to anything about RAID configurations as I have never had experience with them.
So this is how my setup goes:

AMD 3800+ x64 Dual Core 2.0 GHz

Motherboard: Gigabyte GA-M61VME-S2

On the 1 IDE port on my Motherboard:
*(Primary)* DVD-+RW
*(Slave)* 80 Gb IDE HDD 
(2 partitions, 40 NTFS w/ Windows XP Pro, 40 NTFS w/ Windows Vista Ultimate x64)

IDE Controller Card (_Syba ATA8212-133R_):
*(Primary)* 40 GB HDD (2 partitions, _20 GB ext2_, _20GB fat32_, *no OS yet* :()
*(Slave)*250 GB HDD (1 partition NTFS, [I]no OS, for backup space only)
[/I]
Graphics Chip: NVIDIA GeForce 6100

Network (I think thats what it is): nForce 400

Now to the problem,
first off when booting on the Ubuntu live CD **I get quite a few errors**, such as *freezing* and a bunch of other text, and** it takes a long while to boot** (compared to my older 1.5 GHz desktop which boots the Ubuntu live CD in about 1 minute).  I do get to the live CD though, but when I go to install, **the partition manager does not see any of the drives on my IDE Controller card**, and therefore I can't install to the right partition.  Now _I have used the GParted Live CD_ and it reads it just fine as well as Windows.

[SIZE="4"]**So in short, I'm asking how do I get Ubuntu to recognize my IDE controller card so I can install to it.**[/SIZE]

---

### Post by Cappy on 2007-06-05
You probably need to open a terminal (Applications-->Accessories-->Terminal) and enter in
```
dmesg
```

You can post the whole thing to this thread or try to find the parts that relate to the hard drive. Post it in a "[ CODE ]" stuff here "[ /CODE ]" (without the spaces or quotes!)

---

### Post by Thomas Bags on 2007-06-06
Okay, I'll try that then.

---

