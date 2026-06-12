---
title: "Help Please! Problems with Ubuntu and WIndows Vista"
date: 2009-01-23
forum: x86 64-bit Users
---

### Post by calderp on 2009-01-23
Hi
So I was fed up enough with windows vista to try the switch to linux but am having a couple problems. I am running 8.10 on a new Toshiba Satellite laptop. In order to install Ubuntu I used the Linux partition manger (I forget the name, but think it started with G? From what I found online it is the most commonly used), then installed Ubuntu onto my new parition. Ubuntu is running fine but my first problem is that I am not able to boot into Vista. I had thought that in doing this I would be able to dual-boot, but I don't have an option for Vista during Gnome boot-up. Any idea why?

The second, more important problem, is that Ubuntu is not recognizing (or I cannot find) most of the hard drive partition that has Vista on it so I'm not able to access any of my music or files.
I read some threads related to this but couldn't make much sense of them. I did get the impression that in order to help it would be useful to see this:
calderp@paulpc:~$ sudo fdisk -l
[sudo] password for calderp: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f9a64c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2             192         336     1160192+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         337       29096   231014700   82  Linux swap / Solaris
/dev/sda4           29097       30401    10482412+  83  Linux
/dev/sda5             192         336     1160192    7  HPFS/NTFS
calderp@paulpc:~$ 
calderp@paulpc:~$ 

I'm guessing that 'Partition 2 does not end on cylinder boundary.' would be my problem? 

If anyone can help with either of these problems (but primarily the hard drive issue) it would be wonderful. I have essentially no knowledge of linux so you'll have to explain things pretty simply I'm afraid but I'm generally good with computers so it shouldn't be too hard. 
I'm sure this question has been raised before so I apologize for that but I couldn't find a thread that made enough sense for me to get it to work...
Thanks Again

---

### Post by dmizer on 2009-01-23
Closed this. Duplicate here: [http://ubuntuforums.org/showthread.php?p=6605794](http://ubuntuforums.org/showthread.php?p=6605794)

---

