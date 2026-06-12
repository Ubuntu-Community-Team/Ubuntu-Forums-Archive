---
title: "shutdown problem in Ubuntu 5.10 64 bit"
date: 2005-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmarkvillanueva on 2005-12-24
i tried ubuntu live. works well but the only problem is that my machine doesn't shutdown after logging off. it terminate X and leave the screen blank. I have to press the power button to turn it off.

i tried installing the install cd and gives the same problem. how do i fix this :( thanks

---

### Post by mmarkvillanueva on 2005-12-24
i've also tried adding noapic nolapic and also tried noacpi nolacpi in /boot/grub/menu.lst but it still didn't solve the problem :(

---

### Post by ruudiculus on 2005-12-26
You may try the command 'poweroff' in the command line instead of doing it graphically. This doesn't solve your problem, I know, but it may work this way :)

---

### Post by mmarkvillanueva on 2006-01-19
i've tried to run Ubuntu 5.14 live on a friend's pc and no problem occurs with regards to shutting down.

i've installed ubuntu in my new pc. there are other problems that occur like no sound. i assume that the version of ubuntu has no yet any support on my hardware. i'll try to download draper or wait for the release of a new version. maybe it will fix the problem

---

### Post by ccm030 on 2006-01-19
I have the same issue.  Bugzilla seems to point in the direction of upgrading your kernel to daper drake.  So I have two general questions.

1. Has anyone actually resolved this problem yet in Breezy?

2. If not, can you just do and apt-get to upgrade the kernel or is it a complete upgrade daper drake?


Thanks for any help you can give this noob
ccm030

---

