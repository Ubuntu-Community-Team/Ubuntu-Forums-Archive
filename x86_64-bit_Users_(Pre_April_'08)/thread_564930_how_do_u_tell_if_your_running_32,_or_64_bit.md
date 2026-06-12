---
title: "how do u tell if your running 32, or 64 bit?"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by coalblack on 2007-10-01
didnt install my system.

---

### Post by jamesford on 2007-10-01
type 'arch' in a terminal. if it says x86_64 then its 64

---

### Post by steveneddy on 2007-10-01
In a terminal type

```
uname -a
```

There is a listing in there that says 64 bit - or it is like i686/64 - something like that.

**uname** is the name of the linux kernel - the** -a** is for all

---

### Post by steveneddy on 2007-10-01
> **jamesford said:**
> type 'arch' in a terminal. if it says x86_64 then its 64

I didn't know that.

---

### Post by John.Michael.Kane on 2007-10-01
Just to add you can run the below command to list the cpu spec, and show if it's 64bit or not.
```
 sudo lshw -C cpu
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

### Post by coalblack on 2007-10-01
wow thanks guys. much help!

---

### Post by jamesford on 2007-10-01
odd, ive got a 6000+ (2x 3ghz) but the  sudo lshw -C cpu command says its capable of 2x3700mhz...

---

### Post by forumkiller on 2007-12-08
> **steveneddy said:**
> In a terminal type

```
uname -a
```

There is a listing in there that says 64 bit - or it is like i686/64 - something like that.

**uname** is the name of the linux kernel - the** -a** is for all


It came up saying i686, does that mean its 64 bit?

---

### Post by jocko on 2007-12-08
> **forumkiller said:**
> It came up saying i686, does that mean its 64 bit?

No. i686 is 32 bit, x86_64 is 64 bit.

---

### Post by forumkiller on 2007-12-08
Is there much advantage to 64 bit in ubuntu? I'm really wanting to use it for Maya 8, and was hoping for some performance improvements over windows xp if i was running in 64 bit.

---

### Post by Sockerdrickan on 2007-12-08
If it's for Linux and it's 64bit you will get render performance improvement yes.

---

### Post by Calvin349 on 2007-12-12
I love this place.

I look around long enough and I find the info I need.  

Thanks all,

Calvin

---

