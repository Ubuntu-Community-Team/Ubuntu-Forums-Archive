---
title: "Failed to copy files; faulty CD/DVD or hard disk ?"
date: 2008-05-28
forum: x86 64-bit Users
---

### Post by anjanesh on 2008-05-28
I tried installing Ubuntu 8.04 64-bit today on this system :
```
Intel Core 2 Quad Q6600
2.4GHz 8MB cache 1066MHz
Intel Desktop MotherBoard DG33
8GB DDR2 RAM 800MHz Transcend (4 x 2GB)
1GB 8600 GT nVidia Graphics Card
500 SATA HDD Western Digital
Microsoft Wireless Keyboard & Mouse 700
20x Samsung DVD Writer
22" LG LCD monitor
```
I burned the DVD twice - the 2nd one at lesser speed so that the DVD is fine.

I got this error at 63%

[IMG]http://img300.imageshack.us/img300/4268/ubuntu1gm9.gif[/IMG]


After that it went to desktop - I think it was switched to Live mode. Yet why was it showing this info on a 500GB hard-disk ? Has the hard-disk gone bad ?

[IMG]http://img233.imageshack.us/img233/3738/ubuntu2yl0.gif[/IMG]


Thanks

---

### Post by wandalalakers on 2008-11-12
I got this error when trying to install 8.04 from a remastersys created iso.
One of my memory sticks was bad.  Try booting a live cd and running memtest to see if your ram is bad.  I had 640mb (three sticks) and was getting "Failed to copy file; faulty CD/DVD or hard disk?".  It would stcop around 35%.  I tried the alternate CD also and was unable to complete the install.  I even tried a LinuxMint CD.  Replacing my ram fixed the problem for me.

---

### Post by viper on 2008-11-13
I found the same issue downloading from the Australian mirrors, ISO is corrupted IMO. Mine was failing at 54% at the install process. I downloaded from another AU mirror with the same result. I am sure its the download and not your hard disk or CD/DVD.

---

