---
title: "HP printer problem on AMD 64 bit"
date: 2007-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by freemart on 2007-02-25
I recently got a new computer. I installed two hard drives with four operating systems, 32 bit XP Pro, 64 bit XP Pro, 6.10 with Gnome and 6.10 with KDE. Installation was easy for all four operating systems but had a little problem getting Grub right. I use the computer for engineering work and so need a wide carriage printer. I had a HP Deskjet 1120C. It installed o.k. on both Windows OS's but does not install correctly on Ubuntu. The install was done from the system settings, peripherals, printer menu in both Gnome and KDE. Everything seems to go o.k. but when I send a test page to the printer I get one line of garbage. I tried all of the different drivers offered, all result in the same problem. I noticed that the drivers in Windows are not the same ones that are used for 32 bit computers , however, they seem to be the same ones for Ubuntu 64 bit and 32 bit.

My system is Asus A8N-VM CSM?NBP motherboard with AMD Athlon 64, nVidia GeForce 6150B + nForce 430 chipset, nVidia 7300 graphics

Does anyone know what the problem might be?

---

### Post by John.Michael.Kane on 2007-02-25
This may help [http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_1120C](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_1120C)

---

### Post by freemart on 2007-02-27
Found the problem. Set up the bios on the motherboard for the parallel port for "NORMAL" and  not "ECP". Since a lot of you out there are using this motherboard this may help you.

---

### Post by fonsi2099 on 2007-11-28
Every time that I start my printer, HP PSC 1510 I get the test page, it does mean ones or twice a day I get the test page!  This is my home PC  my children working and playing with too.

 is there a way to turn off this printing of test page. 
:guitar:

---

### Post by fonsi2099 on 2008-03-06
Solved

---

