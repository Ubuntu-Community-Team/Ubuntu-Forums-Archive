---
title: "Clock is running crazy."
date: 2008-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rogers on 2008-03-18
My clock is losing HOURS a day, like 3-4 hours a day.  It's nuts.  Brand new MOBO running P35 chipset and a Quadcore 6600.

What's strange is (i dual boot occasionally for weird things that need to run in windows) I booted into windows and my time was fine.  How screwed up is that?  It's not losing any time.

Ubuntu 7.10 all the updates.
        GA-EP35-DS3R
        Quadcore 6600
        4 GIGS OF RAM

Any ideas would be great.  :confused:

---

### Post by munkyeetr on 2008-03-18
Check your Date and Time settings (*right-click* on the clock and choose** Adjust Date & Time**)

Make sure **Configuration** is set to *Manual*

---

### Post by Rogers on 2008-03-19
> **munkyeetr said:**
> Check your Date and Time settings (*right-click* on the clock and choose** Adjust Date & Time**)

Make sure **Configuration** is set to *Manual*

Yep.  I got pissed and flashed the bios, now linux won't boot but windows works fine :-/

---

### Post by munkyeetr on 2008-03-19
> **Rogers said:**
> Yep.  I got pissed and flashed the bios, now linux won't boot but windows works fine :-/

Probably a little excessive. Generally it is not recommended to flash a BIOS except to add some functionality that the BIOS update provides, or as a last resort to fix a problem that *may* be solved by the update.

Anyway, when you get Linux up and running again, if you're having the same issue, check the clock settings like I said in the last post. ;)

---

### Post by Rogers on 2008-03-20
Fixed it, added  acpi=no   my kernel boot params and it fixed the clock and the boot issue. :guitar:

---

