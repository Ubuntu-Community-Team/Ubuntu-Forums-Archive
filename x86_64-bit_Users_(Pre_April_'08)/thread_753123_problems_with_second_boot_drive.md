---
title: "problems with second boot drive"
date: 2008-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by hotballz87 on 2008-04-12
ive been having problems with a second boot operating system on my slave hard drive.
only i can get my computer to read the drive is to boot my main as a cable select, and the slave as slave, but in the GRUB it still doesnt see any other OS except ubuntu on my master. any other jumper settings, my computer will not boot past the drive detection.

any suggestions?

ps im not sure where i should have posted this, i have ubuntu 64bit, with windows XPpro on slave drive

---

### Post by dcstar on 2008-04-12
> **hotballz87 said:**
> ive been having problems with a second boot operating system on my slave hard drive.
only i can get my computer to read the drive is to boot my main as a cable select, and the slave as slave, but in the GRUB it still doesnt see any other OS except ubuntu on my master. any other jumper settings, my computer will not boot past the drive detection.

any suggestions?

ps im not sure where i should have posted this, i have ubuntu 64bit, with windows XPpro on slave drive

Grub will not "see" anything that it did not detect on install - it is not a program that detects things that you add later.

If you want to add the other O/S to the grub menu, do a forum search and find a post that has instructions that you can understand.

---

