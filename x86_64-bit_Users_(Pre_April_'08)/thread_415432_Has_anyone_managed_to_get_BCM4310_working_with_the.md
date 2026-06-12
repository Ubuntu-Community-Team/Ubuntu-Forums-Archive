---
title: "Has anyone managed to get BCM4310 working with the bcm43xx driver?"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by der_vegi on 2007-04-20
Hi, guys!

I'm using Feisty on an AMD64 machine with a Dell 1490 card, which has a BCM310 chip. It is working fine with Ndiswrapper and the firmware (from Dell) version 4.100.15.5 (so says bcm43xx-fwcutter).

But I would prefer to get it working with the bcm43xx driver, because ndiswrapper sometimes fails.  Unfortunately bcm43xx is extremly slow (something like 20 or 30k compared to 500k with ndiswrapper) with my WPA secured network using the firmware version that comes with the install of bcm43xx-fwcutter (wl_apsta.o). And I can't install the driver that works with my ndiswrapper:
```
bcm43xx: Firmware: no support for microcode extracted from version 4.x binary drivers
```

Did anyone manage to get the card working with bcm43xx?

Greets

---

### Post by greenfrog on 2007-04-20
Not that I know of, I quick using Fiesty for that reason.

---

### Post by der_vegi on 2007-05-06
i've just downloaded the newest version of the standalone driver from [ftp://lwfinger.dynalias.org/patches/bcm43xx-softmac-sa.tar.bz2]("ftp://lwfinger.dynalias.org/patches/bcm43xx-softmac-sa.tar.bz2"), compiled and installed it and now everything seems to work perfectly. :)
see [howto]("http://ubuntuforums.org/showthread.php?t=434946").

---

### Post by der_vegi on 2007-05-06
oh, forgot to mention the output of```
sudo lscpi -vnn
```
```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4310 UART [14e4:4312] (rev 01)
        Subsystem: Dell Unknown device [1028:0007]
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint IRQ 0
```

performance seems to improve a little bit by setting the rate to 11Mbit:
```
sudo iwconfig eth1 rate 11M
```

---

### Post by primitivo on 2007-06-08
BCM4318 on a AMD turion64  acer Aspire 5100 - feisty  : Bingo !
followed the rules step by step 
& had it working in 2 minutes !
formidable !
( i have sweated whole streams over such drivers  with other distro's )

---

