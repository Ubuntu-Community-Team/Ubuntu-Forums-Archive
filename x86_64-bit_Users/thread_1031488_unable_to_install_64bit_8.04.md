---
title: "unable to install 64bit 8.04"
date: 2009-01-05
forum: x86 64-bit Users
---

### Post by jimmy2975 on 2009-01-05
Hi,

I have problems installing 64bit 8.04 on my box. I have installed 32-bit (ubuntu, centos, fedora....) and 64 bit (fedora 6,8) in the past w/o any problems. 

I also managed to install 64 bit 8.04 2 days back with safe graphics mode ( w/o this the install would not get past loading the gnome display). After this install, I updated the system and rebooted. The system was ok until next day when I turned on the system and the boot-up would hang for ever! I enabled splash and found sometimes it hangs when gnome is loading and sometimes it hangs with the error "PCI hardware error" (this corresponds to the sky marvell yukon ethernet driver). Ever since I have not been able to get past the hang either with live CD, recevery mode or by disabling the LAN in the BIOS. I have tried disabling acpi, apic, nothin! All 4 sticks of RAM are good. Passes memtest!

This system dual boots with XP. Everthing in XP is ok (so this is not a hardware issue).

I enabled memory mapping to use the 4 gigs and here is the PC spec

ASUS vintage AH-1 barebone (socket 939)
AMD dual core Opteron proc
ATI XPress 200 chipset
Uli southbrige
Ati xpress 300 onboard video(shared memory)
4 GB RAM
2 sata disks (1 internal, 1 external), 1 pata disk, 1 external USB disk, DVD/CD writer

Could this be a kernel issue?
Any help/suggestions would be great.
Thanks
Regards
Jimmy

---

### Post by Paul S on 2009-01-05
> **jimmy2975 said:**
> 
I have problems installing 64bit 8.04 on my box.

Could you be using an old (8.04) buggy cd?  If you're using an old disk, toss it out and download and try 8.04.1 instead.

regards,

---

### Post by jimmy2975 on 2009-01-05
The first one that i burnt onto a cd didnt work and so I tried it again and still the same. They were both 8.04.

---

### Post by bford16 on 2009-01-06
It would really help if we could see the boot log and kernel log for your system. I realize this will be difficult if you cannot boot to a gui.  Maybe you would have better success with an Alternate install CD, or with an Intrepid Live CD.

Also,the way you described the problem made me think of loose (poorly connected) hardware. Did you check for that?

---

### Post by vgrisham on 2009-01-06
I had this problem with Gutsy and it wound up being a bad downloaded cd. Make sure you check the mdsum after burning. I downloaded three bad ones in a row last year!

---

### Post by hyperdude111 on 2009-01-06
I had the same problem and even tho the md5 sum was right it never worked on a host of cd's. I tried a new download and cd and it was perfect.

---

