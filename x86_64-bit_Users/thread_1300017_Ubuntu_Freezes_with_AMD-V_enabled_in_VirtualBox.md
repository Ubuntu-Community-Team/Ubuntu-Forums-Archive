---
title: "Ubuntu Freezes with AMD-V enabled in VirtualBox"
date: 2009-10-24
forum: x86 64-bit Users
---

### Post by xtjacob on 2009-10-24
Hello all, I have ubuntu 9.04 64-bit on a Acer Aspire 4530, and if I enable AMD-V in VirtualBox and run it it completely freezes the system and I have to do a cold restart. It works fine if I turn it off. I have done some research, and tried adding nohz=off to the end of my kernel list in menu.lst, and it still freezes. Please help!

---

### Post by JohnH on 2009-10-24
Yep you are right. 

Virtual Box is not happy on 64 bit from my use of it. Locks up all the time. I had to shut down Nested Paging, and PAE/NX to get things to run at all. On one OS I had to run it on ONE processor before it would work!

It always locks up or loses the pointer or some other problem.

It has not been happy on the 64 bit machine. What a pity.

John

---

### Post by bedtime_with_the_bear on 2009-10-25
> **xtjacob said:**
> Hello all, I have ubuntu 9.04 64-bit on a Acer Aspire 4530, and if I enable AMD-V in VirtualBox and run it it completely freezes the system and I have to do a cold restart. It works fine if I turn it off. I have done some research, and tried adding nohz=off to the end of my kernel list in menu.lst, and it still freezes. Please help!

You should make sure you don't have another virtualisation product installed that may be using AMD-V. KVM is a perfect example of this. It starts a service that uses AMD-V, but if you then start another piece of software that uses AMD-V, it will lock the machine hard. The basic problem is that you can only have one software service accessing AMD-V at once.

---

### Post by xtjacob on 2009-10-25
Nope I only have VirtualBox installed. Other users have reported it too. [http://forums.virtualbox.org/viewtopic.php?f=7&t=17617&start=0](http://forums.virtualbox.org/viewtopic.php?f=7&t=17617&start=0)
Also this is not the open source edition.

---

### Post by tymek666 on 2009-10-25
Which version of the VBox are you using? 
I'm runnig virtualized WinXP under Mint 7 64-bit with VB 3.04 and it works great with AMD-V enabled. The issue you mentioned was common in 2.x version of VBox.

---

### Post by xtjacob on 2009-10-25
3.0.8

---

### Post by tymek666 on 2009-10-25
Well, it's strange. I've recently setup two VBox 3.0.6 installations on two different AMD systems running Mint 7 64-bit. In both cases guest system was WinXP with Guest Additions installed and worked very fast and stable with all possible hardware accelerations enabled. System spec are as follow:
1. AMD Phenom II x3 BE 720, 4 gb ram, Gigabyte motherboard with 785 chipset.
2. AMD Athlon II x4, 8 gb ram and the same mobo.

---

### Post by xtjacob on 2009-10-26
My processor is a AMD Athlon X2, and has a phoenix BIOS, but does not have the virtualization option listed in the BIOS.

---

### Post by tymek666 on 2009-10-26
> **xtjacob said:**
>  but does not have the virtualization option listed in the BIOS.

This could be a serious problem. My machines have this option enabled in BIOS.

---

### Post by xtjacob on 2009-10-26
When I start the VM it does not freeze right away. For example, when I boot up Ubuntu 9.10 with it on it doesn't freeze until after I choose an option.

---

### Post by brianrardin on 2009-11-03
I have the same issue with Ubuntu 9.10 x64 and VirtualBox 3.0.8 on Dell D630 with Core2Duo 2Ghz and 4GB of RAM. Locks up only when VirtualBox is running any guest OS VM. When it locks up, the scroll lock and caps lock LEDs flash together with no way to power off unless I hold the power button. Nothing in syslog is jumping out as the problem either...

---

