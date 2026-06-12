---
title: "unable to get past progress bar(Shuttle SN95G5V3)"
date: 2007-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pancilobak on 2007-07-10
Hi All,

I was trying to install ubuntu latest ver (7). As normal, I boot from CD and it brought me to the screen where I choose to run/install ubuntu, run ubuntu in safe mode, ...memory check, check cd etc..

I chose to install ubuntu and it brought me to a screen where a progress bar just running indefinitely. After certain time, it just hang. the bar stopped.

the same thing happened as well when I chose to run ubuntu in safe mode.

I havent even managed to install ubuntu in my hdd. I only hav XP home edition currently installed.

My specs:
AMD 64 3000+ 1.8GHZ (winchester)
2 x 1 GB RAM Corsair PC3200 (400Mhz)
120 GB seagate SATA 1 HDD 8mb 7200rpm
Nvidia geforce 3 ti 200 64 MB AGP 4X
LG DVD RW 16x

Please enlighten me...is it any possible conflict with my hardware? My geforce 3 ti200 seems to be a bit old.

Best regards,
Pancilobak

---

### Post by Cappy on 2007-07-10
Try boot params
```

noapic nolapic nosplash

```
and if it still crashes at least there should be some information where it is crashing.

---

