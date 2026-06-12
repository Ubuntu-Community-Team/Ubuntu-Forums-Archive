---
title: "FIX Asus K8V Deluxe SE AMD64 DMA freezes"
date: 2004-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmatrix on 2004-10-13
I have been running Ubuntu on my brand new AMD64 hardware since Warty preview release came out. Everything has been working great but one small issue. 

Here is my hardware:

ASUS K8V Deluxe SE
1 gig DDR
Nvidia Ti4200
onboard sound and NIC
Ubuntu Warty upgraded to the latest kernel. linux-amd64-k8

I was experiencing odd little freezes of around 10 - 20 secs of duration during heavy load. This was not really apparent until I really pushed the system by having a dozen torrents open, dvd burning, ogg playing, web surfing, copy stuff from IDE cdroms. It was really starting to get annoying, so I started to look thru /var/log/syslog. This is what I found:

Oct 12 08:26:25 localhost kernel: hda: dma_timer_expiry: dma status == 0x24
Oct 12 08:26:35 localhost kernel: hda: DMA interrupt recovery
Oct 12 08:26:35 localhost kernel: hda: lost interrupt

I do not use the SATA yet just the IDE. I have 4 IDE devices on here that were working fine in my old Athlon 2000. Here are more:

Oct 12 08:27:38 localhost kernel: hdc: lost interrupt
Oct 12 08:28:23 localhost kernel: hdb: lost interrupt

I would get these errors about my cdrom devices under heavy load even when not using these devices. Very odd. The system would freeze until the IDE device was reset. I have not lost any data yet or noticed any corruption, yet...

So I tried the usual disable ACPI and APIC to see if that resolved any issues. In my case disabling APIC did nothing and disabling ACPI made it so my system would not boot. It would freeze loading the orinoco_pci driver.

After a bit of googling I came across a post of a Fedora user with the same motherboard having the same issues. He said to put this in the Grub.conf file at the end of the kernel line (/boot/grub/menu.lst on Ubuntu):

noapic pci=usepirqmask

Having placed this in my menu.lst file and rebooting my heavy load IDE DMA reset issues are gone. 

I hope this will help any other AMD64 users on this motherboard having this issue as it is quite annoying. From posts I have read this also affects SATA devices too.

Is there any way to make Ubuntu detect this motherboard and setup grub properly so other users will not have this issue?

As well every time the kernel updates my menu.lst file is overwritten. Is there any way to have this set every time the kernel updates?

---

### Post by judas_iscariote on 2004-10-22
just a little question..

this is a BIOS issue?
a boot loader issue?
a kernel issue?


somebody tried updating the BIOS?

---

### Post by K6-III on 2004-10-22
Good thing I swapped this board for a Chaintech VNF3-250 a while ago...

---

### Post by jdong on 2004-10-24
From the description, it's clearly a kernel issue, not really to do with Ubuntu in specific.

Try unpacking a SuSE AMD64 kernel, or a Gentoo one, and see if they have the problem. Perhaps they'd have a patch for these issues.


I have this mobo, but in 32-bit mode.

---

### Post by Baloo on 2004-10-25
[QUOTE=jdong]From the description, it's clearly a kernel issue, not really to do with Ubuntu in specific.

Try unpacking a SuSE AMD64 kernel, or a Gentoo one, and see if they have the problem. Perhaps they'd have a patch for these issues.


I have this mobo, but in 32-bit mode.[/QUOTE]
 I'll be installing ubuntu tonight on my K8V so I'll keep an eye out for any DMA issues.

---

### Post by dmatrix on 2004-10-26
Baloo - I would be interested to hear if you have the same problems.

I have no idea if this is a motherboard bios issue or a kernel issue. I have not had enough time to test other things out.

My motherboard has the 1003 bios and I have read the 1004 bios has the same issue and it is possibly a problem with the 2.6.8.1 kernel. I guess testing a 2.6.9 or 2.6.7 kernel would be a good test.

This motherboard does not have the DMA timeout issues once I put in those options into grub and it takes a beating without a single slow down of freeze. As well a 32 bit Ubuntu on the same hardware does not have this problem, but I cannot 100% confirm this as I do not have a 32 bit Ubuntu installed on my hardware right now.

---

### Post by mistic on 2005-01-01
it IS a mobo-problem


i've had it with a PC of a friend of mine, exactly the same MOBO....


it worked fine with Suse 9.1 UNTILL i did an upgrade of the system... then even grub started hanging....

I'm gonna try a fix now i found at the fedora-forums, will let you guys know....

---

### Post by ahyden on 2005-01-01
I have this motherboard but my harddrives are fine. But it has happened to the cdrom while copying from it. Maybe it had trouble reading from the CD or we have the same problem? Well if it happens again I'm going to add the kernel option you specified and see if that fixes it. Thanks for sharing

---

### Post by matyoka on 2005-03-16
I have same mobo. just k8v. My problem solved when I removed the ATAPI cd and dvd-roms.
I donno why, but it works without freeze. I have scsi cd-roms and with them the system doesn't freeze. who knows that? LOL. :D 
 \\:D/ 
i'm happy.

---

### Post by jdong on 2005-03-16
[QUOTE=mistic]it IS a mobo-problem[/QUOTE]

Doesn't necessarily mean it's a mobo problem -- it could just be a kernel bug specific to this mobo...

Hoary has 2.6.10 -- does this happen with the Hoary kernel?

---

### Post by dmatrix on 2005-03-17
This problem does appear to be fixed on the latest Hoary 2.6.10 kernels. Still running the original BIOS with no grub modifications and no DMA freezes yet.

---

### Post by wmcbrine on 2005-03-17
Now if only powernow-k8 would work... Apparently it's fixed in 2.6.11.

Or I could just upgrade the BIOS. Ah.

---

### Post by Pse on 2005-03-17
Well, I have a K8V-X on Hoary64 and haven't had a problem so far. I still haven't used the optical disks...but I guess they should work. Powernow-k8 worked fine, too. BTW, Hoary is on a SATA drive, but I access other devices which are IDE and there hasn't been any problem. Kernel 2.6.10-k8.

---

### Post by benguin on 2005-03-18
[QUOTE=Pse]Well, I have a K8V-X on Hoary64 and haven't had a problem so far. I still haven't used the optical disks...but I guess they should work. Powernow-k8 worked fine, too. BTW, Hoary is on a SATA drive, but I access other devices which are IDE and there hasn't been any problem. Kernel 2.6.10-k8.[/QUOTE]
 Hi there
I have t the ASUS K8V deluxe MoBo with an AMD64 3200+ (Socket 939) running hoary 64 and stock ubuntu 2.6.10-5. I got 512 Megs of dual channel DDR ram, antique nvidia geForce MX2 400 AGP 4x card. Powernow works, never had DMA/Drive-slowdown issues. lm_sensors works too.

-J-

---

