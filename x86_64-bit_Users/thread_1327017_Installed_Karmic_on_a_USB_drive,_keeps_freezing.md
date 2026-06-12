---
title: "Installed Karmic on a USB drive, keeps freezing??"
date: 2009-11-15
forum: x86 64-bit Users
---

### Post by ram130 on 2009-11-15
I installed Karmic on a SanDisk Cruzer Micro 16GB drive..it takes along while to boot and every 1min it freezes and resume..is there any solution to this usb problem?


yes its a USB 2.0 and connected to a USB 2.0 port..

SYSTEM:

RAM: 4GB

CPU: AMD Athlon X2 64bit

OS: Karmic 32BIT

---

### Post by sanderj on 2009-11-15
I have the same experience:
- running Ubuntu live from a **live **USB key, it sometimes freezes; screen turns grey for a few moments
- running Ubuntu from an **installed **USB key (the normal procedure for installing to a real harddisk), it's even worse

I've not found a solution, so I'll watch this thread.

---

### Post by ram130 on 2009-11-15
Its stable, I've been running it for 15 hours now. So far the problem persists, especially when watching YouTube, just gets worst. Hope someone has a solution soon. Anyone know if it was like this older version of Ubuntu? Like 8.10

---

### Post by Yoast on 2009-11-15
have been running the 64Bit version from a USB stick for two days now. I have done one apt-get install -f after the installation of tvbrowser crashed.  Otherwise I have not had any issues. The experimental youtube-browser/64bit flash has not given me any issues. Firefox works smoothly with noscript, adblock+ etc. etc. I installed base from openoffic and did some playing about.  also istalled Avidemux, Audacity, VLC, and Gimp and Wine with Irfanview amd played around with some videos etc. a bit. No problem watsoever.  In feb  played around with 9.04 a bit and gave up because of problems (crashing/freezing etc.). I have even put Guarddog in and use Samba extensively (WD Myboookworld holds the videos, puics and music.). After every couple of installs of software I have rebooted, to make sure it was all stored without issues   So far, so good. I may start and install and run it on the Acer 9301 AWSMI (4Gb Ram and 70b disk) It does not recognise the built in webcam. OOtherwise evvrything seems to be working.  Look forward to hearing from others. USB-Boot runs from the same install as it ran 9.04 off. It is a cheap 4Gb Sancruzer.    I wonder how long the fun will last. The USB-stick cannot stay reliable forever.  On a couple of occasions the mic was not recognized properly, and ubuntu asked if I Wanted to remove the drivers, but after rebooting it di not give any issues.   > **ram130 said:**
> Its stable, I've been running it for 15 hours now. So far the problem persists, especially when watching YouTube, just gets worst. Hope someone has a solution soon. Anyone know if it was like this older version of Ubuntu? Like 8.10

---

### Post by efflandt on 2009-11-15
I just tried various USB devices on Toshiba A105 Intel dual core 1.6 GHz laptop 1 GB RAM, timing approximately from BIOS password entry and quickly hitting enter for boot menus. There are slight differences in boot times, but no noticeable lag after booting for any of them.

32-bit 9.10 live on 4 GB HP USB stick w/2.1 GB casper-rw
45 sec to color flash
65 sec to gnome

64-bit 9.10 live on 2 GB Lexar microSD w/1.1 GB casper-rw
65 sec color splash
75 sec to gnome

64-bit 9.10 regular system on part of WD Passport HD
50 sec color spash
65 sec to login
15+ sec to gnome

32-bit 9.10 on internal drive
35 sec color spash
45 sec login
15-20 sec to gnome depending upon background image

Not sure what to use for a benchmark, but they all work fine full screen on hulu.com (64-bit systems use 64-bit flash).  You might try disabling Visual Effects in System, Preferences, Appearance to see if that resolves glitches.

---

### Post by ram130 on 2009-11-15
Damn you guys are lucky. I have no external 3.5 hard drive, just a regular small 16Gb flash drive.  Booting for me takes 2min from grub, after that it start freezes when ever it reads something. When I look at the drive it is blinking, so it leads me to wonder, is the usb drive that slow? After 1min of waiting, it comes back. Almost as if I'm runing from a live cd! It is most noticeable when I'm typing text like now, freezing every 1min. Also this is a full blown install from a live cd. I've tried the create start up disk option from another install, same results. Its my first time doing this on a flash drive so I'm bit confused. Oh and regular ubuntu on the internal experiences no problems.

---

### Post by efflandt on 2009-11-16
If you are running a normal system on USB flash, you should look at using **tmpfs** for the /tmp file system, so temp files are in RAM (which you have plenty of) to avoid writing every change in state to USB.  The **/etc/fstab** entry for that on live CD on USB is:

```
tmpfs /tmp tmpfs nosuid,nodev 0 0
```But something else is peculiar about the Cruzer.  I installed 64-bit 9.10 live on a 2 GB Cruzer micro I had been using on my BluRay player.  Gparted only showed 1 partition on it (sdb1) yet Ubuntu kept auto mounting "U3 System" even after sdb1 was formatted, safely removed and reinserted. Booting from the Cruzer was noticeably slower than others above.  Although, everything appeared to be responsive once it booted:

63 sec to color splash
120 sec (2 minutes) to gnome

/var/log/messages showed the 2 GB Cruzer taking 109 seconds to get to the same apparent boot completion point that 2 GB microSD did in around 60 seconds (54-62 sec).  Check your dmesg or /var/log/messages for things related to sr devices or other delays during boot.

Maybe U3 for file encryption is hardware ROM, because it continues to show up as an sr device auto mounted as iso9660 regardless of any partitioning/formatting of the Cruzer.  If yours has U3, I suspect that is causing your lag.

---

