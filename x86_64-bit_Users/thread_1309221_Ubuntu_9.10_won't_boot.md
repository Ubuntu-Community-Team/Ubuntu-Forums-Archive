---
title: "Ubuntu 9.10 won't boot"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by 10098 on 2009-11-01
Hi everybody!
I have a Samsung R510 laptop (with an intel core 2 duo processor) which currently runs a 32-bit version of Linux Mint 7. I decided to give Ubuntu 9.10 a try, so I downloaded the version for 64-bit machines, burned the image tp a cd and tried to boot from it. 
When I select the "try ubuntu without installing it" option at the boot screen, a blank screen appears for a few seconds and then the laptop just restarts. 

Does anyone have any ideas about what could be wrong?

---

### Post by bilif on 2009-11-01
I have exactly, exactly, the same problem. 

I also have a samsung. Mine is a R560.

Hope someone can tell us something!!

---

### Post by 10098 on 2009-11-01
I have found a couple of workarounds for this:

1) Boot with mem=4096m - but this way the system sees only 3 gb of RAM, instead of 4. Fail.
2) Boot without acpi (acpi=off) - the system sees all the RAM, but all the acpi-related stuff is gone (can't even monitor battery status, which is unacceptable for a laptop) . Epic fail.

Any suggestions are highly appreciated :)

---

### Post by bilif on 2009-11-01
Have you tried any other 64bit version?

I've downloaded the 8.04 which I thought had to be to most stable version and it hasn't work either.

So even that I have a core 2 duo it might be possible that my laptop can't run a 64bit Ubuntu. dunno...

---

### Post by 10098 on 2009-11-01
Tried the 64-bit version of openSUSE 11.0 - still the same result, laptop reboots when trying to load the kernel.
I think I'll stick with the mem=4096m option, since that one lost gigabyte of RAM is not so critical anyway. Hope this issue will be resolved in further kernel versions.

P. S.:
Or maybe someone knows a way to partly disable ACPI so that we can have both 4 GB of RAM and a working battery monitor at the same time? :-)

---

### Post by sanderj on 2009-11-01
> **10098 said:**
> 

Does anyone have any ideas about what could be wrong?

Some more analysis:

- what happens when you boot non-GUI? So: press F4 or F6 (can't remember) and remove 'quiet splash' from the boot line. Watch closely what the last messages are before rebooting.

- is it a 64bit problem? So: what happens when you boot 32-bit 9.10?

- is it a kernel version problem? So: does it happen with 9.04 64-bit too?

---

### Post by bilif on 2009-11-02
Hey guys!!!

Here is the answer!!

[http://ubuntuforums.org/showthread.php?t=900285](http://ubuntuforums.org/showthread.php?t=900285)

but thanks you all!

---

### Post by bilif on 2009-11-03
I've updated the bios and now everything works fine :)

---

