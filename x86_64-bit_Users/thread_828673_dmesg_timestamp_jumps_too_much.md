---
title: "dmesg timestamp jumps too much"
date: 2008-06-14
forum: x86 64-bit Users
---

### Post by HughR on 2008-06-14
(dmesg(8 ) is the command to dump the kernel's log from the ring-buffer.)

Each line of dmesg output is prefixed with a timestamp: square brackets around the time, in seconds, to 6 decimal places, yielded by the kernel function sched_clock.

On my system, the initial lines have a [0.000000] timestamp. Possibly more than could be executed in a single jiffy.

Then the timestamp takes a large step.  One that differs between boots.  Here is the largest that I have observed:
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[ 2114.573671] time.c: Detected 2399.952 MHz processor.
This suggests that it took 35 minutes between these steps.  But I know it didn't: I was sitting there and it was a normal boot.

Here is the same line from several other boots:
[   21.841625] time.c: Detected 2399.950 MHz processor.
[  648.904955] time.c: Detected 2399.951 MHz processor.
[   28.888185] time.c: Detected 2399.954 MHz processor.

What is going on here?

(Ubuntu 8.04 x86_64 on desktop computer with Intel C2Q6600.  Kernel is Ubuntu 2.6.24-18.32-generic.)

---

