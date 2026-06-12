---
title: "Cannot get to work my Parallel port with Wine 1.0 under ubuntu 8.04"
date: 2008-07-28
forum: Wine
---

### Post by moranpb on 2008-07-28
Can someone help me i can't seem to make my parallel port to work with wine i need it to program a eeprom so so i need to direct write to the port. i did like they said in the wine documentation ln -s /dev/lp0 lpt1 in the dosdevice directory and it is still not working 

when i dmesg i get 

dmesg | grep parport
[   32.739824] parport_pc 00:0b: reported by Plug and Play ACPI
[   32.739876] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   39.646471] lp0: using parport0 (interrupt-driven)

and my program is set to 0x3bc but still cant write i have to do something wrong please help.

Patrick

---

