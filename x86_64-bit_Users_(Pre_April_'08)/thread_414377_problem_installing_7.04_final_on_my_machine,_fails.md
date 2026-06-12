---
title: "problem installing 7.04 final on my machine, fails on load."
date: 2007-04-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by mangar on 2007-04-19
Hi all,
  machine spec: cpu: core duo e6600,motherboard:msi p965 neo, hdd: sata, western digital (320gb, 16mb cache).
 partitions:
 1. primary: 270gb, windows vista 64, ntfs.
 2. secondary: 50gb, reserved for fiesty, unallocated.
  
 problem: 
  when trying to install fesity, after choosing "install", the loading of the live-cd fails while showing the splash
  screen, and shows the busybox login, with "failed to initialized tty" error.

 --note: when an external usb hdd was attached to machine, the live cd loaded as usual, but when choosing
 install partition, the partitioner showed only the usb drive, and not the sata drive.

i'm currently stuck using vista.. please set me free!
thanks in advance!  
  
p.s:
 the problem is probably not the cd's,
 i've downloaded and burnt them twice: once on my laptop, under linux, using k3b,
 and the second time on the main machine, under vista, using ImgBurn

---

### Post by mangar on 2007-04-20
additional note:
when disabling ioapic in the bios, the live-cd loads, but the mouse response is very slow, and the sata harddrive is not recognized.

thanks in advance!

---

### Post by dabl on 2007-04-20
you don't want to hear thisk, and I hate to say it ....

I would direct my suspicion at the motherboard and that P965 chipset.  If you search this forum and Kubuntu Forum on "965", you're probably going to learn more about what works and what doesn't -- I'm no expert on it, but I have seen multiple reports of trouble installing (K)Ubuntu on it.  Luckily, I have the P975, which seems to be a happy combinate.

Sorry ...

---

### Post by Syirrus on 2007-04-20
> **dabl said:**
> you don't want to hear thisk, and I hate to say it ....

I would direct my suspicion at the motherboard and that P965 chipset.  If you search this forum and Kubuntu Forum on "965", you're probably going to learn more about what works and what doesn't -- I'm no expert on it, but I have seen multiple reports of trouble installing (K)Ubuntu on it.  Luckily, I have the P975, which seems to be a happy combinate.

Sorry ...

Then the same must be true for the 975X chipset because I'm experiencing the same problem.  In fact, I get the same error using the 32bit install disk.

---

### Post by dabl on 2007-04-20
Hmmmmm .... well, perhaps the motherboard/BIOS is also involved, then.  My board is an Intel D975XBX, running a Core 2 Extreme CPU.  I've installed both Edgy and Feisty Kubuntu 32-bit, and Feisty Ubuntu 64-bit, and not had any installation issues of this type.  Here are some examples of problems from the Kubuntu forum that seem to center on that Intel P965:

[http://kubuntuforums.net/forums/index.php?topic=11347.0](http://kubuntuforums.net/forums/index.php?topic=11347.0)

[http://kubuntuforums.net/forums/index.php?topic=3081134.0](http://kubuntuforums.net/forums/index.php?topic=3081134.0)

[http://kubuntuforums.net/forums/index.php?topic=10323.0](http://kubuntuforums.net/forums/index.php?topic=10323.0)

I dunno -- maybe it's just circumstantial that they're P965s -- kinda hard to prove one way or the other.

:(

---

### Post by mangar on 2007-04-27
sorry for the late reply, but i've solved the problem:

1. during install, pass the following arguments: all-generic-ide irqpoll (using f6)
2. when booting for the first time, use the grub menu and add: irqpoll, remove splash from the default boot options.

---

