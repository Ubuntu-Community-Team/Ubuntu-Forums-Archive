---
title: "Dell E521 Booting help."
date: 2007-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nitro Boy on 2007-03-18
I just bought a new system, and finally decided to try out the 64bit ubuntu. I downloaded 6.10 x86_64, burned it, and put it in. When I go to boot, I choose the first option, and it freezes at the loading screen. What can be done to fix this?

Specs:
Amd 64 x2 3800+,
1gb ddr2 533,
160gb SATA-II (this might be the problem),
SATA-II Dvd+/-RW (I don't know the specific model atm,
BFG 7600GT 256mb.

Thanks in advance for all the help!

---

### Post by kuisma on 2007-03-22
Specify either "noapic" or "apci=off" before booting (F6).  Don't ask my why, but both solutions works on the E521.
Also be aware that the USB controller seems to be unreliable and may fail from time to time, even with the 1.1.5 BIOS.

---

