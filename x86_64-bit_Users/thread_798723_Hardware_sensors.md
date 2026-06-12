---
title: "Hardware sensors"
date: 2008-05-18
forum: x86 64-bit Users
---

### Post by mcgodx on 2008-05-18
I just built a new computer, I'll show the specs at the end of this post, but the problem I am having is, when I installed Ubuntu 8.04 64-bit version on it, I installed lm-sensors and various temperature monitoring applets for the panel.  None of them seems to be able to detect temperature sensors.

They always just give some variation of the error "No sensors found!" and I cannot access the preferences to change it.

My computer is a micro ATX desktop with the following:

Intel DG35EC motherboard
Intel Q9300 45nm Core 2 Quad processor
4GB Geil Esoteria DDR2 RAM
2 Western Digital 320GB hard drives

That's all that's all the relevant hardware information I can come up with.  I am not sure if I forgot a package somewhere, but all the dependencies were installed no problem.

Thanks for any help!

---

### Post by mcgodx on 2008-05-18
> **mcgodx said:**
> I just built a new computer, I'll show the specs at the end of this post, but the problem I am having is, when I installed Ubuntu 8.04 64-bit version on it, I installed lm-sensors and various temperature monitoring applets for the panel.  None of them seems to be able to detect temperature sensors.

They always just give some variation of the error "No sensors found!" and I cannot access the preferences to change it.

My computer is a micro ATX desktop with the following:

Intel DG35EC motherboard
Intel Q9300 45nm Core 2 Quad processor
4GB Geil Esoteria DDR2 RAM
2 Western Digital 320GB hard drives

That's all that's all the relevant hardware information I can come up with.  I am not sure if I forgot a package somewhere, but all the dependencies were installed no problem.

Thanks for any help!

Looking around I found the solution to this problem for any people doing searches on this subject.  Run the command:
```
sudo sensors-detect
```
That detected all the sensors for me, and once I restarted Linux it worked perfectly.

---

### Post by philinux on 2008-05-18
[http://www.lm-sensors.org/wiki/Documentation](http://www.lm-sensors.org/wiki/Documentation)

Too much info here. :lolflag:

---

