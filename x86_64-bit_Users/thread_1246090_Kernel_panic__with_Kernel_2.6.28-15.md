---
title: "Kernel panic  with Kernel 2.6.28-15"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by rslamet on 2009-08-21
Hi,

Just updated my kernel from 2.6.28-14 to 2.6.28-15.  But when rebooted the system crashed with Kernel panic.  I am running AMD 64bit.  Any reasons for this?  This also happens with 2.6.28-13.

Regards
Rolly

---

### Post by wickerman1413 on 2009-08-22
I had a similar problem some time ago and it turned out to be an issue with the version of BIOS I was running - highly inconvenient as the BIOS update was only available for Windows, which meant I had to install Windose to a USB memory stick to update the firmware :-(

---

### Post by rslamet on 2009-08-23
Thanks,  I had  a similar bios problem with 2.6.28-13 and upgraded the Bios.  The frequency of freezing was somehow reduced but not totaly eliminated.  It tends to crash and freeze when I am about to hand in a major piece of work.  Very annoying.  But when I upgraded to 2.6.28-14 the problem disappear completely.  Now with 2.6.28-15 it tends to crash during the boot process ending with the caps lock and scroll lock lights fashing and a frozen screen and keyboard.  So now I better stay put with 2.6.28-14 until the next upgrade.

I am just wandering that when they upgraded the kernel whether they have missed something in the code. :confused:

---

### Post by silvagroup on 2009-09-10
I have had problems with my hp dv since since upgrading to 2.6.28-15. No sound and no wifi radio. From googling seems to be a finiky kernel. Starnge thing it works fine on my three desktops desktops.
Moral of the story if it works yippy if it doesn't down grade till it (maybe) gets worked out in the next release.

---

### Post by Daaz40 on 2009-09-26
i am also geting the same error "Kernel Panic"  when I use Kernel 2.6.28-15.
Everything works fine when I use Kernel 2.6.28-11
I am using Intel Core2Duo

---

### Post by silvagroup on 2009-09-26
Try try a complete removal and reinstall and see if that does anything.
I still can not get any of the 2.6.8-* kernels to work on my hp dv5 to work properly.
I have no kernel panics or freezes, but I loose wifi and sound, very strange.
Again if the removal doesn't work then downgrade to the 2.6.27-* kernels.

---

### Post by Malta paul on 2009-09-27
I had the same problem with Kernel 2.6.28-15, I then tried 2.6.30 which works good on my system.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by silvagroup on 2009-10-23
Wondering how this has worked out for everyone.
I don't have problems with kernel panics I just have problems with wifi and audio with any kernel above 2.6.27-11 on my HP DV5 laptop.
There seems to be a terrible regression. I upgraded bios from HP and problems where worse.

---

