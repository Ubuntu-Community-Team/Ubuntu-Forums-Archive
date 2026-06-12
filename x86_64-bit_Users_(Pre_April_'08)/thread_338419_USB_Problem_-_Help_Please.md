---
title: "USB Problem - Help Please"
date: 2007-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by mike00 on 2007-01-14
Hi,
I'm quite new to Linux as well as new to Ubuntu, I have managed to have a set-up where I can dual boot windows and Ubuntu. Thanks mostly to the help on this forum :) I have managed to get most of my hardware etc working.

Unfortunately I am having trouble when USB devices are connected. If I leave something connected to my computer and try to boot up - the system will hang.
These USB devices consist of a wireless adaptor + card reader + usb memory stick -- These all work fine if I connect them after boot up. (Boot up still freezes regardless of which ones are connected)

If I view the system messages as it boots It gets to " ohci_hcd ... new usb bus registered, assigned bus number 1  "   then it gets stuck, with the disk activity light on. 

Could anyone tell me how I could fix this?

Thanks in advance

---

### Post by kleeman on 2007-01-14
Sounds like a kernel problem to me. Try compiling the latest stable kernel (2.6.19.2) using the instructions here:

[http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel)

---

### Post by mike00 on 2007-01-15
Thanks for the response, I actually just updated the bios and this seems to have fixed the problem.

Mike

---

