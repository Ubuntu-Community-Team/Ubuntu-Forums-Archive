---
title: "[SOLVED] Is my machine a 64bit or 32bit?"
date: 2008-08-18
forum: x86 64-bit Users
---

### Post by HousieMousie2 on 2008-08-18
I was under the impression that the AMD Athlon Thoroughbred was a 32bit processor... which is what I have in my machine.

However, when I typed:

uname -a

in a terminal, I got this result:

Linux "MyComputer'sName" 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

When I typed:

grep flags /proc/cpuinfo


I got:

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts


When I typed:

less /proc/cpuinfo

I got:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Athlon(tm) XP 2400+
stepping        : 1
cpu MHz         : 1998.424
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips        : 4000.31
clflush size    : 32



Now, not knowing what the things I typed are really looking at, I am wondering if I did not grab the wrong ISO version of Hardy for my machine... since in another thread it states that the i686 is for 64 bit CPUs.

Hardy is working, but it is acting a *little* strange.

Thank you for your time!

---

### Post by drs305 on 2008-08-18
This is the response for a 64-bit machine running the 64-bit kernel:
```
Linux hb1 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 **x86_64** GNU/Linux

```

When I run cat /proc/cpuinfo (edited):
```

~: cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
cpu cores	: 2
processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 2009.260
clflush size	: 64
cache_alignment	: 64

```


i686 is still for 32-bit systems but can run on 64-bit machines. Added: specifically - Athlon is 32-bit, the newer 64-bit are called Athlon64.

---

### Post by HousieMousie2 on 2008-08-18
Thank you!  I am casting about looking for any possible cause for the problems... seemed a good idea to start with human error... mine.

Cheers!

---

### Post by jayson.rowe on 2008-08-18
Athlon XP = 32-bits.

---

### Post by jespdj on 2008-08-19
i686 = 32-bit
x86_64 = 64-bit

---

### Post by stchman on 2008-08-19
Your machine is not capable of running 64 bit.  To run 64 bit on AMD you need an Athlon 64, Athlon 64 X2, or Phenom.

---

### Post by elmoosecapitan on 2008-08-19
'i6' is the prefix to the archetype i686_xx, in which xx is 32, or 64 (2,4,8,16 are no longer made; rest in piece). At any rate, 64-bit machines are sometimes noted as x64 or 86_64, whereas 32-bit machines are sometimes seen under i686 or 86_32.

If you run: ```
cat /proc/cpuinfo 
``` in your terminal you should then be able to see your processor information regardless of OS platform. If you see two processors then you have a 64-bit machine.


Can you define 'a little strange'?

---

### Post by Kilz on 2008-08-19
> **elmoosecapitan said:**
>  If you see two processors then you have a 64-bit machine.



While this thread is almost dead since the original poster has not posted. The above statement is wrong in case anyone in the future finds this thread. The original core duo was a 32bit processor. It will show two cores.

---

### Post by HousieMousie2 on 2008-08-20
> **Kilz said:**
> While this thread is almost dead since the original poster has not posted. The above statement is wrong in case anyone in the future finds this thread. The original core duo was a 32bit processor. It will show two cores.

LOL  Sorry about that... I got my answer from the first person to reply to me.  I did not think it so critical an issue... did not cross my mind to set it as Solved, but I shall do so now.

Thank you to everyone else who took the time to post, lol, even if they didn't take the time to read what other people had said.

Cheers!

---

### Post by HousieMousie2 on 2008-08-20
> **elmoosecapitan said:**
> 'i6' is the prefix to the archetype i686_xx, in which xx is 32, or 64 (2,4,8,16 are no longer made; rest in piece). At any rate, 64-bit machines are sometimes noted as x64 or 86_64, whereas 32-bit machines are sometimes seen under i686 or 86_32.

If you run: ```
cat /proc/cpuinfo 
``` in your terminal you should then be able to see your processor information regardless of OS platform. If you see two processors then you have a 64-bit machine.


Can you define 'a little strange'?

Thank you for the command, less /proc/cpuinfo gave me the same result... as I posted in my original post in this thread.

Sorry, I had missed you asking a question...

Yeah, it wasn't wanting to mount my ntfs HDD partition, but after fighting with it, that has been resolved... except for Amarok not being able to get my music off of that HDD.  Still not sure what to do about that.  It can see it, meaning I can select it in the settings for Collection, but it never actually finds/lists/loads the mp3s.

In Gutsy, I had the nvidia-glx-new drivers... worked great... have been fighting with them in Hardy, but *think* that it has been sorted out now.  Oh the lengths we go to for pretty screensavers (well, some of anyway. :) )

But these issues are way off of the thread topic... thank you for asking though.

Cheers!

---

### Post by Liviu-Theodor on 2008-09-02
I know the thread is solved, but I have an AMD Athlon with Barton technology (which is newer than Thoroughbred), but is still 32 bit. Only AMD processors Athlon 64/64FX or newer are 64bit processors (now they produce even 64 bit Sempron).

---

### Post by HousieMousie2 on 2008-09-14
> **Liviu-Theodor said:**
> I know the thread is solved, but I have an AMD Athlon with Barton technology (which is newer than Thoroghbred), but is still 32 bit. Only AMD processors Athlon 64/64FX or newer are 64bit processors (now they produce even 64 bit Sempron).

Thanks for posting anyway, Liviu-Theodor!  It still might help someone else and that's a good thing!
 :guitar:

---

