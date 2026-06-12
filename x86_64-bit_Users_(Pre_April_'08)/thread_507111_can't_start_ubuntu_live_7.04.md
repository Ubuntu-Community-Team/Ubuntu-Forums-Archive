---
title: "can't start ubuntu live 7.04"
date: 2007-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by d34th on 2007-07-22
Hello
I'm trying to boot from a live CD to install ubuntu, but when booting, (start or install ubuntu option) the screen switches off, like when you turn off the computer.
I've also tried with the x86 version, but it displays some error messages
The PC is a brand new Intel core2duo E6600 with a geforce 8600GT
the motherboard is an asus P5B

I don't think it is a hardware problem as long as the windows intallation CD starts without any problem
I've also checked that CD is not corrupted

---

### Post by angryfirelord on 2007-07-22
It's a driver issue. Ubuntu is trying to load the "nv" driver, which fails to work. Try loading the vesa driver instead (it's activated by hitting  F4 and selecting it).

---

### Post by d34th on 2007-07-23
It works now
I also forgot to put the jumpers on the DVD so it failed whe trying to boot

Thnk you for your help

---

