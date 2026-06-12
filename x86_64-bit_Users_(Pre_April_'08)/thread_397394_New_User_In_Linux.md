---
title: "New User In Linux"
date: 2007-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammyd253 on 2007-03-30
Hey everyone, I'm new here and just have a few questions about using Ubuntu.  First off, here are my system specifications:

Asus A8N-SLI Deluxe Socket 939 Motherboard
AMD Athlon 64 X2 4400+ "Toledo Core"
2 GB PC3200 Corsair Value Select RAM
2 XFX Nvidia 6800 GS Video Cards Factory Overclocked in SLi
SB Live! 5.1 Sound Card
Western Digital 250GB SATA 3.0GB/s 16MB Cache Hard Drive
Samsung 18x SATA DVD +/- RW 2MB Cache

I post these specs because I want to know if any of my hardware will have compatibility issues with the most up-to-date, stable release of Ubuntu.

Along with this, I want to know if it is possible to take full advantage of my hardware using Linux.  By this, I mean I want to do the following:

-Ensure that Ubuntu takes full advantage of my CPU's 64-bit extensions
-Ensure that Ubuntu utilizes both CPU cores when it can
-Ensure that Ubuntu can use Cool n' Quiet with my CPU
-Ensure that Ubuntu utilizes SLi
-Ensure that Ubuntu can use my sound card properly (play audio), and also use the integrated Nvidia NIC

I know there is a lot of information here, and that it will probably require a large response.  However, feel free to post back yourself, or even point me in the direction of a few links that I can review myself.  I don't currently have Ubuntu available to me to play around with options, I am just trying to do my homework first.  I feel that if I'm going to attempt to make the move to Linux, I need to do it the right way.  Thanks in advance to all that want to help!

---

### Post by Kilz on 2007-03-30
> **sammyd253 said:**
> Hey everyone, I'm new here and just have a few questions about using Ubuntu.  First off, here are my system specifications:

Asus A8N-SLI Deluxe Socket 939 Motherboard
AMD Athlon 64 X2 4400+ "Toledo Core"
2 GB PC3200 Corsair Value Select RAM
2 XFX Nvidia 6800 GS Video Cards Factory Overclocked in SLi
SB Live! 5.1 Sound Card
Western Digital 250GB SATA 3.0GB/s 16MB Cache Hard Drive
Samsung 18x SATA DVD +/- RW 2MB Cache

I post these specs because I want to know if any of my hardware will have compatibility issues with the most up-to-date, stable release of Ubuntu.

Along with this, I want to know if it is possible to take full advantage of my hardware using Linux.  By this, I mean I want to do the following:

-Ensure that Ubuntu takes full advantage of my CPU's 64-bit extensions
-Ensure that Ubuntu utilizes both CPU cores when it can
-Ensure that Ubuntu can use Cool n' Quiet with my CPU
-Ensure that Ubuntu utilizes SLi
-Ensure that Ubuntu can use my sound card properly (play audio), and also use the integrated Nvidia NIC

I know there is a lot of information here, and that it will probably require a large response.  However, feel free to post back yourself, or even point me in the direction of a few links that I can review myself.  I don't currently have Ubuntu available to me to play around with options, I am just trying to do my homework first.  I feel that if I'm going to attempt to make the move to Linux, I need to do it the right way.  Thanks in advance to all that want to help!

I have the same processor as you, I am running Dapper drake 6.06 lts (long term support). All 64bit kernels have smp enabled, so they are set up for multicore processors. The 64bit version is set up to use your processor. Cool and clear is controlled by yout hardware and bois, not the operating system.
If you want to see if the rest of your hardware is compatible with linux, [check here.]("http://www.linuxcompatible.org/index.html")

---

### Post by sammyd253 on 2007-03-31
Thanks for the reply :)   I understand that Cool N' Quiet is controlled by the motherboard/BIOS settings, but I know that in Windows XP I have to set my power options to "Minimal Power Management" and also install a driver from AMD's site.  Are you telling me that if I have Cool N' Quiet enabled in my BIOS, Linux will take advantage of this feature automatically?  Or is there a driver I need to install?

---

### Post by Kilz on 2007-03-31
> **sammyd253 said:**
> Thanks for the reply :)   I understand that Cool N' Quiet is controlled by the motherboard/BIOS settings, but I know that in Windows XP I have to set my power options to "Minimal Power Management" and also install a driver from AMD's site.  Are you telling me that if I have Cool N' Quiet enabled in my BIOS, Linux will take advantage of this feature automatically?  Or is there a driver I need to install?

From what I understand linux, and specificly ubuntu will use this feature, its part of most modern 64bit kernels. The only problems I was able to find ,is [if you are overclocking it may not scale up]("http://ubuntuforums.org/showthread.php?p=1799054"). Phronix had a good [article on this feature ]("http://www.phoronix.com/scan.php?page=article&item=391&num=1")and said
"This driver is for use in conjunction with Linux 2.6.10+ kernels and cpuspeed or cpufreq. Most modern day Linux distributions should have no problems utilizing Cool 'n' Quiet with an out-of-the-box configuration on most supported systems."

---

