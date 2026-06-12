---
title: "help"
date: 2005-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by cimnik029 on 2005-11-13
i just installed Ubuntu 5.10, and i have the following problem. The GRUB loader freezes. LILO wont install. This is what I see when I boot

Loading GRUB stage 1.5
_

And it freezes there... anyone got any idea how to get over this? I'm dual booting with windows xp, but i get the same problem without a second os on the harddrive.

would a SATA harddrive be the problem? i was told before the it might be that I have to flash my bios. is this a logical answer? :confused: 

thanks

if it helps, iv had this problem with every linux disto iv tried: some previos ubuntu versions and SUSE 9.3

---

### Post by kelsey23 on 2005-11-13
Ahhh, I have seen this problem before with someone I installed Ubuntu GNU/Linux on their computer. I actually have LILO installed, but I think either would work OK. The soultion for the problem was quite simple: When GRUB stops loading, turn off the monitor and then turn it back on :-)

Seriously, that was the problem.

---

### Post by cimnik029 on 2005-11-13
thanks for the tip, but that didnt work...:(

---

### Post by cimnik029 on 2005-11-13
flashing bios didnt work either... anyone got any ideas?

---

### Post by willoc on 2005-11-13
if you have multiple hard drives, switch the boot order.  this worked for me.

---

### Post by cimnik029 on 2005-11-13
i only have one harddrive... a sata one... but would having my cd drive on primary ide cause some problems?

---

