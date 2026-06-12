---
title: "64bit Ubuntu freezes intermittently, 32bit on same machine does not"
date: 2009-08-23
forum: x86 64-bit Users
---

### Post by ironblade on 2009-08-23
Hi all,

As per the topic, my 64bit install freezes intermittently, I think it started several weeks ago (I've just persevered), probably after an update.

The freeze is random - I've had it while doing stuff, and just after booting, prior to opening any apps.
The freeze is complete - the screen locks up, and the system does not respond in any way, except to holding the power button down for a hard power-off.

I've done some checking - I've checked my RAM, and that's been given the all-clear by memtest. I've run the various CPU tests on The Ultimate Boot CD, and it hasn't found issues.
Finally, I've run 32bit Ubuntu, first off the live CD, now installed to a spare partition (on same HDD as 64bit install). In 32bit, I'm not getting any freezes, so it appears to be limited to 64bit, probably the kernel.

Anyone in the same boat?


EDIT:
I figured it out - it was my BIOS. I reset to default settings and the freezing went away.

---

### Post by Yellow Pasque on 2009-08-24
Do any keyboard LED's start blinking when you lock up? If so, that would be a kernel panic. If not, you're probably looking at an X freeze.

---

### Post by ironblade on 2009-08-24
> **Temüjin said:**
> Do any keyboard LED's start blinking when you lock up? If so, that would be a kernel panic. If not, you're probably looking at an X freeze.

I haven't noticed any blinking.

Also, it seems I spoke too soon - I just had a freeze in 32bit, too.
I'm now booted into the default Jaunty kernel (as supplied on CD iso) 2.6.28-11-generic.
I was just in -15, which seems to have the freeze issue, and -11 doesn't (so far), that'll at least point me in the right direction...

There's nothing in Xorg.0.log, syslog or kern.log to suggest anything happened.

Wonder if I need to look at my CPU and maybe reseat it with fresh thermal paste?

---

### Post by Jouke74 on 2009-08-24
If you have random freezes over various software or things, it is time to first check the internal memory with Memtest. Open Grub it should be an option in the boot-up list. If this test shows errors, or also crashes, it is time to check / replace your memory sticks.

---

