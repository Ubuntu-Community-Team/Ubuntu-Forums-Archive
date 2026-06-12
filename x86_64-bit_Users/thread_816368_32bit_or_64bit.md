---
title: "32bit or 64bit"
date: 2008-06-02
forum: x86 64-bit Users
---

### Post by RWells on 2008-06-02
I just pruchased a new Acer Apire with a 
AMD Athlon™ X2 Dual-Core Processor BE-2350 chip, and upgrade to 4gig ram.

Is this 64-bit capable?

I already have 32-bit Ubuntu 8.04 installed and working perfectly with no problems installing other thatn only recognizing only 3.2gigs of ram, is there any real reason to install 64-bit version, or would I just be asking for problems.


Thanks
Rusty

---

### Post by Kevbert on 2008-06-02
32 bit operating system = 3.2Gb maximum.
64-bit should work just fine and the machine should see just under 4Gb of memory.  The only thing you may have problems with is flash. 
You may need to set the bios up to see the memory hole (addresses just above 3.2Gb).  The memory hole exists as no-one ever thought we'd ever have this much memory on a pc and so other devices, such as your ports were allocated memory (addresses) just above 3.2Gb. The memory hole patch in effect re-allocates higher memory to the other devices allowing you to use almost all your 4Gb. To check the amount of memory available you can type
```
free -m
```
in terminal.

---

### Post by monkeyking on 2008-06-02
Well it depends on what you are planning todo,
if you're not planning to use the last 800 gig memory, I wouldn't bother.

Alot of plugins for various programs are quite problematic.

I remember having problems with firefox/flash,
and some packages for R(statistic tool) and some for python.

But then again if you're using 64bit at another computer,
then I would use 64bit on my laptop.
So I would have a consistent system.

---

### Post by John.Michael.Kane on 2008-06-02
> **RWells said:**
> I just pruchased a new Acer Apire with a 
AMD Athlon™ X2 Dual-Core Processor BE-2350 chip, and upgrade to 4gig ram.

Is this 64-bit capable?

I already have 32-bit Ubuntu 8.04 installed and working perfectly with no problems installing other thatn only recognizing only 3.2gigs of ram, is there any real reason to install 64-bit version, or would I just be asking for problems.


Thanks
Rusty

First I take it you have read the thread below.
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

To answer your question. Yes, that processor is 64bit capable, and nearly all problems one may encounter on 64bit can be replicated under 32bit so the notion of one being less problematic than the other is nearly always false.

Also most programs one would use under 32bit is installable under 64bit.

---

### Post by RWells on 2008-06-02
> **John.Michael.Kane said:**
> First I take it you have read the thread below.
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

To answer your question. Yes, that processor is 64bit capable, and nearly all problems one may encounter on 64bit can be replicated under 32bit so the notion of one being less problematic than the other is nearly always false.

Also most programs one would use under 32bit is installable under 64bit.

No I had not read that thread, Thanks for pointing it out.

I will probably try the 64-bit just for grins, dont really need it right now.

Thanks
Rusty

---

