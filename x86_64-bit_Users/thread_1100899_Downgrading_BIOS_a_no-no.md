---
title: "Downgrading BIOS a no-no?"
date: 2009-03-19
forum: x86 64-bit Users
---

### Post by GARoss on 2009-03-19
Well, you can do research but it's difficult to get all the info you need.
I'm running Ubuntu AMD64 with Core Duo E6600 & DG965RY MB. The BIOS is fully updated (v1755). I install 8gb (previously 2gb) which is the max according to Intel support for this MB. Install the RAM & now it boots extremely slow. According to what I've read on the net, there were no RAM problems with an older BIOS v1669.

Intel has the old version available. Is installing an older BIOS a no-no?

---

### Post by Slim Odds on 2009-03-19
> **GARoss said:**
> Intel has the old version available. Is installing an older BIOS a no-no?

Shouldn't be a problem.... it's not like it's got any external dependencies

---

### Post by GARoss on 2009-03-20
Well this is weird.
After the additional 8 gb of RAM was installed it took 90 seconds to boot to the OS selection screen (Dual boot computer) which would normally take only take 10 seconds with old RAM. This got me searching the internet looking for a solution & one was to install an older BIOS version. 
But, before doing that, I started the computer a few more times & got normal boot-time results with all 8 gb of RAM installed. 
There must be a sort of orientation process the mother board goes through when it detects new hardware.
No need to change BIOS after all. Learn something new everyday!:popcorn:

---

### Post by lukjad on 2009-03-20
@GARoss  

You really shouldn't play around with the BIOS unless you really, really, really need to and really know what you are doing. Horrible things have been known to happen. ;)

---

### Post by mpsii on 2009-03-20
Normally, when changing RAM, there should be a message that the amount of  system RAM changed (coming from after POST). However, if this message is non-existent or disabled, then the first boot after new RAM sends some motherboards into a check of the ram which can take a bit.

This is why I like to set my BIOS to not show a splash screen on boot, but detailed messages, so I can see what it is doing.

---

