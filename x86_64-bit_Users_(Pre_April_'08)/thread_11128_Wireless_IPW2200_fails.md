---
title: "Wireless IPW2200 fails"
date: 2005-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by dJCL on 2005-01-14
OK, Ubuntu installed with few problems on the laptop, AMD64 works fine here.
I was sort of hoping that my problem in debian64 would have been solved, obviously not... same message:

ipw2200: dmaWaitSync Failed
ipw2200: Unable to load boot firmware
ipw2200: Unable to load firmware: 0xFFFFFFFF
ipw2200: Failed to up device


The driver loads fine, until I actually enable the device, it loads the first two firmware files and fails on the last one. The same thing happens if I enable it before boot, just failing during driver load then.

Others have had this problem, and I've seen no solution to it yet. Sometimes the card works for some poeple but those who get this, get it all the time.

I've tries a few things, compile the latest, try some patches to deal with 64 bit processors, verify my firmware files, even reviewing the code and modifying the dma wait time some to see what happens(nothing).

Anyone here have any luck?

JC

---

### Post by mlomker on 2005-08-26
I'm having the same problem.  I thought I'd try compiling the latest driver but I'm not a linux-whiz, so I'm not sure what to do about the various errors.

---

