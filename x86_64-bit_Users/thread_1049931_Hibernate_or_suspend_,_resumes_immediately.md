---
title: "Hibernate or suspend , resumes immediately"
date: 2009-01-25
forum: x86 64-bit Users
---

### Post by santosh9999 on 2009-01-25
Hi,
I just installed 8.10, was using 8.04 without issues.
In 8.10, when I try to hibernate, things get written to disk smoothly. Where I expected the PC to be turned off, it starts again afresh and goes on to resume from Hibernate.
Same case with Suspend as well. It suspends well and when you expect it to just sit on RAM, it triggers by itself immediately to resume smoothly back to the login prompt.

Thanks,
Santosh

---

### Post by santosh9999 on 2009-01-27
Hi,
Did I post in the wrong place or is the issue/question posted too naive to solicit an answer...a little disappointed with my first post drawing no reply for about 2 days.

More details on the system:
Ubuntu 8.10 64 bit AMD 
NVIDIA 8400 GS with proprietary drivers installed

Regards,
Santosh

---

### Post by drs305 on 2009-01-27
Sorry you are not getting an answer to your issue, especially as this is your first experience with the ubuntu forums. I checked the System, Preferences, Power Management to see if a setting there might be interfering with the hibernation but don't see anything there. 

Another issue that might prevent hibernation is a swap issue. Your swap partition must be large enough and, of course, be working. You can check the status of your swap with:
```
free -m
```
You should *not* see all zeros in the *Swap:* line.

In answer to your question on which forum to post on, you might have gotten a better response on the *General* forum. This doesn't sound specifically like a 64-bit issue and many more users look at the *General* forum than this one. You can try a search of all the forums - there have been a fair number of hibernate/suspend threads. Sorting them out may be the most difficult part.

If I find something I will report back. Best of luck finding a solution.

---

