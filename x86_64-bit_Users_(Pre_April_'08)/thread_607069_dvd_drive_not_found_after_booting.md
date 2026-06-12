---
title: "dvd drive not found after booting"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrq1 on 2007-11-08
hi

i want to install kubuntu amd64 gutsy on my new asus p5gc with a core2 duo;
after burning the image on a dvd+r it shows the blue bootscreen and after booting, i get dropped to the initramfs interpreter; 

after booting without "splash" and "silent" it looks like my dvd-drive is not detected; its a old ide drive and it is on the same bus with the ide harddisk, which is detected;
i dont think, that the drive is the cause, it boots the disk very fast and works on windows too;

after this, i tried all bios settings (compatibility & enhanced mode) but that does not change anything; the ide-cd kernel module is not loaded too;

what can i try next?

---

### Post by dcstar on 2007-11-08
> **mrq1 said:**
> hi

i want to install kubuntu amd64 gutsy on my new asus p5gc with a core2 duo;
after burning the image on a dvd+r it shows the blue bootscreen and after booting, i get dropped to the initramfs interpreter; 

after booting without "splash" and "silent" it looks like my dvd-drive is not detected; its a old ide drive and it is on the same bus with the ide harddisk, which is detected;
i dont think, that the drive is the cause, it boots the disk very fast and works on windows too;

after this, i tried all bios settings (compatibility & enhanced mode) but that does not change anything; the ide-cd kernel module is not loaded too;

what can i try next?

Verify that the jumpers on the DVD are set up to "Slave", and the hard drive jumpers are set to "Master" (and not "Single Drive").

If it still doesn't work, and you have a spare IDE cable, try moving the DVD to the secondary IDE channel and configure it as a Master device.

---

