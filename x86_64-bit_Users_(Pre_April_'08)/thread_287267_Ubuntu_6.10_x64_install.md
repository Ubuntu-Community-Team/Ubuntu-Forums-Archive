---
title: "Ubuntu 6.10 x64 install"
date: 2006-10-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by zog on 2006-10-28
Hi Everone,

I am attempting to install the latest Ubuntu 6.10 x64 desktop version on a Dell Dimension C521.  I've downloaded the software from 
[http://ftp.osuosl.org/pub/ubuntu/edgy/ubuntu-6.10-desktop-amd64.iso](http://ftp.osuosl.org/pub/ubuntu/edgy/ubuntu-6.10-desktop-amd64.iso)

I burned the ISO image to a CD and begin the installation.  The Kernel unzip and the Ubuntu splash screen displays.  However, it gets stuck at this point and I can't seem to get to actually install setups.  Has anyone ever seen this?  Are my aspirations of x64 Ubuntu OS on a new Del AMD system just wishful thinking?

Any and all suggestions glady accepted.



The hardware specs for this system are as follows:

Video:        256MB ATI Radeon X1300 Pro 
CPU:          Athlon64 x2 5000
Hard Drive:   SATA II 320 GB drive
Memory:       4GB DDR2 SDRAM at 533MHz
Keyboard:     USB keyboard
Mouse:        USB Mouse

Thanks.

zog

---

### Post by cotcot on 2006-10-28
Try the alternate install CD. I am running 6.10 on an AMD64X2 and saw no problems till now. I installed a month ago dapper with the install CD on it and saw the same problems as you do. I then reinstalled with the alternate install CD. That worked. Today I upgraded dapper to edgy without any problems. I have 2 SATA and an nvidia graphics card.

---

### Post by zog on 2006-10-28
Hi Cotcot,

I tried the alternate iso and it gives me the following error while booting the kernel:

i8042: can't read CTR while initializing.

Any thoughts.

I'm moving on the server iso and see if I have any luck there.

zog

---

### Post by taurus on 2006-10-28
I am going to move this over to the AMD64 section since you would get more helps out there...

---

### Post by kuja on 2006-10-29
Well, assuming the CD is free of defects, it is likely an issue with the motherboard, probably something to do with APIC. These threads seem to deal with it: [http://ubuntuforums.org/showthread.php?t=198839](http://ubuntuforums.org/showthread.php?t=198839)
[http://ubuntuforums.org/showthread.php?t=245055](http://ubuntuforums.org/showthread.php?t=245055)

In short, I think the answer was to boot with "noapic maxcpus=2"

---

### Post by magicfab on 2007-01-24
A similar problem with a Dell E521 was solved by a recent BIOS upgrade from Dell.

See:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

