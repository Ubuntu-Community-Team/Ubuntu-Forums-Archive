---
title: "Kernel Panic - Kubutu-64|feisty fawn"
date: 2007-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Swooper on 2007-09-02
Dear Ladies and Chaps,
 
I've currently got a situation where, after the bios splash screen, Kubuntu stalls with these details:

[COLOR="Red"]Loading please wait...
[         10.173033] Kernel Panic - not syncing = Attempted to kill init.
[         10.173064]   *blicking cursor*


Kernel Alive
kernel direct mapping tables to 100000000 @ 8000-d000[/COLOR]

 So, the points of note that relate to this are:
  - The numbers change, such as 10.608997 and 10.609629, etc
 - Im running Kubuntu 64bit edition  Feisty Fawn with the latest updates as of 2 days ago
 - the choices from the boot menu are 2.6.20-16, 2.6.20-15, mem test and windows Xp pro. Of these, 20-16 and its recovery mode do not work, 20-15 does work, memtest shows no errors over 3 pases.
 - the machine specs are: AMD 3200+, 1 gb ddr2 dual-channel RAM, 250gb Sata drive, dvd combo drive, with the asus m2n-mx motherboard.
 - Prior to kernel panic, i had just installed apache 2, php5 and mysql, and there was a report of a package/install error. I had a similar thing where i attempted to install java and flash via apt package installer. 

 Otherwise, i wasnt sure whether to post this in the newbie section or not, and couldnt find any otehr posts that didnt relate to install issues

many thanks,
 Swooper

---

### Post by Claus7 on 2007-09-03
Hallo,

mostly this seems to be a hardware failure. If I were in your shoes first I would check hardware cables, cards e.t.c. and see if everthing is ok. In my situation the memory card had a lot of dust. After I removed it everything was ok.

I hope this helps,
Regards!

---

### Post by stevecs on 2007-09-03
If one version of kernel works and the other doesn't then it's probably _NOT_ hardware related (or at least directly, ie, there may be a bug/work-around in a driver for a particular chipset that's causing you grief).

I've run into _LOTS_ of problems w/ Fiesty 64bit's 2.6.20-15 & -16 kernels with my MB here had to either fall back to 6.10 or upgrade to a newer kernel which I did.   If it's working fine w/ -15 then go ahead and use that.    You could also just boot into -15, grab the current 2.6.22-6 kernel from [www.kernel.org](www.kernel.org) and try compiling a new one which if it's your first time may be more involved than what you want.

---

### Post by Swooper on 2007-09-05
Ah, thankyou for the ideas.

 Would waiting it out in -15 until the next update work?  I think i will just format the lil' beastie and see hwo that goes....

cheers

---

### Post by Cappy on 2007-09-05
Have you tried adding boot params
```

noapic nolapic
```
onto the grub boot line?

There is a page on how to edit grub before booting into Ubuntu here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

