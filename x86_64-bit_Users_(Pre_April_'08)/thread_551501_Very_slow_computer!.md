---
title: "Very slow computer!"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by cableroy on 2007-09-15
Hi 

I hope this is the correct thread. This is my hardware:

Amd 64 x2 dual core 4400+, 2 gb memory, 2 X Nvidia 7800GTX, Sata 10K rpm disk. 

This should be "fast" computer but it isn't, surfing with either firefox or opera feels slow, change/open/close tabs, loading pages,scrolling is so slow, switch tabs can take up to 4-5 sec,even typing lags! Ii know this is not correct and wounder what can cause this? firefox and opera is 64 bit also, i do not run beryl/compiz, and its 7.04. Nvidia driver is  NVIDIA-Linux-x86_64-100.14.11dmesg says this:


[   59.587520] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)
[   59.587524] powernow-k8: MP systems not supported by PSB BIOS structure
[   59.587557] powernow-k8: MP systems not supported by PSB BIOS structure

i don't know if that has anything to do with it.

---

### Post by Kilz on 2007-09-15
> **cableroy said:**
> Hi 

I hope this is the correct thread. This is my hardware:

Amd 64 x2 dual core 4400+, 2 gb memory, 2 X Nvidia 7800GTX, Sata 10K rpm disk. 

This should be "fast" computer but it isn't, surfing with either firefox or opera feels slow, change/open/close tabs, loading pages,scrolling is so slow, switch tabs can take up to 4-5 sec,even typing lags! Ii know this is not correct and wounder what can cause this? firefox and opera is 64 bit also, i do not run beryl/compiz, and its 7.04. Nvidia driver is  NVIDIA-Linux-x86_64-100.14.11dmesg says this:


[   59.587520] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)
[   59.587524] powernow-k8: MP systems not supported by PSB BIOS structure
[   59.587557] powernow-k8: MP systems not supported by PSB BIOS structure

i don't know if that has anything to do with it.

Is this a laptop? Is it pluged in or running off the battery?

---

### Post by tgalati4 on 2007-09-15
I've read elsewhere to edit your /etc/hosts.

Remove the 127.0.1.1 entry

---

### Post by John.Michael.Kane on 2007-09-15
> **cableroy said:**
> Hi 

I hope this is the correct thread. This is my hardware:

Amd 64 x2 dual core 4400+, 2 gb memory, 2 X Nvidia 7800GTX, Sata 10K rpm disk. 

This should be "fast" computer but it isn't, surfing with either firefox or opera feels slow, change/open/close tabs, loading pages,scrolling is so slow, switch tabs can take up to 4-5 sec,even typing lags! Ii know this is not correct and wounder what can cause this? firefox and opera is 64 bit also, i do not run beryl/compiz, and its 7.04. Nvidia driver is  NVIDIA-Linux-x86_64-100.14.11dmesg says this:


[   59.587520] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)
[   59.587524] powernow-k8: MP systems not supported by PSB BIOS structure
[   59.587557] Preparing the kernel MP systems not supported by PSB BIOS structure

i don't know if that has anything to do with it.

The errors mean your mainboard possibly has a broken DSDT, and lacks ACPI _PSS, and the PSB table does not support MP=multi processors.

Two options come to mind.
Upgrading the bio Which should fix the issue provided the board maker implemented the proper support.

Moving to a newer kernel.You can try the method below for moving to the gutsy kernel, and see if that fixes the issue.
[Howto: Simple kernel upgrade ]("http://ubuntuforums.org/showthread.php?t=511974&highlight=gutsy")

---

### Post by cableroy on 2007-09-15
> **Kilz said:**
> Is this a laptop? Is it pluged in or running off the battery?

Hehe i would like to see a laptop with dual 7800GTX cards :) No its a workstation.

---

### Post by cableroy on 2007-09-15
Hmm take a look at my dmesg, [   27.411202] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

Attacthed full dmesg.

cableroy@ws1:~$ uname -r
2.6.22-11-generic


Not any better...

---

### Post by John.Michael.Kane on 2007-09-15
> **cableroy said:**
> Hmm take a look at my dmesg, [   27.411202] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

Attacthed full dmesg.

First I would see if there is a bios update for the board in question.  

Second would be  trying the guide for moving over to the gutsy kernel to see if that helps. 

Third is disabling cool n quiet in the bios

Theres many factors, and your going to work through them one at a time to narrow the issue down.

---

### Post by cableroy on 2007-09-16
> **SD-Plissken said:**
> First I would see if there is a bios update for the board in question.  

Second would be  trying the guide for moving over to the gutsy kernel to see if that helps. 

Third is disabling cool n quiet in the bios

Theres many factors, and your going to work through them one at a time to narrow the issue down.

OK

Bios up2date
cool'n'quiet was off in bios
Running gutsy kernel 2.6.22-11-generic

My mobo is DFI Lanparty Nf4 sli...

---

