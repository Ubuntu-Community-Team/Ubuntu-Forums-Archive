---
title: "My 1.8 GHz iMac G5 is running at 1 GHz!"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by farmer on 2005-10-14
My iMac G5 rev. a 1.8 GHz reports, via CPU Freq Scaling Monitor panel applet, that it is running at 1 GHz. I don't know if this is an error in the applet, or what. I''m going to investigate more, and see what I can see.

---

### Post by Smeggy on 2005-10-14
Thats normal afaik, itll scale up when its needed.

---

### Post by farmer on 2005-10-14
It says my processor isn't supported for scaling, and that it's running at 100%.

> You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

I think it has no idea what's going on, becuase it says it's running at 998947 MHz, which it clearly isn't.

---

### Post by khc on 2005-10-15
does cpufreq-selector work for you? What does lsmod | grep cpu says?

---

### Post by farmer on 2005-10-21
lsmod | grep cpu outputs nothing. cpufreq-selector outpus no cpufreq support.

---

### Post by ctt1wbw on 2006-01-08
You got Ubuntu 5.10 to run okay on your iMac G5?  How, prey tell?

---

### Post by hentaidan on 2006-01-08
Try "watch cat /proc/cpuinfo" in a terminal, and open a few programs, openoffice, firefox etc.

My ibook clock starts at 666Mhz and then jumps to 1333Mhz

---

