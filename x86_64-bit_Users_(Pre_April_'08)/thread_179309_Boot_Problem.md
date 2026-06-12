---
title: "Boot Problem"
date: 2006-05-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hensenshi on 2006-05-19
I'm having problems acutally installing Ubuntu. It's been quite a while since I've installed an OS, but I really don't remember having these problems. Just as I go through the boot process, hit enter, and text scrolls(too fast to read even a word mind you), the screen goes blank and my fans stop spinning. If I use the Ctrl+Alt+Del interupt key, it reboots and starts the exact same process over again, and continues to unless I take the install CD out. I'm currently running an AMD Athlon 64 Processor 3200+ and I'm using the 64bit install disk. Like I said, been quite a while since I've really messed with an OS, and I'm sure that I'm doing something really really stupid and I can't figure it out. So, someone point out my obvious mistake.](*,)

---

### Post by natman on 2006-05-19
You probably already know this but, have you tried hitting " F2" during boot, ( just while your manurfacture logo is up), if you need to just hold "F2" down from the moment you power on.
It should give you a BIOS screen, head to the section on boot order, make the CD-rom drive the preferred option for booting from.
Like i said this is very simplistic solution but i might just help.

If all else fails, i heard that getting a BIOS update can help, ( it worked for me when ubuntu could not power up hot plug usb devices) - just a though.

Have Fun !!
patrick

---

### Post by Hensenshi on 2006-05-20
[QUOTE=natman]You probably already know this but, have you tried hitting " F2" during boot, ( just while your manurfacture logo is up), if you need to just hold "F2" down from the moment you power on.
It should give you a BIOS screen, head to the section on boot order, make the CD-rom drive the preferred option for booting from.
Like i said this is very simplistic solution but i might just help.

If all else fails, i heard that getting a BIOS update can help, ( it worked for me when ubuntu could not power up hot plug usb devices) - just a though.

Have Fun !!
patrick[/QUOTE]

BIOS update... I'll have to try that.

---

### Post by flaran on 2006-05-21
Maybe also try setting vga to 771..

> linux vga=771

Instead of just hitting enter.

---

### Post by Hensenshi on 2006-05-23
So, strangly my BIOS is up todate. O_o Weird no?

And the VGA to 771 worked, for a while. I got through system bootup, past the BIOS, but then when I finally get to the Ubuntu bootup screen, it bombs out. It's really starting to bug me. ](*,)

---

