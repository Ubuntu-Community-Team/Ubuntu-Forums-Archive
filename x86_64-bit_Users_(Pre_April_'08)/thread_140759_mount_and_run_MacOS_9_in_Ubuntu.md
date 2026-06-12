---
title: "mount and run MacOS 9 in Ubuntu?"
date: 2006-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by geuis on 2006-03-06
I'm doing this for the technical challenge mainly.

I've got a cd image of MacOS 9.1. So far, I've been able to mount the HFS drive and I can explore the disk.

I understand that I have to copy the ROM file from the disk as part of the steps.

Is there a general guide of steps to actually be able to mount and install MacOS 9 and run it under Ubuntu?

Thanks,

Geuis

---

### Post by engla on 2006-03-06
You need [mac-on-linux]("http://maconlinux.org/"), it can do stuff like this [it's said].

I've installed in on my breezy install and I can run OS X in a window from my hfs+ partition.

There are a few *caveats*
Mac-on-linux (mol) is in the repostitories, but that package doesn't seem to work; try it if you want to. I had to compile all of mol from the source package on project page.
Documentation doesn't seem to be very hot, and it looks like it was some time since there last was a community around the project.

And lastly; I run OS X in mol without problems. I did a very small test to see if I could run OS9, it didn't work at the first try and I left it at that... so you would have to try harder, perhaps.

There are options, perhaps. I've heard about QEMU, a cool emulation project.
Perhpas you could use that to emulate a mac and run OS9 in that, emulation would be pretty much slower than the native execution of mol though...

---

### Post by Ptero-4 on 2006-03-07
Hi. Mol do work. But ubuntu doesn't include the mol kernel modules. There's a place on the web with the mol kernel modules for pretty much every ubuntu version. It's something with Peter, google can for sure find it. Also as for Qemu. No it currently can't run MacOS. It only have basic PPC CPU emulation, it doesn't yet emulate the rest of the hardware required to run OS9/X.

---

### Post by ssam on 2006-03-08
there is a MOL howto [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto)

i think kernel modules will be included in dapper

---

### Post by engla on 2006-03-08
[QUOTE=ssam]there is a MOL howto [https://wiki.ubuntu.com/MacOnLinuxHowto](https://wiki.ubuntu.com/MacOnLinuxHowto)

i think kernel modules will be included in dapper[/QUOTE]
These are great news. Some machead must be involved with ubuntu development, we'll get bcm43xx and mol, and perhaps even more!

---

