---
title: "[SOLVED] Installing - Won't go past hardware drivers"
date: 2007-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by lukeminus on 2007-09-19
Hello. 

I just purchased a new cheap notebook, and for some reason Ubuntu will not install/go live. The CD boots okay, however when it gets to the loading hardware drivers part at startup it will not progress. The basic specs of my notebook are are: Compaq F551au, AMD Turion 64 X2 Dual-Core 1.6Ghz TL-50, 80GB 5400RPM Hard Drive, 512MB DDR2 RAM, Nvidia GeForce Go 6150.

I am trying to install the 7.04 (AMD-64) version and I have updated the BIOS but still no luck. I am kinda gutted because I never had any troubles with my older hunk of junk!

I hope someone can help, Cheers!

Luke.

---

### Post by Kilz on 2007-09-19
> **lukeminus said:**
> Hello. 

I just purchased a new cheap notebook, and for some reason Ubuntu will not install/go live. The CD boots okay, however when it gets to the loading hardware drivers part at startup it will not progress. The basic specs of my notebook are are: Compaq F551au, AMD Turion 64 X2 Dual-Core 1.6Ghz TL-50, 80GB 5400RPM Hard Drive, 512MB DDR2 RAM, Nvidia GeForce Go 6150.

I am trying to install the 7.04 (AMD-64) version and I have updated the BIOS but still no luck. I am kinda gutted because I never had any troubles with my older hunk of junk!

I hope someone can help, Cheers!

Luke.

Pressing f2 and f3 will give booting options 
apci=off noacpi seem to be recommended as helping lots of laptops boot.

---

### Post by lukeminus on 2007-09-19
chur chur thanks, will try now. What is *apci* anyway?

---

### Post by John.Michael.Kane on 2007-09-19
> **lukeminus said:**
> chur chur thanks, will try now. What is *apci* anyway?

To make use of the commands post restart your machine with the ubuntu cd, and at the boot/install menu (make sure to hit F6 first).
```
nosplash noapic nolapic
```
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

As far as what each command does.
```
Option: nosplash

Impact: Disable the "Graphical Boot Process" 

Option: noapic

Impact: Disable the "Advanced Programmable Interrupt Controller (APIC)".

Option: nolapic

Impact: Disable the "local APIC". 
```

---

### Post by lukeminus on 2007-09-19
Cheers guys, that worked sweet as. Backing everything up now and getting completely rid of vista! Hooray

---

