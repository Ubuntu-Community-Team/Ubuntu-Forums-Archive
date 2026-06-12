---
title: "Has anybody been able to install dapper beta on a beige G3?"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by nkbj on 2006-04-28
Has anybody been able to install dapper beta on a beige G3?

When I try BootX seems to be unable to start the kernel (no error messages though). I have no problems installing breezy on the system.

Regards,
Niels Kristian

---

### Post by davygravy on 2006-04-28
[QUOTE=nkbj]When I try BootX seems to be unable to start the kernel (no error messages though). I have no problems installing breezy on the system.
[/QUOTE]


I could not get it to install on a Beige G3.  I tried maybe 5 or 6 times, and got nowhere.  

I **didn't** try upgrading Breezy (worked fine on my Beige box) using apt-get .  IIRC, if I had done this, I would have had to somehow have gotten a copy of the Dapper kernel over on the Mac OS 9 partition for BootX to see.   Well, I never got that far.

I have Dapper beta running very nicely on my Blue & White, w/ no problems whatsoever.

Good luck. (maybe I'll try again once Dapper is official)

---

### Post by nkbj on 2006-04-28
Did you see the same symptoms (BootX going nowhere)?

It seems to me that the dapper kernel somehow doesn't like old world macs. :-(

Regards,
Niels Kristian

---

### Post by davygravy on 2006-04-29
IIRC, neither the LiveCD nor the InstallerCD would work for me in Dapper (at that point it was Flight 5).  BootX would leave on it's journey (whatever that means) and I would see a dark screen, I think.  Some chattering from the hard drive, then nothing...silence.  That's all.

I'd agree, it doesn't seem to like the OldWorlds.

---

### Post by virgule on 2006-04-29
Me neither. I seam to me they dropped support for "legacy bootloader" in the kernel or somethin'.

---

### Post by nkbj on 2006-04-30
I found the bug had been reported on launchpad. It has since been confirmed and severity changed from normal to major. Still hope I guess. :-)

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30273](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30273)

Regards,
Niels Kristian

---

