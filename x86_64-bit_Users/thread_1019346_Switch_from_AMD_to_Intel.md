---
title: "Switch from AMD to Intel"
date: 2008-12-23
forum: x86 64-bit Users
---

### Post by jsegars on 2008-12-23
Folks, I'm looking for some guidance...actually more like help because I've already done it. I just replaced my AMD Athlon 3700+ with an Intel Core 2 Quad Q6600. This included a motherboard replacement. I essentially did a hot swap of everything. I shutdown the computer, swapped the parts and turned it back on. Ubuntu started up and is running without any issues (I love it). My concern right now is the Kernel configuration along with various other apps. I'm assuming that kernels are going to have architecture specific flags that are set when it's built depending on the processor you have. I would like to think that a lot of the other programs on this box were built under AMD architecture as well and that the updates would pick up on this fact and re-install/rebuild said apps/kernel. So what I'm getting as is would I be better off re-installing ubuntu under this new configuration or is it ok to just leave it alone? Did I mention I would like to switch to 64-bit?

Thanks in advance

---

### Post by jespdj on 2008-12-23
You don't need another kernel for your Intel processor. The Linux kernel automatically detects your hardware and uses the right settings.

On some Linux distributions (Gentoo for example), you'll get only the source code and you'll compile all the software yourself, optimized for your specific hardware. Ubuntu and most other Linux distro's don't work like that. You get binaries that work on almost any system.

If you now are using 32-bit Ubuntu and you want to switch to 64-bit, you'll have to reinstall the whole system. There's no easy way to upgrade from 32-bit to 64-bit.

---

### Post by jsegars on 2008-12-23
Thanks for the clarification. I think I'll stick with 32-bit as I can't see the need for the upgrade as I'm not looking at addressing memory above 3.5G, nor do I think any of the major apps I utilize take advantage of 64-bits. Thanks again

---

### Post by jespdj on 2008-12-23
The advantages of 64-bit are more than the ability to address more than 3.5 GB RAM. If you install 64-bit Ubuntu, then (almost) all of the applications you get with it are 64-bit native executables. (Only some proprietary, closed-source stuff such as Skype and Google Earth are 32-bit, and note that you can also run 32-bit programs on 64-bit Ubuntu).

Especially if you are using processor-intensive applications (for example video or audio encoding or decoding, encryption, etc.) then you'll notice a massive performance difference on 64-bit.

---

### Post by jsegars on 2008-12-23
You just threw a wrench in my plan. If I didn't have everything setup the way I liked it I would wipe my hard drive clean in a heart beat. Unfortunately it's taken a bit of time to get it there so I don't think I want to deal with starting all over again. Although it doesn't make much sense not to get the most out of the processor as I can.

---

### Post by stchman on 2008-12-23
> **jsegars said:**
> Folks, I'm looking for some guidance...actually more like help because I've already done it. I just replaced my AMD Athlon 3700+ with an Intel Core 2 Quad Q6600. This included a motherboard replacement. I essentially did a hot swap of everything. I shutdown the computer, swapped the parts and turned it back on. Ubuntu started up and is running without any issues (I love it). My concern right now is the Kernel configuration along with various other apps. I'm assuming that kernels are going to have architecture specific flags that are set when it's built depending on the processor you have. I would like to think that a lot of the other programs on this box were built under AMD architecture as well and that the updates would pick up on this fact and re-install/rebuild said apps/kernel. So what I'm getting as is would I be better off re-installing ubuntu under this new configuration or is it ok to just leave it alone? Did I mention I would like to switch to 64-bit?

Thanks in advance

Theoretically there should be no problem.  All the drivers for Linux are in the kernel.

Since you upgraded to a 64 bit processor I highly recommend 64 bit Ubuntu.  The Q6600 is a great processor.  I have one and have been successfully overclocking it now for months to 3.0GHz.

To go to a 64 bit OS a complete reinstall will be necessary.

---

### Post by stchman on 2008-12-23
> **jsegars said:**
> Thanks for the clarification. I think I'll stick with 32-bit as I can't see the need for the upgrade as I'm not looking at addressing memory above 3.5G, nor do I think any of the major apps I utilize take advantage of 64-bits. Thanks again

You paid for a 64 bit processor why not take advantage of it's speed and power?  Think of it as buying a ZR-1 Corvette to drive 65 on the interstate!!!

64 bit OS is about 30% faster on average.  Now that Flash 10 works very well on Ubuntu and you can use Icedtea Java plugin there is no reason to stay 32 bit.

---

### Post by tomdkat on 2008-12-23
> **stchman said:**
> You paid for a 64 bit processor why not take advantage of it's speed and power?  Think of it as buying a ZR-1 Corvette to drive 65 on the interstate!!!
I think of buying a Corvette ZR-1 to pick up chicks....  :lolflag:

Peace...

---

### Post by stchman on 2008-12-23
> **tomdkat said:**
> I think of buying a Corvette ZR-1 to pick up chicks....  :lolflag:

Peace...

True, I am saying why get a hot rod to putt back and forth to the grocery store.

---

### Post by tomdkat on 2008-12-23
> **stchman said:**
> True, I am saying why get a hot rod to putt back and forth to the grocery store.Because good looking women tend to walk along the path I would take to the store?  :)

Seriously, the OP made the change for a reason.  Maybe the old mobo died or maybe they wanted a newer, faster machine.  If the price of the new mobo with the 64-bit dual core processor was "right", they probably didn't think twice about getting it.  I/we don't know how much of a factor having a 64-bit processor was in the purchase decision.  Given how prevalent 64-bit processors are these days, it might be challenging to find a fast 32-bit  processor at a great price point these days.

I don't think running a 32-bit OS on a 64-bit processor is a "waste" at all.  Getting back to the car analogy, how many people actually "use" all the horsepower in the sports cars they own anyway?  :)

Peace...

---

