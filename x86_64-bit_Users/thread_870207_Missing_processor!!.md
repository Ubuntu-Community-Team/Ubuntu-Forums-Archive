---
title: "Missing processor?!?!"
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by kinuser on 2008-07-25
I have a problem.

I started up my computer today and for some reason it appears that ubuntu is only seeing one "core" or processor from my cpu.  I looked under System Monitor and where there is usually two CPU's there is only one.

I built this computer about two months ago and until today, everthing has been running great.

Configuration:
Kernal    - Linux 2.6.24-19 -generic
Processor - AMD Athlon 64 X2 6000+
Memory    - 7.3 GiB

Any ideas on whether this is a software or hardware issue?  Any ever had just one CPU from a dual core processor go bad or something?

Any help would be great.

---

### Post by stchman on 2008-07-25
> **kinuser said:**
> I have a problem.

I started up my computer today and for some reason it appears that ubuntu is only seeing one "core" or processor from my cpu.  I looked under System Monitor and where there is usually two CPU's there is only one.

I built this computer about two months ago and until today, everthing has been running great.

Configuration:
Kernal    - Linux 2.6.24-19 -generic
Processor - AMD Athlon 64 X2 6000+
Memory    - 7.3 GiB

Any ideas on whether this is a software or hardware issue?  Any ever had just one CPU from a dual core processor go bad or something?

Any help would be great.

Did you somehow install the i386 kernel?  If yes then that kernel does not support SMP.  The -generic supports SMP OOB.

Are you running 32 or 64 bit Hardy?

---

### Post by kinuser on 2008-07-25
I am not sure how to check for the i386 Kernal.  I am running Hardy 64 bit.
I have only ever used the sudo apt-get update and sudo apt-get upgrade to update my computer.  Could it have been automatically downloaded somehow???

---

### Post by Neo0351 on 2008-07-25
post what u get from
```
uname -a
```

---

### Post by xprisoner on 2009-05-24
Edited: 

I was seeing a similiar issue, my problem turned out to be bad dimms.

---

