---
title: "16 CPU machine"
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by G3rrrr on 2007-09-21
Hi there forum.

Hope you can help. We have a pc with 16 cores, 16GB of ram. We have tried red-hat, but got a kernel panick. UBUNTU installed nicely, but we can only access 8 of the cores. 
We want to stick to UBUNTU, on a CPU intensive simulation. 

Has anybody out there run on  more than 8 cores? 

The suppliers got SUSE to see all 16 cores, but had to install some patch. 

Any help will be great - as we really want to stick to UBUNTU if we can. 

Kind Regards, 

Technical team.
MSC-Africa

---

### Post by fakie_flip on 2007-09-21
> **G3rrrr said:**
> Hi there forum.

Hope you can help. We have a pc with 16 cores, 16GB of ram. We have tried red-hat, but got a kernel panick. UBUNTU installed nicely, but we can only access 8 of the cores. 
We want to stick to UBUNTU, on a CPU intensive simulation. 

Has anybody out there run on  more than 8 cores? 

The suppliers got SUSE to see all 16 cores, but had to install some patch. 

Any help will be great - as we really want to stick to UBUNTU if we can. 

Kind Regards, 

Technical team.
MSC-Africa

Support for it comes from the kernel. If the stock kernel in Ubuntu can't support that many cores, then you need to build your own kernel in Ubuntu from source code. However, I think that 16 cores is supported. Personally, Ubuntu is doing just fine with my AMD 3800+ 64 x2 cpu. If Ubuntu does not support your computers hardware, please file a bug report, so that the developers can add support for your hardware.

---

### Post by david_2001 on 2007-09-21
I've compiled kernels before but I've never had to use this particular configuration option.  Anyway, the kernel configuration parameter CONFIG_NR_CPUS is set to 8 for the stock feisty 2.6.20-16-generic kernel, so compiling with CONFIG_NR_CPUS=16 has got to be the first thing to try (there are plenty of kernel compilation guides around for Ubuntu/Debian).

---

### Post by stmiller on 2007-09-21
Yes you'll definitely want to compile your own kernel for this. The default setting in the Ubuntu kernel is for 8 cores max, it looks like. Linux supports up to **255 cores**, according to the "make menuconfig" options. !? Interesting. 

It's also good to compile your own kernel as you can specify AMD or Intel, memory options, and other stuff for such a high end box.

Check out the [master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158").

---

### Post by dcstar on 2007-09-22
> **stmiller said:**
> 
............
It's also good to compile your own kernel as you can specify AMD or Intel, memory options, and other stuff for such a high end box.

Check out the [master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158").

And you can also turn off various kernel items that don't apply to your hardware - thus reducing kernel size and compilation time significantly!

---

