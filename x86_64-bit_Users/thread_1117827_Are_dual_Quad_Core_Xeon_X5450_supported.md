---
title: "Are dual Quad Core Xeon X5450 supported?"
date: 2009-04-06
forum: x86 64-bit Users
---

### Post by ralib on 2009-04-06
I've spent about 15 minutes trying to find a definitive answer to no avail. I know the Dell Poweredge is supported, but I'm trying to verify that a dual quad core processor config is supported in Ubuntu before I buy the hardware. Can anyone say definitively if I'll be able to get it working? Also, do you think it will require much tweaking?

Here are the specs I'm considering:
Dell PowerEdge 2950
(2) Quad Core Intel Xeon X5450 2x6MB Cache, 3.0GHz, 1333MHz FSB
8GB 667MHz RAM

Thanks in advance,
ralib

---

### Post by 3Miro on 2009-04-06
From what I can see it definitely works.

Ubuntu does great job with multiple cores (just like any Unix). There is no tweaking needed to make it work. Core 2 Duo/Quad and AMD X2/3/4 work out of the box, a CPU would not run only if it is a different architecture (i.e. Spark, PowerPC ... and those also have versions of Linux that will run on them). Standard Windows XP runs on Xeon, therefore Linux will.

Make sure to install the 64-bit version of Linux to get maximum performance. Spending that kind of money on a CPU and then not using its full power is just wrong.

---

### Post by ralib on 2009-04-06
> **3Miro said:**
> From what I can see it definitely works.

Ubuntu does great job with multiple cores (just like any Unix). There is no tweaking needed to make it work. Core 2 Duo/Quad and AMD X2/3/4 work out of the box, a CPU would not run only if it is a different architecture (i.e. Spark, PowerPC ... and those also have versions of Linux that will run on them). Standard Windows XP runs on Xeon, therefore Linux will.

Make sure to install the 64-bit version of Linux to get maximum performance. Spending that kind of money on a CPU and then not using its full power is just wrong.

Great! Thanks for the response.  I'll be sure to get the 64-bit version, I'd hate to waste all that potential. :)

---

### Post by Arup on 2009-04-06
Works fine on my dual quad core Intel board with 5400 chipset. If you have any doubts, try to run the live cd and you will get the most definitive answer.

---

### Post by lisati on 2009-04-06
The 64-bit version runs fine on my laptop with its Intel dual core T5450 cpu. I'm not sure of the significance of the T or the X in the chip number but I can't forsee any major hassles.

---

### Post by kevmitch on 2009-04-07
Generally the processor is the last thing you need to worry about in terms of compatibility with Linux. This is especially true for Intel processors and even more true of Xeon. Intel knows that Linux is keeping them in the high end market and they're very good about ensuring that their hardware is supported.

---

### Post by 3Miro on 2009-04-07
Likewise AMD has excellent support for Linux. ATI used to have poor Linux support and look at what AMD did with them, ATI is at least as well supported as NVIDIA.

For video and CPU there shouldn't be any compatibility issues at all.

---

### Post by ralib on 2009-04-08
It might be a few weeks until I'm ready to order my new server and move on this, but it sounds like I won't have any OS trouble.

Thank you all for your input.

-Ralib

---

### Post by stchman on 2009-04-09
If I am not mistaken (the other forum member can correct me) the Linux kernel supports up to 32 processors (logical or physical).

So yes your dual quad cores will be supported.

---

### Post by stchman on 2009-04-09
> **3Miro said:**
> Likewise AMD has excellent support for Linux. ATI used to have poor Linux support and look at what AMD did with them, ATI is at least as well supported as NVIDIA.

For video and CPU there shouldn't be any compatibility issues at all.

I disagree, Nvidia cards work better with Linux than ATI/AMD.  It is getting better though.

---

### Post by 3Miro on 2009-04-09
For years it was the case that ATI cards would barely run under Linux and if you want Linux, then you must get NVIDIA. However, I recently heard very good things about the new ATI drivers, since it became AMD/ATI, there has been great effort to improve the Linux support. Currently System 76 offers only ATI cards for their Desktop computers, so they must be well supported.

NVIDIA on the other hand had a problem with the new KDE 4.x KDE 4.x was released over a year ago and it had big problems with NVIDIA cards, not due to KDE but due to the driver. It wasn't until driver 1.80 that most of those were resolved. That was a big negative for NVIDIA in my books.

---

### Post by fbonniwell on 2009-07-19
> **3Miro said:**
> From what I can see it definitely works.

Ubuntu does great job with multiple cores (just like any Unix). There is no tweaking needed to make it work. Core 2 Duo/Quad and AMD X2/3/4 work out of the box, a CPU would not run only if it is a different architecture (i.e. Spark, PowerPC ... and those also have versions of Linux that will run on them). Standard Windows XP runs on Xeon, therefore Linux will.

Make sure to install the 64-bit version of Linux to get maximum performance. Spending that kind of money on a CPU and then not using its full power is just wrong.


Correct me if I'm wrong, there isn't a version of Ubuntu x64 that would run on a Duel Quad Core Xeon X5450. There are only AMD64, which only run AMD processers and i386 32bit available. Granted you can install the i386 on this Intel Xeon X5450, but it won't be in a true  64 bit mode, just 32 bit mode. 

I also have this exact Xeon configuration and was troubled when I found 64bit is only in favor of AMD processors. It's like having a Ferrari with a valet key in the ignition.  


FB

---

### Post by dagrump on 2009-07-19
Just because it is called AMD64 it also works on Intel cpu's.

---

### Post by lisati on 2009-07-19
> **dagrump said:**
> Just because it is called AMD64 it also works on Intel cpu's.

I can confirm this: the so-called AMD64 version works well on my laptop which has a dual-core CPU by Intel.

---

### Post by fbonniwell on 2009-07-19
> **lisati said:**
> I can confirm this: the so-called AMD64 version works well on my laptop which has a dual-core CPU by Intel.
 
 
Hello,
 
When I try to install Ubuntu AMD64 I get this error:
"This Kernel requires an x86-64 CPU, but only detected and i686 CPU. 
Unable to boot - please use a kernel appropreate for your CPU. 
 
I think the XEON X5450 is not the same. 
 
Thanks,
 
Frank

---

### Post by fbonniwell on 2009-07-19
> **fbonniwell said:**
> Hello,
 
When I try to install Ubuntu AMD64 I get this error:
"This Kernel requires an x86-64 CPU, but only detected and i686 CPU. 
Unable to boot - please use a kernel appropreate for your CPU. 
 
I think the XEON X5450 is not the same. 
 
Thanks,
 
Frank


I figured it out! It's because I had Virtualization disabled in my bios. We always test new OS's in VMware before we install. It's installing now!

:D

---

