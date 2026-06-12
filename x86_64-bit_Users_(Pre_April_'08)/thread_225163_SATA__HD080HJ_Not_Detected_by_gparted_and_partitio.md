---
title: "SATA  HD080HJ Not Detected by gparted and partition editor ..."
date: 2006-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by savimonty on 2006-07-29
People,

I recently purchased a new amd64 and tried to install Dapper-amd64 on it. I used both the Desktop version and the Alternate version!
Also tried using the Dapper-i386. Even tried using Breezy amd64!

**For all of the above :**
* It did not start gparted from Espresso. It used to just get stuck.
* Also, from the alternate installation partition editor did not start and the screen remained blue.

My SATA HDD is **Samsung HD080HJ**

When I used the traditional (NOT SATA) hard disk, everything came back to normal! And things worked as usual.

SOS!
Thanks a lot in advance,
Savio Monteiro.

---

### Post by Ares Drake on 2006-07-29
My guess is, that not the SATA disk itself is the problem, but probably the onboard SATA controller on your mainboard. Maybe you have more than one onboard controller and can switch?

---

### Post by savimonty on 2006-07-29
Ares,

How do I find out whether there are 2 controllers or one??
Where do I look for it on the mainboard?

Also, WIndows 2000 works perfectly fine which I want to get rid of ASAP ...!

Savio.

---

### Post by Ares Drake on 2006-07-29
> **savimonty said:**
> How do I find out whether there are 2 controllers or one?? Where do I look for it on the mainboard?
If there are 2 controllers, the are maybe colored differently. Or have a look in your mainboard's manual. There you might also find what SATA controller you have and search this forum for its name to find a HowTo around the installation problems

Good luck!

---

### Post by savimonty on 2006-07-31
Well the manual just referred to the followoing lines! And I couldn't find 2 controllers with different colors!

BTW here is what the manual has to say about the SATA support!

"The mother board supports the serial ATA technology through the Serial ATA interfaces and the VIA VT8251 Southbridge link. The serial ATA 2 specs provides twice the bandwidth of the current SATA products with a host of new features including native command queueing (NCQ), power mgmt (PM), implementation algorithm and HOT SWAP. SATA allows for thinner more flexibke cables with lower pin count, reduced voltage requirement and data tranfer rates of upto 150MBPS for SATA1 and 300MBPS for SATA2"!

:confused:  :rolleyes:  :x :?: 

Thanks a lot!
Savio.

---

### Post by savimonty on 2006-07-31
BTW take a look at this!!

[http://www.ubuntuforums.org/showthread.php?t=196171](http://www.ubuntuforums.org/showthread.php?t=196171)

This is most probably the problem .... the drivers!!

I too have an VT8251 controller and ASUS A8V-MX motherboard!!

Phew ,,... gotta compile a kernel ... or else switch to FreeBSD!

---

