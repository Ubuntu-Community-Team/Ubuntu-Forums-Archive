---
title: "Hardy randomly hangs during boot"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by knattlhuber on 2008-08-22
I just installed 64-bit Hardy on a new HP Pavilion with Intel Quad Core and nVIDIA GeForce 9500.
When starting the computer, Ubuntu freezes shortly after the GRUB menu when the splash screen comes up and the progress bar bounces to and fro. This happens mostly when restarting the computer, but sometimes also following a clean start.
Does anybody have any suggestions for diagnosing the problem? I have tried to do a verbose boot by pressing Alt+F1 but the splash screen always freezes before the verbose mode kicks in.

---

### Post by mrsteveman1 on 2008-08-22
So it's not grub that freezes but definitely the boot process after the kernel is read into memory.

You could disable the splash stuff by removing it from the boot line in grub, then you should be able to see what it's doing. I think the relevant options are splash and quiet.

---

### Post by knattlhuber on 2008-08-22
Thanks, Steve.

I removed the splash screen and then had to reboot five times until I got through. The boot process got stuck at different points each time. I took 'screenshots' with my camera of the four failed attempts (see attachment).

Any suggestions what's wrong?

It's worth noting that I had the same boot problem with a similar HP Pavilion that I had purchased a couple of days ago and returned to the store because the fan was too loud.

---

### Post by mrsteveman1 on 2008-08-23
I don't see any real errors. Try booting with the insane safe mode options Suse uses:

> vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single

If that doesn't help, try removing any extra hardware in the machine one at a time to see if any of them are causing problems.

---

### Post by knattlhuber on 2008-08-23
Thanks again, Steve.
With the restricted options, the freezes became less frequent but would still happen.
As the wireless and the TV card were also giving me problems, I took advantage of BestBuy's return policy today... It's a pity as it was a nice computer and HP so far has worked well with Ubuntu for me.
I'm probably gonna file a bug report. Others apparently had the same problem with the 64-bit version: [http://ubuntuforums.org/showthread.php?t=872166]("http://ubuntuforums.org/showthread.php?t=872166")

_Edit:_ Seems that this is a known bug. E.g.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/172563]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/172563")

---

