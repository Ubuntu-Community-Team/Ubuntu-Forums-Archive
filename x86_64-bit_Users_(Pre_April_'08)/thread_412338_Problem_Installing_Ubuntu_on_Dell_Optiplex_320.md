---
title: "Problem Installing Ubuntu on Dell Optiplex 320"
date: 2007-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by lungten on 2007-04-18
:guitar: Hi Everyone,
I am new to Ubuntu but have been using other Linux distros like Red Hat, FC and FreeBSD for some time.

I've been trying to load Ubuntu 6.10 on my new Dell Computer but running into problems. The specs of my computer is

Dell Optiplex 320 with Pentium D (3.4 GHz), 512 MB RAM, 128 MB ATI X1300 Video card.

Firstly, i tried ubuntu_6.10-desktop-i386 and the kernel failed to load. The error message was something like:
[xxxx:xxx] PCI: Could not allocate resource for device 1 at 0000:xx:xxxx
The 'x' are nombers.

Then I tried ubuntu_6.10 for AMD 64-bit. The kernel loaded but stopped at a point where it says 'mounting root file system'.

I need some help to proceed with the installation. I already have Win XP installed. I want to make a dual-boot my PC.

Thanks.

---

### Post by amohanty on 2007-04-18
Two things come to mind (a lot could be wrong but only two pop up right now :)

1. Some peice of hardware is non-functional
2. The CD you downloaded and burnt was bad. 

For 1. check your bios or windows device manager for those yellow question marks.
For 2. Use the check media option before starting the live version.

AM

---

### Post by mfa81 on 2007-04-19
Search the forums... there are many issues about install linux on dell optiplex 320, there are at least two things you must do to get ubuntu running on your dell

1 - append pci=nomsi to kernel on boot loader
2 - use lilo instead of grub

there are one topic that explains how to do that in more details, just search

---

### Post by marshcast on 2007-04-20
Yep! a fine machinme the Dell Optiplex 320. I blame Dell Entirely - but maybe that's just me being prejudiced (Hehehe...)

Anyways - I have just bought 7, and guess what - they have problems...

Neither Dapper OR Edgy will install onto these systems.

Feisty will - but it won't boot unless you use the LILO bootloader instead of grub.

You need to install from the Feisty live CD.

try to boot (Feisty was released officially today, so it may be sorted)

if not boot again from the live CD and follow Stacemans fantastic howto in this thread:

[http://ubuntuforums.org/showthread.php?t=409345](http://ubuntuforums.org/showthread.php?t=409345)

that should get you up and running ;)

Good luck!

---

