---
title: "Which kernel should I choose for Pentium D processor?"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by shucho on 2006-06-01
I've setup Ubuntu 6.06 AMD-64 version successfully last night. But it seems that  
  it is slower than the Ubuntu 5.04 x86 w/ a SMP kernel :(  Can anybody kind enough tell me what kernel should I choose fro my Pentium D processor. I only found an xeon kernel, is it suitable for my situation? Or, maybe I have to build from source?:confused: 

TIA

---

### Post by RAOF on 2006-06-01
The -xeon one should work.  It's possible that the -generic kernel isn't built with SMP, which would mean you're only using one core.  The -xeon one **will** be SMP enabled.

---

### Post by shucho on 2006-06-02
Thank you for you reply, I will try it:)

---

### Post by JoWilly on 2006-06-02
Yep, the xeon one is right one as it is compiled with optimizations for EM64T.

The -generic one definitely also uses smp.

---

### Post by kaffelars on 2006-08-11
Great :D 
I installed Ubuntu 64 bit on my Pentium D box yesterday, and it was fast with the generic kernel, but a little more (CPU) speed shouldn't kill me ;)

---

### Post by mikeescott on 2006-08-11
Where do I find this xeon kernel?

---

### Post by Kilz on 2006-08-11
> **mikeescott said:**
> Where do I find this xeon kernel?

Open synaptic and search for linux-image :D You may have a number of them avialable, chose the one with the higest version number.

---

### Post by mikeescott on 2006-08-11
I am not able to get on the net yet with Ubuntu, still using Windoze to look for help getting it set up. I've been looking for about a week and I still have not been able to get the modem working, among other things. This is the 1st Linux I have ever used. Can I download the kernel with Windoze and install with Ubuntu from file?

---

