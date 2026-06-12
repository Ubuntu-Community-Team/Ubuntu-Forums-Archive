---
title: "Hardy 64 Bit with ATI Graphics Card"
date: 2008-07-23
forum: x86 64-bit Users
---

### Post by Euphorion on 2008-07-23
Hallo

I have a Fujitsu XI-2550 Laptop with ATI HD2700 graphics and 4GB of Memory. I am currently running Hardy 32 Bit on this machine, the ATI Driver flgrx in conjunction with the Catalyst Control Center works very well.

I do quite a bit of video rendering, and the posts in this forum show that I can expect a significant improvement in performance by using the 64 Bit version.

Before I reinstall (a terrible must, the thought that I will have to setup all my favorite software again is daunting), have all the issues regarding ATI Graphics mentioned in various Posts in this Forum been resolved?

The other big issue is running Firefox with extensions, I would like to use Firefox 3 with at least Foxmarks, currently I use the following extensions Dictionary Switcher, German Dictionary, Down them all, Foxmarks, Image Toolbar, PDF Download and Print/Print Preview and would ideally like to continue to use them in the 64 Bit Version.

Has anyone out there installed Hardy 64 Bit on a Fujitsu XI-2550 with ATI and got the flgrx driver to work?

Thanks in advance

---

### Post by tuxxy on 2008-07-23
I have run 64 bit Hardy successfully on an ATI X1250 & X1650 chips, both are compatible and run ok, although now upgraded to nVidia as I had some minor problems with the ATI drivers such as not being able to view 3D flawlessly and a few other graphical issues.

Good Luck

---

### Post by Yellow Pasque on 2008-07-23
If you have enough free disk space, you can resize your partition(s) and do a dual-boot until you verify everything works properly. You can reuse your swap partition and /home partition if you have a separate one.

---

### Post by kingtaurus on 2008-07-23
The current MTRR issue is still open (as of the last hardy kernel upgrade).

---

### Post by Euphorion on 2008-07-24
Hallo Temüjin and Kingtaurus

You both have given me decisive advice, thank you. The first being that ATI Issues are still ongoing and especially the MTRR issues, which I have read about in this forum and must say are above my Linux capabilities. Firefox Flash and Java I will be able to fix with the help of this Forum.

I too have decided to install the 64 Bit Version on a separate Partition in order to do a soft migration. One very important info is that I can reuse the swap partition. One question that concerns me with this aspect is the placement of Grub with regard to EasyBCD.

My Laptop is currently setup as follows: On the first hard disk 2 Partitions a Vista recovery and Vista. On the second hard disk, the first partition a common data pool, the second partition Ubuntu 32bit, the third partition Ubuntu swap. Grub is installed in the Ubuntu partition and NOT in the MBR of the second hard disk. Booting is done using EasyBCD.

When setting up Ubuntu 64 Bit I assume that I can install as for 32 Bit with following modifications, I do not create a new swap partition but somehow tell Ubuntu to use the existing swap partition and place Grub for the 64 Bit partition in its partition (once again not in the MBR of the 2nd hard disk and on no account in the 32 Bit Ubuntu partition) so as to avoid a collision with the 32 bit Grub. I then reconfigure EasyBCD to include the 64 Bit Ubuntu.

Do you think that the above mentioned method is feasible ?

Thanks in advance

---

### Post by soxs on 2008-07-24
> **Euphorion said:**
> Hallo Temüjin and Kingtaurus

You both have given me decisive advice, thank you. The first being that ATI Issues are still ongoing and especially the MTRR issues, which I have read about in this forum and must say are above my Linux capabilities. Firefox Flash and Java I will be able to fix with the help of this Forum.

I too have decided to install the 64 Bit Version on a separate Partition in order to do a soft migration. One very important info is that I can reuse the swap partition. One question that concerns me with this aspect is the placement of Grub with regard to EasyBCD.

My Laptop is currently setup as follows: On the first hard disk 2 Partitions a Vista recovery and Vista. On the second hard disk, the first partition a common data pool, the second partition Ubuntu 32bit, the third partition Ubuntu swap. Grub is installed in the Ubuntu partition and NOT in the MBR of the second hard disk. Booting is done using EasyBCD.

When setting up Ubuntu 64 Bit I assume that I can install as for 32 Bit with following modifications, I do not create a new swap partition but somehow tell Ubuntu to use the existing swap partition and place Grub for the 64 Bit partition in its partition (once again not in the MBR of the 2nd hard disk and on no account in the 32 Bit Ubuntu partition) so as to avoid a collision with the 32 bit Grub. I then reconfigure EasyBCD to include the 64 Bit Ubuntu.

Do you think that the above mentioned method is feasible ?

Thanks in advance

A. Don't highchack threads.
B.. Use chainloader +1 (in case of grub) like this:
Add this to your primary boot device grub (/boot/grub/menu.lst):
```
title           Whatever you would like to name it
root            (hd1,0) #the boot partition of the second system
chainloader     +1
```

---

### Post by Yellow Pasque on 2008-07-24
> A. Don't highchack threads.
How can he hijack his own thread (which only has a few posts and hasn't moved on to another topic)? Am I missing something?

---

### Post by Yellow Pasque on 2008-07-24
Sorry, double post (it's been doing that to me a lot lately even though I only hit the button ONCE).

---

### Post by soxs on 2008-07-24
> **Temüjin said:**
> How can he hijack his own thread (which only has a few posts and hasn't moved on to another topic)? Am I missing something?

lol, ok.. I am sorry, that was my fault, I didn't get that he was the thread author. i am sorry again.

---

### Post by Euphorion on 2008-07-25
By nature I am not a hijacker but a peaceful person. The apologies are accepted and no harm done. The answer from Sox was very interesting and led me to download the Grub documentation and I have learnt a lot. Thanks for the stimulus.

---

