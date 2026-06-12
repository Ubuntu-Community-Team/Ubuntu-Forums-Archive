---
title: "Two Hard Drives, Ubuntu &amp; Win XP, select at startup"
date: 2006-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by endokrin on 2006-05-18
Hi,

After installing Ubuntu on my laptop a while ago, I decided I was comfortable enough with it to install it on the desktop I use for work.

I would like to have two hard drives.  Ubuntu will be installed on one and Win XP on the other.

I would like Ubuntu to be the default, and I assume I set this up in BIOS???

Is there some way to make a menu pop up at boot up to select the hard drive and thus the OS?
Even better, can I have Ubuntu be the default, but if I want Win XP to boot, I can hold down a certain key or key combination at boot up and the computer will switch to the Win XP hard drive?

---

### Post by tonyr on 2006-05-18
This kind of installation is called  Dual-Boot, as you probably know.  If Windows
is already installed (and it should be installed first if it is not),  the Ubuntu Install
process will find it and know about both drives and their partitions, and will ask you
where you want to install Ubuntu.  It will generate a boot selection menu
that will always be displayed first for you to select which OS you want.  I think
it makes Ubuntu the default OS, but there are ways to manage that by
editing the GRUB menu  in /boot/grub/menu.list.  Go to the Ubuntu Wiki
Installation page [here]("https://wiki.ubuntu.com/Installation") and look for the link to [WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

---

### Post by endokrin on 2006-05-18
Silly me...

I thought dual boot was when both Operating Systems were installed on the same hard drive.

Thanks, and thanks for the link.

---

### Post by vincentb on 2006-05-19
[QUOTE=endokrin]Silly me...

I thought dual boot was when both Operating Systems were installed on the same hard drive.

Thanks, and thanks for the link.[/QUOTE]

In fact, 'dual boot' is valid when you have two operating systems on the same computer, regardless of the number of disks that are installed in the computer. For instance, on my laptop, I have XP - Ubuntu - FC4 on the same hard disk and use Grub to select on which OS I want to boot. On an other PC, I have several Linux spread over several disks.

It is however correct to state that you should install XP first, then add other Linux distros (and for sure not the reverse order which is often problematic).

If you install Ubuntu on a PC with several disks, make also sure to install XP on the 'first disk' (for instance, on the disk connected to SATA1 port). Otherwise, you'll have problems later on (believe me) at the boot (non system disk ...., for instance)

Hope this helps,

Vincent

---

### Post by rplantz on 2006-05-20
[QUOTE=vincentb]
If you install Ubuntu on a PC with several disks, make also sure to install XP on the 'first disk' (for instance, on the disk connected to SATA1 port). Otherwise, you'll have problems later on (believe me) at the boot (non system disk ...., for instance)
[/QUOTE]

Multiple disks can get interesting. I have two disks, one is SATA and the other IDE. My BIOS is set up to boot first from the SATA disk, but it sees the IDE on channel 1 and the SATA on channel 2. I have grub installed on the SATA, but once grub is running, it sees the SATA as the second disk. I originally installed the IDE disk so I could put Dapper on it to play with before switching. I got it to work at one point. But I finally installed Dapper on my main (SATA) disk and the IDE disk is being ignored for now. One of these days I will try to figure it all out.

Meanwhile, grub apparently sees my "second" (SATA) disk as the first one until the system has booted. Then it sees my "first" (IDE) disk as the first one. Almost as bad as a human. :)

---

