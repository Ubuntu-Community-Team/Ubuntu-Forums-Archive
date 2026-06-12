---
title: "Are packages optimized for AMD64?  I'm confused"
date: 2007-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by underwater on 2007-08-06
Hello, I have some questions about the AMD64 version of Ubuntu.  Basically, are the packages that I would install via aptitude with it AMD64 optimized as well?  I want to make sure that the new AMD64 processor I'm getting is used and not wasted and I'm debating between putting Ubuntu on it vs Gentoo.  I feel that,  if all the packages are optimized (for the most part that is--I'm sure some aren't or whatever) that there is no reason not to run the AMD64 version of Ubuntu.  What are the channels thoughts?

Will the standard packages take advantage of the 64bit goodness of my dual core processor or should I emerge everything in Gentoo to get the full effect?


Thanks in advance,
Underwater

---

### Post by xtknight on 2007-08-06
All packages in AMD64 Ubuntu are pure 64-bit with no 32-bit parts whatsoever.  All packages from the universe, multiverse, main, etc sections of the repositories are pure 64-bit.  Some packages like wine aren't in the 64-bit repositories and must be compiled manually.

You can, however, run 32-bit packages on your AMD64 Ubuntu installation with the proper libraries and sometimes commands like "linux32".

---

### Post by xtknight on 2007-08-06
sorry, double post

---

### Post by Kilz on 2007-08-06
> **xtknight said:**
>  Some packages like wine aren't in the 64-bit repositories and must be compiled manually.


Negative, wine is available from the wine repository as a 64bit deb file for Feisty. There are 32bit packages for Edgy and Dapper, that can be force installed. There is no need to compile wine.

---

### Post by GumbyX on 2007-08-07
> **Kilz said:**
> Negative, wine is available from the wine repository as a 64bit deb file for Feisty. There are 32bit packages for Edgy and Dapper, that can be force installed. There is no need to compile wine.

True, but it only runs as a 32-bit program. There are programs that can only be run as 32bit. That is what I was told here and it makes sense.

---

### Post by stmiller on 2007-08-07
> **underwater said:**
> 
Will the standard packages take advantage of the 64bit goodness of my dual core processor or should I emerge everything in Gentoo to get the full effect?


Ubuntu 64bit is a fully top to bottom 64bit distro. 64bit kernel, 64bit userspace with 64bit packages.
The default kernel and packages are all compiled for generic x86_64, so that they will run on both Intel and AMD 64bit cpus.

Gentoo of course is a more optimzed distro, for any cpu. You compile every package specifically for your own machine.

---

### Post by MikeStone on 2007-08-07
I'm new to Ubuntu and Linux in general.  I'm running an AMD64 processor.  When I downloaded Ubuntu, I downloaded the "normal PC" option.  Does that mean I'm running a 32 bit version?  How can I tell what version I have?

---

### Post by John.Michael.Kane on 2007-08-07
> **MikeStone said:**
> I'm new to Ubuntu and Linux in general.  I'm running an AMD64 processor.  When I downloaded Ubuntu, I downloaded the "normal PC" option.  Does that mean I'm running a 32 bit version?  How can I tell what version I have?

To see if the machine is running a 64bit kernel you can run the command below
```
uname -a
```

Example uname -a output 
```
Linux (your machine name here) 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 **x86_64** GNU/Linux
```

This will list the cpu spec, and show if it's 64bit or not.
```
lshw -C cpu
```

Example lshw -C cpu  output from the machine I'm on:
            
```
      product: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
       vendor: Advanced Micro Devices [AMD]
       physical id: 2
       bus info: cpu@0
       size: 1GHz
       capacity: 1GHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy cpufreq
```

Should you find you have downloaded the 32bit version of ubuntu. You can find direct links to 64bit ubuntu in the thread below.
[http://ubuntuforums.org/showthread.php?t=368607]("http://ubuntuforums.org/showthread.php?t=368607")

---

