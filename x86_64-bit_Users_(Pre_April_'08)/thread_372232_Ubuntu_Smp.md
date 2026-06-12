---
title: "Ubuntu Smp"
date: 2007-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trippen Out on 2007-02-27
high i was curious if ubuntu 64bit was setup as an smp or single core distro  i would perfer to have it setup for smp is this possible or do i have to do something ive noticed that some distros have smp kernels and what not.. any info on this subject would be greatly welcomed

---

### Post by magicfab on 2007-02-28
Hi there,

Since Edgy you get a generic kernel image, meaning it includes support for all architectures (including 386/686/smp/k7)

There is a thread with many details about this decision and performance differences (not noticeable), etc.:
[http://ubuntuforums.org/showthread.php?t=353128](http://ubuntuforums.org/showthread.php?t=353128)

---

### Post by Trippen Out on 2007-03-02
> **magicfab said:**
> Hi there,

Since Edgy you get a generic kernel image, meaning it includes support for all architectures (including 386/686/smp/k7)

There is a thread with many details about this decision and performance differences (not noticeable), etc.:
[http://ubuntuforums.org/showthread.php?t=353128](http://ubuntuforums.org/showthread.php?t=353128)


are you saying that you would not see a noticeable difference between running smp vs standard.. im confused on that

---

### Post by enjoy_freestyle on 2007-03-03
no... he said that the generic kernel that ubuntu installs on your pc has the support for smp enabled!!

...and if you have a dual core and if you want to use both core the kernel must have smp enabled!

so if you have the generic kernel you should have the smp....

bye

---

### Post by flapane on 2007-03-03
check with cat /proc/cpuinfo

---

