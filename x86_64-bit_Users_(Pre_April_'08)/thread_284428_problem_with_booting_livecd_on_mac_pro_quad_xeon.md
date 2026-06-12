---
title: "problem with booting livecd on mac pro quad xeon"
date: 2006-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by marianne on 2006-10-25
Hello!:-k 
I'm trying to boot my intel mac pro quad xeon with the ubuntu livecd x86_64. I doesn't work att all. 

I have now installed the i386 version of ubuntu and it works fine, but I wan't all my cores to be used. Does anyone know why it doesn't work?
Is it away to work around this problem?
Greatful for help
Marianne:

---

### Post by John.Michael.Kane on 2006-10-25
Have you tried the alternate install x86_64 cd?

There have been issues with the live install cd for some folks hardware.

---

### Post by marianne on 2006-10-26
Hi!
With the Dapper Drake normal x86_64 cd i se the menu and when I choose run live or install it hangs on mounting root file system, the second item.

I've also tried the alternate cd but there it gives me strange messages and hangs after a little while.

I'm thinking of changing the kernel but I'm not sure yet.

I also tried with fedora core 6 x86_64 and it also hangs.

---

### Post by sergiez on 2006-11-17
> **marianne said:**
> Hello!:-k 
I'm trying to boot my intel mac pro quad xeon with the ubuntu livecd x86_64. I doesn't work att all. 

I have now installed the i386 version of ubuntu and it works fine, but I wan't all my cores to be used. Does anyone know why it doesn't work?
Is it away to work around this problem?
Greatful for help
Marianne:

In order to use all your cores you must only install the linux-686-smp package. In fact is the same package as linux-686, but you will see the SMP in your synpatics :-)

If you want a 64bits systems then the thing is more complicated. There is a thread in the Apple-PPC forum called MacPro where you will find more information.

---

### Post by sergiez on 2006-11-17
> **marianne said:**
> Hi!
With the Dapper Drake normal x86_64 cd i se the menu and when I choose run live or install it hangs on mounting root file system, the second item.

I've also tried the alternate cd but there it gives me strange messages and hangs after a little while.

I'm thinking of changing the kernel but I'm not sure yet.

I also tried with fedora core 6 x86_64 and it also hangs.

Pass "acpi= force irqpoll" to the kernel when booting. It runs on Ubuntu Edgy (64bits) and someone has also reported that runs on Fedora Core 6.

---

### Post by daedius on 2006-12-22
Is this accurate for people with PIONEERs?

---

### Post by sjatkins on 2007-03-25
My setup is a Mac Pro with an Apple 23 inch monitor.  I installed fine from the Feisty Fawn Alt AMD64 cd.  On boot though the typical orange Ubuntu login screen is sort of slowly flashing and there is no window or text on it.  Just for the hell of it I entered my credentials blind to see what would happen next.  It switches to a non-pulsating grayish-white screen again with no text or windows or other decoration or mouse cursor.  At this point I rebooted into safe mode and looked at the xorg.conf.  It is running the nv driver and seems basically sane.   Anyone have this experience or have some idea what could be going on and how to get past it?  Resolution is 1920 x 1200.

I then tried to install from a live cd of the same configuration.  It gets totally wigged out and produces diagonal stripped lines on the screen.  So at a guess Feisty Fawn is somehow misreading standard Mac Pro graphics hardware.  

Any thoughts or cures out there?

---

