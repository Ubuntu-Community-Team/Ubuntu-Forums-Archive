---
title: "Dell D820-64bit-Current experience"
date: 2006-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mattyj on 2006-12-24
Hello,

I have read several posts suggesting that the newer kernels will have better support for the Core2Duo in the Latitude D820.  I am looking to buy a 64 bit laptop with alot of RAM and it fits the bill.

Your experience is appreciated.

---

### Post by xopher on 2006-12-24
Core2Duo is a great CPU, great price/performance ratio too. It would definately be my choice of upgrade if I were to do it.

I have a friend with this CPU who hasn't had any problems whatsoever, and is very satisfied with it.

---

### Post by gonesolo on 2006-12-24
> **mattyj said:**
> Hello,

I have read several posts suggesting that the newer kernels will have better support for the Core2Duo in the Latitude D820.  I am looking to buy a 64 bit laptop with alot of RAM and it fits the bill.

Your experience is appreciated.


Dell's new laptop have the option of the 64 bit Turion processors as well. i've not been a fan of Intel for a long time now so will always go AMD if I have a choice and now with Dell I'm glad to say I do have that choice.:D

---

### Post by mattyj on 2006-12-24
Thank You.  I am specifically looking for resolution of the issue related to having to pass "notsc" to the kernel and other issues.

Does anyone actually running one have some current experience?

Looking at Dell Latitude D820, 2ghz C2D, 4GB RAM, 512MB Nvidia card, 3945 wireless card.

Specifically:

1.  Any issues with install?
2.  Issues with wireless?
3.  Currents suspend/close top  to suspend tips?

Thank You,

MJ

---

### Post by grimtrigger on 2007-05-28
Couple of things about the D820:

You won't see all 4gb of the RAM. Regardless of running a 64bit OS, which in theory should be able to address well over 4gb in memory, some limitation of the notebook version of the processor (runs in 64 bit "emulation" mode). Appears that only a little over 3gb will be usable to the OS. Before you chop your RAM down to 3gb though, remember that running different size chips in the banks will slow down your throughput by half, since matching the slots will allow DCI mode. 

Also, check the net about the 512 on the video card. It's really just 256 dedicated and 256 shared. There are a bunch of folks moaning about it out there.

That said, my D820 arrives in 2 days. :D

-gt

---

### Post by mattyj on 2007-05-29
I have been running Feisty for ~ 4 months on my D820 and it works great.  You are right, you only see 3.2 GB  of RAM as that is what the chipset is limted to (why macbookpros only have option for 3 GB), and the video card is relatively slow.  The chipset issue should be resolved with Santa Rosa I think.

But other than that everything works out of the box.  Wifi, suspend, you name it.  If I turned on compiz it stopepd suspending so I don't use that anymore, maybe there is a workaround.

But in general a great machine.  Got 4 GB, 2.33 ghz, 160gb hd, WUXGA for $2100 on their refurbished site, so keep an eye out.  My buddy has the precision version with the better graphics card and it is about twice as fast in term of FPS, but I am pretty happy with mine for the scientific computing I do when on the road, have 16 core opteron with 64GB of ram as my main machine at work, so slow compared to that  (:   

Definitely get the intel wifi card, not worth hassling with the other stuff in my opinion.

---

### Post by bimmerd00d on 2007-05-31
I've got a D820, and i FINALLY have it configured to where beryl doesn't lag at all.  Sync to VBlank needs to be disabled!

---

