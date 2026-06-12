---
title: "Installing dual boot on raid 0"
date: 2005-09-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by emenny81 on 2005-09-24
hey guys I have an asus a8v-e deluxe and I want to install ubuntu on it, right now I have windows and I have it partitioned in a way that I have 100 gigs left for the linux instalation, thing is that when I try to install ubuntu it wants to re format both of the drives, is there any way I can install in the free space that I designated for it ??? thanks

---

### Post by mlomker on 2005-09-26
That's the default.  You can select to do manual partitioning.

---

### Post by Rounan on 2005-09-28
Installing to a raid0 isn't quite so simple as that. Dual-booting with both OS's in raid0 may be impossible.

Are you using your motherboard's RAID functionality? If so, does Ubuntu detect only one big disk? If this is so, you're in luck! Your motherboard is smart and the solution is probably what mlonker said - just do a manual partition of the "disk" that is actually your motherboard-managed RAID0 volume.

More likely is that Ubuntu is detecting two disks with only one partition each. This is because Windows and Linux handle RAID very, very differently. Linux is able to RAID together partitions using the kernel, while Windows will only do this with entire disks and needs 3rd party drivers. With Windows, what's actually going on is there's a special driver handling the communications with your mobo's RAID controller, and that driver presents a single disk to the OS that is actually your RAID volume. Problem is that the driver is (most likely) closed-source Windows-only, and it won't work on only part of the disk - leaving no space for Ubuntu.

I've tried several RAID setups on a couple different PCI "RAID" cards, and have never been able to get both OSes on RAID. If Windows is in RAID, it's monopolizing all of both disks. Linux will share, so you can boot Linux in RAID and have Windows on a single partition - or you could have a Windows partition on each disk, one for system one for data. But no RAID coexistence.

One final caveat: Ubuntu may need you to make a seperate boot partition in a RAID1 rather than a RAID0 setup. This is because the bootloader needs to load the kernel, and it's not mart enough to read a striped volume. Because RAID1 is just two crbon-copies, it can read form it the same as a normal partition. /boot need only be 32-64MB.

If this didn't help, please provide more information and we'll go from there.

--Rounan

---

### Post by mlomker on 2005-09-28
> I've tried several RAID setups on a couple different PCI "RAID" cards, and have never been able to get both OSes on RAID. If Windows is in RAID, it's monopolizing all of both disks.

Ah, yeah...I must have read that post too quickly.  The so-called RAID on motherboards is really nothing more than a BIOS setting that depends upon a software driver being loaded on the operating system...and few have drivers for linux.

You'd have to step-up to a hardware RAID (adaptec, compaq, or that one SATA RAID board that's out there).  They cost $100-3000 but they look like one big disk to the operating system and are many times faster than software RAID.

---

### Post by Rounan on 2005-09-28
Hardware RAID is usually reserved for server-grade operations in RAID5. For a RAID0 config, hardware RAID isn't appreciably faster than software, and it's many many times as expensive.

I'm currently running a ubuntu media server with an Athlon XP 1400+ and 5 120GB disks in RAID5, and it never chews more than 2-5% CPU for the RAID operations. Because the load average of the server is below 0.2, that's more than OK. Desktops would probably have load averages under that (unless you're running Gentoo and fanatical about your updates).

If you've got an always-on mission-critical database server, then a hardware RAID setup is well worth the effort and expense for the added speed and security. For your desktop machine, you'll just blow a lot of money for an imperceptible performance gain. The unfortunate state of dual-boot desktop RAID is that you're buggered and restricted to running only 1 OS in RAID. Only thing to recommend is that you send a letter to the mobo manufacturer asking them to release a linux driver - which in practise means an open source driver, since any other time the driver is only released for version xx.xxx of RedHat. And that's been done to death.

Cheers,
Rounan

---

