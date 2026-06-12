---
title: "32-bit from 64-bit"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by messagesend on 2007-09-20
Im running Kubuntu 7.04, the disk I installed from did not specify 32 or 64 bit. I have a 64 bit processor so I would prefer running the 64-bit OS. Trouble is I dont know which one I have installed. Does anyone know how to tell?

Incidentally, since I am new to linux, how would one go about uninstalling / replacing Kubuntu? (without involving a copy of windows)

---

### Post by John.Michael.Kane on 2007-09-20
> **messagesend said:**
> Im running Kubuntu 7.04, the disk I installed from did not specify 32 or 64 bit. I have a 64 bit processor so I would prefer running the 64-bit OS. Trouble is I dont know which one I have installed. Does anyone know how to tell?

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


> **messagesend said:**
> Incidentally, since I am new to linux, how would one go about uninstalling / replacing Kubuntu? (without involving a copy of windows)

As for replacing kubuntu you can either reinstall using the standard ubuntu iso Or try installing the ubuntu desktop metapackage from inside kubuntu.

```
kdesu aptitude install ubuntu-base ubuntu-desktop 
```

IMHO being that your new to linux/ubuntu you might be better off doing a clean install of the version you want.

---

### Post by jocko on 2007-09-21
> **messagesend said:**
> Incidentally, since I am new to linux, how would one go about uninstalling / replacing Kubuntu? (without involving a copy of windows)

If you mean replace 32bit kubuntu with 64bit kubuntu, the only way is to download the 64bit cd, boot it up and install. To replace the 32bit installation, just install the 64bit version to the same partition, and make sure it's re-formatted in the process...

---

### Post by messagesend on 2007-09-21
I tried those commands & I think i'm on 32-bit OS with 64-bit CPU. Here's the output:

uname -a
Linux Daisy 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu
       product: AMD Processor model unknown
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: cpu@0
       version: 15.11.1
       size: 1GHz
       capacity: 1GHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc _6_ cpufreq

It says "model unknown" but later says "x86-64" under capabilities. I know my CPU to be: AMD Athlon X2 BE 2300 (45W) 2x1.9GHz.

It looks to me like I'm using the 32-bit OS. I have a 64-bit version burned to CD. I expected it to boot from the CD but it didnt.. What happens next?
And thankyou for your help.

---

