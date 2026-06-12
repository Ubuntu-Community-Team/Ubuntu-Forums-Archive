---
title: "Major trouble on x64"
date: 2008-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Svenstaro on 2008-02-13
Hey,

got major trouble here trying to install Ubuntu x64.

Specs:
Gigabyte P-35 DQ6 (latest BIOS)
Intel Q6600
Geforce 8800GTX
4x1GB 800mhz RAM
750GB Seagate 7200RPM SATA
Floppy drive
LG IDE MultiDVDWriter


What works and what does not?

Well, booting the LiveCD without additional parameters does not.
SOMETIMES I manage to boot it using the acpi_use_timer_override boot option and eventually I managed to install it like that.
When I try to boot the LiveCD without these parameter it would show 
"Kernel alive" 
"Kernel mapping --lots of numbers--"
and then suddenly reboot.
Taking away the 'quiet' option it says some stuff about ACPI and timeouts. 

I have tried several other ACPI/APIC disabling commands though with no success so far.

Anyway, as you may have guessed the system that I kinda managed to install doesn't really run so stable, in fact I can hardly boot it. By 'hardly' I mean it works in 1/4 of the times I try with the acpi_use_timer_override option.

The 32bit LiveCD boots up fine, though with a lot of involuntary beeps and it's rather painful to work with.

Searching the forums It looks like a _LOT_ of people experience the same problems and all come up with different solutions if at all. Most threads do not contain any posts, I hope this one gets some.
I have yet to try out removing the floppy as stated here: [http://ubuntuforums.org/showthread.php?t=577399](http://ubuntuforums.org/showthread.php?t=577399)
though I don't think it's a real solution.


Help is *very* appreciated.

EDIT: 
Looks like the lads over here [http://ubuntuforums.org/showthread.php?t=694805](http://ubuntuforums.org/showthread.php?t=694805) and here [http://ubuntuforums.org/showthread.php?t=658155](http://ubuntuforums.org/showthread.php?t=658155) are getting the same problem and are also using Gigabyte boards. Looks like that's the problem. Any ideas?

---

### Post by kaivalagi on 2008-02-13
I had problems booting the 64 bit live cd and then the install, it stemmed from the usplash setting in grub, you need to change the grub switch 'splash' to 'nosplash' (make permanent in /boot/grub/menu.lst). There is a problem with the 8800 graphics card on boot I think.

I got the usplash screen working eventually but to get going you'll need to use the alternative boot options. I tried lots of things, then after a reinstall of usplash from apt it worked with the splash setting again...?

Hope that helps, hard to know until you try I suppose :)

---

### Post by Svenstaro on 2008-02-14
I kind of fixed my problems now by running the new Hardy Alpha 4 but this is hardly a solution. I'll leave it like this though if no further problems arise.

---

### Post by kaivalagi on 2008-02-15
Do you want to mark the thread solved on this basis?

---

### Post by Svenstaro on 2008-02-15
Yup, just did.

---

