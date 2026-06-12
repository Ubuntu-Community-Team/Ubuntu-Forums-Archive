---
title: "How do I ensure I have 64 bit version running"
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by professor-g on 2007-07-18
From command line - how do i quickly look-up if a machine has a 32- or 64-bit operating system installed.

I have a bunch of machines (some old, some new) noone is using and I have been ssh into them to check what resources are available.

Please advise.

Thanks,

G.

---

### Post by John.Michael.Kane on 2007-07-18
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

---

### Post by professor-g on 2007-07-18
Thanks for the quick reply (helps keep us all going and using these O/Ss)

I found this command right after I wrote the original post and indeed it is a 32-bit version running on 64-bit hardware (loser ?)
Details below (in case this helps others to visualise this problem).

So it seems I used a 32 bit install.
Now - is there a means to update to a 64 bit version without re-installing the whole O/S, or is it just better to start from scratch and install a 64 bit version.

Which 64-bit version is most highly recommended for highest performance regarding floating point operations (i.e. bare-bones minimum) ?

---
Indeed :
---
user@gg:718  ~>uname -a
Linux tempranillo 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
---

Also :
---
 user@gg:719  ~>lshw -C cpu
  *-cpu
       product: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
.
.
.
       width: 64 bits
---

---

### Post by John.Michael.Kane on 2007-07-18
Theres no known way to upgrade from 32bit ubuntu to 64bit. 

Your best off backing up any files ect you need, and reinstalling clean.

As far as performance theres going to minor differences with regards to different distro speed. Some distros seem to run quicker. Some also allow you to install only what you need. 

I would try ubuntu 64bit first, and run it for 30 days see if it does what you need it to. If 64bit ubuntu does not fit your needs. You can look here [Other OS Talk:]("http://ubuntuforums.org/forumdisplay.php?f=147") to get info on other  distros that might be more suited to your needs.

In the end It really will come down to what you want to do with the machine, and what distro you feel will suit that purpose.

---

