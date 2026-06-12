---
title: "Live CD 64 bit and 32 bit Ubuntu 8.04?"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by oceallaighm on 2008-06-21
Hi,

I can now boot from both the 64 bit and 32 bit Ubuntu 8.04 CD's.  Having booted from the 64 bit CD, I go System, Administration, System Monitor, System tab, this shows Kernel Linux 2.6.24-16-generic, memory 3.7GiB.

I have a sinking feeling that the 64 bit AMD Live CD is running in 32 bit mode?

How can I prove that the 64 bit AMD Live CD is 64 bit? (I do know, that I did download the 64 bit AMD iso image.) As I need to check that Ubuntu 8.04 64 bit AMD can recognise most of my hardware, before I zap Vista.

Thanks.

---

### Post by Kilz on 2008-06-21
> **oceallaighm said:**
> Hi,

I can now boot from both the 64 bit and 32 bit Ubuntu 8.04 CD's.  Having booted from the 64 bit CD, I go System, Administration, System Monitor, System tab, this shows Kernel Linux 2.6.24-16-generic, memory 3.7GiB.

I have a sinking feeling that the 64 bit AMD Live CD is running in 32 bit mode?

How can I prove that the 64 bit AMD Live CD is 64 bit? (I do know, that I did download the 64 bit AMD iso image.) As I need to check that Ubuntu 8.04 64 bit AMD can recognise most of my hardware, before I zap Vista.

Thanks.

open a terminal, type ```
uname -a
``` at the end of the string it should say x86_64 GNU/Linux if its 64bit

---

### Post by oceallaighm on 2008-06-21
Hi,

Having booted from the 64 bit CD, I go System, Administration, System Monitor, System tab, this shows Kernel Linux 2.6.24-16-generic, memory 3.7GiB
Processor AMD 64 x 2 TK 57

Having booted from the 32 bit CD, I go System, Administration, System Monitor, System tab, this shows Kernel Linux 2.6.24-16-generic, memory 3.3GiB
Processor 0: AMD 64 x 2 TK 57
Processor 1: AMD 64 x 2 TK 57

When I use uname -a in the terminal on the 64 bit CD I get X86_64 SMP
When I use uname -a in the terminal on the 32 bit CD I get i686 SMP

Why do I not see 2 processors present in System, Administration, System Monitor, System tab on the 64 bit OS and why doesn't the 64 bit OS report the full 4GB of ram.  Both the Bios and Windows Vista Home Premium (which I understand as a 32 bit OS, cannot use more than about 3.5GB of memory) report 4GB present?

Thanks

---

### Post by Cappy on 2008-06-21
> **oceallaighm said:**
> Windows Vista Home Premium (which I understand as a 32 bit OS, cannot use more than about 3.5GB of memory) report 4GB present?


It's not really using the full 4GB, it just says it is so consumers won't complain.

---

### Post by cariboo on 2008-06-22
Open up a terminal (Applications-->Accessories-->Terminal) and type the following:

```
cat /proc/cpuinfo
```

And you should see something like the attached file:

Jim

---

