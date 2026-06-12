---
title: "Better 32 or 64 bit?"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by Emanuele_Z on 2009-11-13
Hi guys,

I'm going to upgrade to 9.10 (I have 9.04 but I plan to format and re-install).
What do you recommend? 32 or 64 bit?
Naturally I have 2 GB Ram, so that's not a mandatory upgrade.
I usually develop and compile with gcc/g++ and OpenGL/GLSLang...
I'm more of a kind dev user, but I prefer not to compile the big apps but install via apt-get (don't want to mess with configs etc etc).

What do you suggest? Most of all why?
I've posted the same request here: [http://ubuntuforums.org/showthread.php?t=1325480](http://ubuntuforums.org/showthread.php?t=1325480) but probably on the wrong section, as seen as many answers have been non technical (like "*64 is better than 32 as 11 is better than 10*"...)

Anyway, from a dev point of view the only advantage of 64 bit if you have more than 4gb memory.
Or is it that all the 64 bit compiled application come with optimizations/more registers as default (gcc -march=i686 instead of -march=i386) and thus are faster on modern CPUs?
Any benchmark around?
The x86-64 ISA does use more registers and if I'm not wrong the sse2 are enabled by default with gcc/g++, so on all compiled packets. This could be an pro. Am I wrong?

Because opposed to that we have for sure some downsides, like bigger executables, some issues with 32/64 bits libraries and most of precompiled packets are for 32 bits...

Thanks again,

Cheers,

---

### Post by Emanuele_Z on 2009-11-14
I might install 64bit...Anyone has anything more to suggest ?

Cheers,

Ps.I think people has replied on the other post...

---

### Post by cascade9 on 2009-11-14
Might as well install 64bit. Even if your on a system thats fine for 32 bit, sooner or later you'll be using 64 bit, so I'd start on it now LOL.  

I know of one slightly old 32bit vs 64bit benchmark. Using Ubuntu 8.04 alpha, so I would guess that if there is any changes, 64 bit will have got better since then. 

**[http://www.phoronix.com/scan.php?page=article&item=998&num=1](http://www.phoronix.com/scan.php?page=article&item=998&num=1)**

---

### Post by TheHolm on 2009-11-14
Check a sticky in this forum.
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

64-bit is sill sometimes problematic. 32-bit is much more developed.
IMHO stay on 32.

---

### Post by insane_alien on 2009-11-14
if you have 64-bit capability, then go 64-bit.

---

