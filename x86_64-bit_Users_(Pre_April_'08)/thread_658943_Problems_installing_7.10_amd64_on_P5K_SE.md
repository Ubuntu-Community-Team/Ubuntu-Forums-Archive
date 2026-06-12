---
title: "Problems installing 7.10 amd64 on P5K SE"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by kubusiowaty on 2008-01-05
Hi there,

I'm having some serious problem installing Gutsy (desktop) on my machine.
My specs are:
Processor: Intel Core 2 Duo E6550
Motherboard: Asus P5K SE (P35 Intel chipset)
Memory: GeIL 2 x 512 MB DDR2 800MHz
Graphics: Radeon HD3850 256MB
Hard Disk: Seagate 250GB 16MB cache

After installing Gutsy, if I try to update any packages, some of them are always broken (no matter how many times downloaded). Dpkg exits, giving an information about broken package file. Tried using apt-get install -f to solve errors but it did not help. I've read many posts it seems that nobody else had that problem.
Found some suggestions about a broken hard disk. Checked mine. He's in good shape no bad blocks or something else.
Memory run's fine too. Tested with memtest. No errors while I work on MS Windows.

In my installation of Ubuntu some files are always corrupted (media I'm installing from is ok - checked it, I've tried downloading and burning again, but the same error occurs). For example: /var/dpkg/available always has some strange chars inside which interrupt the install process.
Tried cleaning available and rebuilding it. Did not work. Errors return.
Some schema files are also always corrupted.
I've tried to check if it was maybe a wrong module for disk controller so I've added piix to my initial ramdisk.
Did not help.
Tried also changing my network card but this also did not help.

It seems that while installing something always goes wrong but I'm not sure what.
I'm using EXT3 filesystem.

Can anyone help?

Thank You,
James

---

### Post by muhsinzubeir on 2008-01-13
mmh got the same mobo here...but im struggling getting gentoo on it.En most cd's fail   along the way when i boot...

---

### Post by cubicsilver on 2008-01-14
My friend has this board and we had to set the sata to compatibility in the bios to get xp to install.

It was a setting called sata configuration and I changed it from enhanced to compatible and this seemed to fix the problem.   

It was a western digital hard drive too if that helps.

---

### Post by wilstar on 2008-01-14
hi,
i have your mobo asus p5kse and ubuntu 7.10 64 bit.
At the first time on installing ubuntu 7.10 64bit, i had many problems, not only with ubuntu (fedora, knoppix, mandriva).
Eventually, i added acpi=off at the boot line and then ubuntu worked fine, but the pc didn't shut off itself.
Then, i changed the acpi=off boot line with nolapic and the pc worked fine. there wasn't any boot problems and the pc shut down tiself.
So, i tried to modify bios parameters. i've changed the "apic" (or similar voice) menu from disable to enable and then the pc start working fine without boot parameters.
Now i have no boot parameters and ubuntu 7.10 works great.

wilstar

---

