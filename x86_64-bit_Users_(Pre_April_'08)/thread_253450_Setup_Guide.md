---
title: "Setup Guide?"
date: 2006-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jasonlfunk on 2006-09-08
I just got a amd 64 x2 3800+ machine. What things to I need to install/activate on a new install of 64 bit Ubuntu to make full use of the dual core and the 64 bit features of the cpu?

---

### Post by hizaguchi on 2006-09-08
Probably just 64-bit Ubuntu and linux-k8-smp (or possibly k7, depending on how old the processor is).  Then run "cat /proc/cpuinfo" and make sure it lists 2 processors and they're both running at the right speed.  If they're running slow (likely 800 MHz), it's probably because they're scaled down.  If that's the case, run glxgears and check them again with it going to see if they speed up.

---

### Post by jasonlfunk on 2006-09-08
It is a 2 ghz dual core and it is showing up in /proc/cpuinfo as 1.25 ghz with 2 core (I do have it overclocked so that is probably why it isn't 800 mHZ). It seems to be scaled down - I run glxgears and nothing happens. How do I scale it back up?

---

### Post by kuja on 2006-09-08
The amd64-generic kernel should have smp support, You could use the k8 kernel if you wanted to though, perhaps slightly more optimal, not 100% sure.

If it's showing as 1.25GHz then it's a result of CPU scaling. You can turn it off in the BIOS probably, look for something along the lines of "AMD cool 'n quiet"

---

### Post by jasonlfunk on 2006-09-09
Thanks man. Cool and Quiet it was. Thanks.

---

