---
title: "64 bit reduces bandwidth?"
date: 2009-08-11
forum: x86 64-bit Users
---

### Post by Philotus on 2009-08-11
Morning All,

I'm running 64 bit jaunty quite happily on an acer 5735. I'm running a 2.6.29 kernel to eliminate the freezes, and have followed the guides on this forum to install flash, java and the rest. Other than occasional firefox and sound hiccups I really like the speed of the 64 bit system, (especially on R, JAGS and OpenBUGS) however I have a reduced bandwidth problem and its got me stumped.

I am triple booting this system and under vista and 32-bit jaunty I can directly connect to my cable modem by ethernet cable and get 17-18 Mb/s (I pay for 20, so that ain't bad). By wireless router the connection is usually between 12 and 15 Mb/s (which makes sense due to interference and a crappy router). 

Despite all this, for some bizarre reason my 64 bit jaunty system gets consistently between 1 and 3.5Mb/s whether by ethernet cable or wireless.

I've disabled ipv6 in firefox and by adding the 'ipv6.disable=1' to my grub entry for the 2.6.29 kernel.
I've also manually changed the rate option in iwconfig to read 54Mb/s instead of 1Mb/s, but still no luck.

Any ideas?
My guess is that the wireless driver and ethernet driver are not appropriately configured in the 64 bit kernel, but are correct in the 32 bit version. If this is the case, I'm not sure how to fix it.

Many thanks in advance.

UPDATED and SOLVED on 12AUG by doing a reinstall and sticking with the current production kernel (2.6.28-14). So far, I haven't had the stability problems that popped up on the earlier 2.6.28 revs and all seems to be working fine.
Bandwidth issues are gone and ipv6 is enabled...

That's what I get for trying random unfinished kernels I suppose.

---

### Post by Philotus on 2009-08-12
I've updated my original post to, hopefully, make it more clear and to include additional steps I have tried to sort out the problem.

Thanks.

---

