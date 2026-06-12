---
title: "reverting to jaunty: karmic kernel will not boot"
date: 2009-10-31
forum: x86 64-bit Users
---

### Post by freelsjd on 2009-10-31
I have a dual-processor (single core) amd64 system that, heretofore, has booted fine with the server kernels of ubuntu.  It is normally necessary to add the "noacpi" kernel parameter with this system in order for it to boot.

When I upgraded to karmic, the new kernel 2.6.31-14-server was there to try out.  But, it will not boot.  Instead, it immediately spits an error message to the screen

Kernel panic  not syncing: Attempted to kill the idle task !

I have tried several things to workaround including additional kernel parameters

clocksource=hpet
nolapic
acpi=off
idle=poll

these ideas were posted several places around the web to fix this problem, but did not work here.  Fortunately, I have a duplicate of my jaunty root partition in another filesystem, so, I am running the prior installation now. 

Any ideas to fix this problem ?

---

### Post by freelsjd on 2009-11-01
I have waited over 24 hours and gotten no response.  I guess it is time for a bug report on this one.  If you can't boot, that is pretty serious IMHO.

Also, having other problems on other machines.  3 separate Ubuntu machines, none of them with a clean upgrade from jaunty to karmic.

---

### Post by gewitty on 2009-11-02
I encountered a similar problem with the desktop upgrade. However, I found that the system _would_ boot if I used the 2.6.31-15 kernel version.

Despite getting 9.10 running though, I ran into some serious problems with both sound (nothing working at all and unable to get ALSA Mixer loaded) and also my NVIDIA drivers.

In the end I reverted to 9.04 via a Clonezilla image backup.

When I get time, I'll do a clean install of 9.10 in a separate partition and see if I can get it working, or maybe wait until the initial bugs have been fixed.

---

### Post by no_martini_no on 2009-11-10
You have 2.6.31-14 kernel ver. Mine is 2.6.31-15 with similar problems!
Check on:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1852158.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1852158.html)

To workaround the karmic upgrade problem, my poor solution was by using an older kernel image (like 2.6.28 ).

---

