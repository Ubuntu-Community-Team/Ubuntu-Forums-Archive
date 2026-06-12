---
title: "ACPI issue for Samsung q310"
date: 2009-06-20
forum: x86 64-bit Users
---

### Post by JDShu on 2009-06-20
Hi, I was wondering why acpi is not being supported for the samsung q310. It seems that this problem has existed since 8.10 according to the following threads:

[http://newyork.ubuntuforums.org/showthread.php?t=974336](http://newyork.ubuntuforums.org/showthread.php?t=974336)

[http://ubuntuforums.org/showthread.php?t=937062](http://ubuntuforums.org/showthread.php?t=937062)

Basically, the computer reboots continuously if acpi is not disabled in grub, and recompiling the kernel with cpufreq disabled allows it to boot, but I would rather not mess with that.

Does anybody have a suggestion for how to fix the problem? Can I expect this to be fixed in 9.10 or should I file a bug report? Thanks in advance.

---

### Post by JDShu on 2009-06-29
Alright I'm talking to myself but I've figured out the issue. 

This launchpad thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272530](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272530)

wxplains that Samsung is not supporting 64 bit, and that there are RAM problems. The workaround is to stick "mem=4096M" into the bootline in grub. This will let you enable acpi in exchange for less system RAM. Using the brightness keys however will lock up the keyboard, a problem I actually experienced with Intrepid 32bit, so that is probably a separate issue.

Alternatively you can look into updating the BIOS, but a google search about the issue hasn't been too promising.

Hope this helps other q310 users out there.

---

