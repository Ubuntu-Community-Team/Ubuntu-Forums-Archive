---
title: "Ubuntu 6.10 USB Freezes"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by NilsJeppe on 2007-02-13
Hi Guys,

I am having a serious problem with Ubuntu 6.10: USB doesn't work. I mean, as in, not at all. While all my usb hubs are detected on bootup, the system displays "read errors" when booting. I do get the Gnome interface, and I am able to get the installer to start via an old ps/2 keyboard, but once it starts to modprobe any usb kernel drivers, the modprobe process hangs (unkillable).

Now, I have found some hints via google to turn off usb probing; but my entire system is built around USB. I have USB scanner, pen tablet, mouse, keyboard, external drives, everything. So turning off USB is not acceptable.

System: Athlon 64 x2, dualcore 2.0 Ghz (3800+ I believe), Asus A8N-SLI premium Mainboard (nForce 4), 3GB Ram

Does anybody have a good working solution for me?



Thanks,
Nils

---

### Post by seanwnz on 2007-02-16
This helped me get my USB stuff working:

[http://www.ubuntuforums.org/showthread.php?t=227412](http://www.ubuntuforums.org/showthread.php?t=227412)

Hope it helps.

---

### Post by John Jason Jordan on 2007-02-16
> **seanwnz said:**
> This helped me get my USB stuff working:
[http://www.ubuntuforums.org/showthread.php?t=227412](http://www.ubuntuforums.org/showthread.php?t=227412)
Hope it helps.
Thanks to all you guys for the suggestions. I have also been having problems with USB on my Compaq R3240 laptop. But I know it's not a problem with Edgy because it has been going on since I started over a year ago with Hoary. And I have a Logitech wireless optical mouse and it never fails me. My problem is when I transfer lots of stuff quickly over USB, as when I do a backup to an external USB drive. (Regular drive, not a flash drive.)

I tried pci=assign-busses and noapic irqpoll pci=routeirq, but each time I just get error messages. I rebooted the computer and then, when the Grub menu came up, I hit e to edit, entered a new line, and put the command in the line, then hit b to boot. Grub just gives me an error message that it can't understand the command.

Evidently I'm stupid. Apparently these lines don't go in the Grub menu.lst file. So where do they go?

---

### Post by NilsJeppe on 2007-02-17
Unfortunately this didn't get my USB to work.

---

### Post by NilsJeppe on 2007-02-22
I have now taken the time to test the 32bit version. And lo and behold, it works "out of the box" where no trick made the x64_64 bit Ubuntu work with my USB. Conclusion: x86_64, go back to the drawing board! :-(

---

