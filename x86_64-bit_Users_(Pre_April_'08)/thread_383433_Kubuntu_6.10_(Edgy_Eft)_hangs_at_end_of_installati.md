---
title: "Kubuntu 6.10 (Edgy Eft) hangs at end of installation process"
date: 2007-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by johnerskine on 2007-03-13
Running the following

Dell E521
AMD Athlon 64 X2 Processor 5000 (2.60 Ghz, 512k)
Memory - Dual Channel 2GB (2X1024mb) 533 Mhz DDR2
Hard Drive - (500gb Serial ATA Non-Raid - 2X250gb) 7200 rpm Dual... 

I've been trying to install Kubuntu 6.10 for the past week on my new machine. Yesterday I managed to get the installation process going after using a DVD and disabling acpi. Everything goes fine until I get to the last prompt - this invites me to remove the disc, close the tray and hit enter.

I did this, and nothing happened, the machine locked completely and would not respond to any command. When I switched off the power and started up again, I got GRUB but it just took me as far as the Kubuntu splash screen with the blue vertical bars beneath, but with nothing happening.

Reinstalling was possible, but I had to repeat the acpi=off command, and it just took me to the same remove disc, close tray, hit enter prompt.

Any ideas what is happening?

---

### Post by Ravanous on 2007-03-13
Are you by any chance using an ATI video card?

---

### Post by johnerskine on 2007-03-13
Yes - it is - and I've just seen the fun and games some people are having with them!

---

### Post by Ravanous on 2007-03-13
The ATI  card was the biggest problem in my AMD 64 installation.

I followed Method 2 of the [cchtml wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") instructions.

I hope this helps you out.

(I currently have it running with the latest version of the Linux drivers available from ATI)

---

### Post by johnerskine on 2007-03-13
The installation process hangs before the system is usable - how is it possible to insert these scripts?

---

### Post by Ravanous on 2007-03-13
Did you try Ctrl+Alt+Backspace to get into commandline mode?

That is what I ended up doing to install the ATI drivers (using method 2, method 1 did not work for my X1600)

---

