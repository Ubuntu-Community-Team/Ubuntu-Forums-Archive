---
title: "Trusted 64-bit setup"
date: 2006-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by wildem on 2006-05-31
Let me mention that my intention is to upgrade the hardware for best performance for a LAMP server. 
1. Is a Lamp server solid under 64-bit chipsets and 64-ubuntu or is it wiser to have the 64bit chipset but have the 32-ubuntu. For me , it seems like a balancing act between performance and stability. 

2. Is a 32bit chipset comparable in performance to a 64 if the OS is 32 bit on both.

Has anyone seen a good case study or experienced a good setup that they might want to mention here. I'm very much interested in this matter.

Cheers,

---

### Post by kuja on 2006-06-01
If I remember right, there really isn't much of a performance difference, though, I do recall the AMD website claiming that their 64bit stuff would outperform your typical 32-bit stuff even if you were only running a 32-bit operating system (difference is pretty much nominal though, but very *slightly* better). As per stability, I haven't noticed any stability differences at all, both the 32 and 64 bit kernels run stable, at least for me.

---

### Post by Patsoe on 2006-06-01
[http://www.anandtech.com/showdoc.aspx?i=2114&p=6](http://www.anandtech.com/showdoc.aspx?i=2114&p=6)
This is a performance test showing higher MySQL performance in 64bit Linux. There are newer reviews than this one (it's two years old, sorry) but I couldn't find them just now.

I think stability of 64bit Ubuntu is not different from the 32bit version. The only reason I'd see not to use it, is if you need third-party closed-source material - like drivers for your special network- or storage-controllers...

---

### Post by Cheese Sandwich on 2007-06-14
I'm having some sort of stability/other issues with server 64 & LAMP.

I've installed server64 + LAMP on a eMachine pentium D machine, as well as xubuntu-desktop & openssh-server.

However, whenever I'd try to login remotely via ssh, ssh would hang after connecting & the server would also stop serving web pages.

So I uninstalled openssh-server for the time being, but even now I surfed around a bit on one of the hosted websites & it just stopped serving pages.

Maybe the xubuntu-desktop is causing problems...?

---

### Post by tgm4883 on 2007-06-14
You will see zero performance gain running a 32-bit OS on a 64-bit Processor Vs on a 32-bit processor (all else being equal).  Keep in mind that > 4 GB Ram is possible on 64-bit, and that 64-bit apps on a 64-bit OS are going to have better performance than 32-bit apps on a 32-bit OS.  It should also be mentioned that 32-bit apps on a 64-bit OS will have worse performance than 32-bit apps on a 32-bit OS.

---

### Post by Kilz on 2007-06-14
A server install should raise no problems running a 64bit os. All the little things like media players, browsers, plugins for browsers and other desktop problems will not come into play.
Dont fall into the 32bit vs 64bit fud trap.

> **tgm4883 said:**
> .  It should also be mentioned that 32-bit apps on a 64-bit OS will have worse performance than 32-bit apps on a 32-bit OS.
Would you happen to have a link to benchmarks for server applications that proves this?

---

