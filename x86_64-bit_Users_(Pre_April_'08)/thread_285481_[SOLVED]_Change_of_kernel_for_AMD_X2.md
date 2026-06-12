---
title: "[SOLVED] Change of kernel for AMD X2?"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by beneedict on 2006-10-26
Hi!
I am running a HP Compaq nx6325 notebook with AMD TL-52 X2 in noapic mode. Which causes the notebook to run on one CPU onlY
Do you think, it is useful to change from the generic kernel to the linux-amd64-k8-smp kernel?
If yes, how to I install it after downloading it from the respiratories?

Thx! Benedikt

---

### Post by kuja on 2006-10-28
Generic kernel should work fine, difference between them should be more or less negligible, and certainly not noticeable.
Edit: If you're using that NOAPIC option, you might be out of luck with getting the second core to work. There have been a couple threads on it here before, I suggest you dig them up and see what they concluded.

---

### Post by beneedict on 2006-10-28
I was prepared to hear that... Too bad. And the worst thing is, that there is no chance (yet) to get the ATI proprietary driver to work without the NOAPIC option...
I am running without noapic now, but if anybody would know more on how to run the ATI driver on a HP notebook, he/she is more than welcome to give hints on that :)

Thx, Benedikt

---

### Post by kuja on 2006-10-29
After a little digging, I found something that might just do the trick! 
Try booting with "noapic maxcpus=2"

---

### Post by beneedict on 2006-11-06
The thing with maxcpus=2 has no effect :( It is still booting one CPU only, since it is missing SMP...

---

### Post by almalaci on 2006-11-06
> **kuja said:**
> Generic kernel should work fine, difference between them should be more or less negligible, and certainly not noticeable.


I'm afraid it's not true.. I had x86_64 edgy on a Compaq Presario AMD Turion and the power management plus some other things were quite buggy, however working fine with an i386 install. I can't think of anything else than the generic kernel..
For us amd64 users it's worth trying a 32bit install of edgy, you probably gain more than you lose out on cpu performance and stuff..

---

### Post by kuja on 2006-11-06
> **almalaci said:**
> I'm afraid it's not true.. I had x86_64 edgy on a Compaq Presario AMD Turion and the power management plus some other things were quite buggy, however working fine with an i386 install. I can't think of anything else than the generic kernel..
For us amd64 users it's worth trying a 32bit install of edgy, you probably gain more than you lose out on cpu performance and stuff..
I wasn't comparing the x86_64 generic kernel the x86 generic kernel (or 386 kernel either). I was comparing the x86_64 generic kernel to itself with k8, xeon, /other optimizations enabled.

I do believe that these problems are both laptop specific, and also dependent on which software you use (KDE vs GNOME) for power management, based on what I've read. As far as I've gathered, the GNOME power management is more problematic in Edgy than the KDE power management. I've never tried any of it for myself though as I've only got a desktop, so I can only rely on what I hear from others.

---

### Post by almalaci on 2006-11-06
As far as I understand there is nothing to compare because there isn't a specific amd64 (or x86_64) kernel in edgy anymore, there is only one kernel for amd64 and i386. That is why things are buggy in my understanding. But I haven't tried kubuntu and many other things myself either. 
Thanks.

---

### Post by kuja on 2006-11-06
There are actually two kernels for x86 - the generic kernel which has pretty much all the regular stuff like SMP enabled, and the 386 kernel, with such things disabled - provided for compatibility reasons.

---

### Post by almalaci on 2006-11-06
OK, but the 386 kernel is not included in a regular install, you would have to compile it right?
Reading over the whole thread again I get what you are saying about comparing, sorry. My point goes a bit off from the original issue of this thread but I guess it's still worth trying a 32 bit install for folks like us who have trouble with amd64. Is that right?

---

### Post by kuja on 2006-11-06
No. It should be a package available for installation.

---

