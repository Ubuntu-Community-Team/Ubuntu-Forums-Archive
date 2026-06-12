---
title: "Kernel panic : not syncing : attempted to kill init"
date: 2006-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by sayantan on 2006-04-05
Hi 

I recently recompiled the new 2.6.16.1 kernel on my system (AMD 64 2800+, 256 MB RAM).. and selected high memory support, as well as selected AMD 64 as the sub-architecture type ... 

however I wasn't able to boot the kernel .. getting the following kernel panic 

**17179576.000000 : Kernel panic : not syncing : attempted to kill init**

I then recompiled the kernel without the high memory support and also selected generic X86 support in the config ... also kept AMD 64 as the sub-architecture ....

However the kernel panic stays ... 

The kernel uncompresses itself ... and then the kernel panic ... 

I'm running the default ubuntu i386 on this computer ... 

I'm not sure if i've configured the kernel well ... I have the Gigabyte K8M800 MB.. with VIA VT82Cxxx Chipset .. again i've selected the specific chipset ... and also a generic chipset support..

I hope i've included enough info ... 

Please help..

PS : I'm not using SATA HDD ..

---

### Post by waster on 2006-04-05
Why are you compiling a kernel? Why do you have so little RAM??? Are you using Breezy or Dapper?

If you want extra kernel modules to support hardware, download the ubuntu kernel headers and compile new modules against them.

---

### Post by sayantan on 2006-04-05
Why??

I'm running a generic i386 kernel (Breezy 5.10), I wanted to run a kernel with specific AMD64 optimizations ... 

I just want a kernel that is specific to AMD64 ... 

unfortunately my ubuntu 64 (Breezy 5.10 ) was made un-bootable.. so I'm left with only one istallation of i386...

I guess I should be able to recompile and run a kernel ... no biggie ...

I want to know why I'm getting the kernel panic...

Of course having 256 MB RAM and compiling in high memory support does seem silly ... but that shouldn't stop the kernel from booting ... 

It is just adding support to high memory (I guess )

Correct  me if I'm wrong

Also I believe it has something to do with initrd... the recompiled kernel makes its own initrd ... can someone please give me some pointers to creating an initrd image, the manual doesn't help much ...

---

### Post by sayantan on 2006-04-05
Hi again,

After suspecting an issue with the initrd, i did the following, I reconfigured the kernel with Inital RAM Disk support ( I had it as a module, now I configured it in the kernel itself i.e Y instead of M) and got a different Kernel Panic ..

**Enforcing mode requested but no policy loaded. Halting now. **

Hmmmm..... 

There is a simple configuration issue that I'm missing... if only I could figure it out ... 

I'm posting the lspci of my machine ... 


00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0204
00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1204
00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2204
00:00.3 Host bridge: VIA Technologies, Inc. K8M800
00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4204
00:00.7 Host bridge: VIA Technologies, Inc. K8M800
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)


I hope this helps.... 
I've also tried  *make defconfig* .. the kernel will not give any panics ... and will not boot .... 

Please Help ...

---

### Post by skylark on 2006-04-06
[QUOTE=sayantan]
I'm running a generic i386 kernel (Breezy 5.10), I wanted to run a kernel with specific AMD64 optimizations ... 
I just want a kernel that is specific to AMD64 ... [/QUOTE]
I might be misreading your post. Are you trying to compile a 64-bit kernel on a i386 installation? If so it won't work since the rest of your system would still remain compiled for i386 not AMD64.

---

### Post by sayantan on 2006-04-06
I'm not trying a x86_64 (not  64 bit on i386)  but I'm trying to compile a x86 ( i386 with k8 ) amd64 as the subarchitecture .... 

yes it'll still be i386 but with amd64 or a k8 kernel ... it'll be a i386 kernel optimised for k8 ..

I think I can do it .. can't I ? 

correct me here ...

---

### Post by skylark on 2006-04-06
Try compiling the kernel with i686 as the sub-architecture. If it works (and sub-architecture AMD64 doesn't as you have discovered) then you have your answer.

---

### Post by sayantan on 2006-04-06
Pheeew ....... 

I have finally figured it out ...
The reason why I got the first panic is because I didn't have Initial RAM Disk support compiled in the kernel ( I had it as a module), it turns out a module won't work ... 

The solution for the second panic was as simple as adding the following in the menu.lst of GRUB 

kernel=/boot/vmlinuz-2.6.16.1 root=/dev/hda5 ro quiet _enforcing=0_

now enforcing=0 is very important here ... this is actually disabling any SELinux stuff and letting the kernel boot ... ( I don't really understand much of it myself) ... but hey I have a bootable 2.6.16.1 kernel !!!

So the lessons learnt from this exercise ... the linux kernel would panic if *some* of the drivers are not configured as kernel ( i.e if they are M instead of Y) ... so make sure atleast the following are compiled into the kernel..

1. Initial RAM disk support ( Drivers-->Block Devices)
2. ATA/ATAPI Support ( That includes the support to chipsets generic or otherwise ... as well as DMA)
3. The filesystems ... (ext2, ext3) 

All of the above needs to be compiled into the kernel not as a module ... 

this is what i got when i ran uname -a on my kernel .... 

**Linux localhost.localdomain 2.6.16.1 #16 PREEMPT Thu Apr 6 20:10:12 IST 2006 i686 athlon i386 GNU/Linux**

It uses AMD64 subarchitecture on i386 ...

check the #16 ... it is the number of times I've recompiled the kernel ... 
also PREEMPT here stands for a premptable kernel .. for a low latency desktop .... ( I dunno if this is a good idea, but yeah the kernel is a lot more responsive ) 

[This]("http://www.linuxjournal.com/article/5600") link explains the low latency thing on the kernel...

Thanks for all the help ...

---

