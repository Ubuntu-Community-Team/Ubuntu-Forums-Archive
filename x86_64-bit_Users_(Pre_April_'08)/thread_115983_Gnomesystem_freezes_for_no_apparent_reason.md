---
title: "Gnome/system freezes for no apparent reason"
date: 2006-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yob on 2006-01-11
Hi,

I'm new to Linux and has a problem with my newly installad AMD 64-K8. My system freezes occasionally and I can't figure out what is causing it. There's no apparent connection, it happens with different programs running and sometimes directly after booting, sometimes hours after I boot.
When it freezes I've no choice but hitting the power button. Can't switch to a terminal (CTRL+ALT+1) or restart Gnome (CTRL+ALT+Backspace).

What really blows me off is that I've managed to get World of Warcraft running through Wine, and I can play the game for hours without these freezes occuring.

I've searched this forum and googled comprehensively to find a solution, but to no avail.

Any help will be greatly appreciated!

Hardware:
CPU: Sempron 3100+ AMD64
MB: MSI K8N Neo3
GF: Asus N6600 Silencer (GeForce 6600 Nvidia)

System
Ubuntu AMD64-K8
Nvidia-glx installed and enabled
Nvidia-settings installed

---

### Post by Jave27 on 2006-01-11
I had the same problem after installing my 6600GT and some new RAM.  Ended up messing around with the BIOS settings and manually setting them instead of leaving them at Auto and it fixed it.  I just installed the latest Beta version of the BIOS driver for my board (ASUS A8V Deluxe), and reverted to the Auto settings, and so far so good.  If you have another OS, does it freeze at all after being on for a while?

---

### Post by Bghmsh on 2006-01-11
I have the same problem with my system , but have managed to isolate it to the following I am runninh gdesklets to keep an eye on network activuty If I load to many sensors the system barfs, running the system without the sensors works just fine
I also have a triple boot system it only hangs in ubuntu !

---

### Post by Yob on 2006-01-12
I only have Ubuntu on the machine, so I don't know whether it would freeze or not. However I had the 32bit Ubuntu installed first (though only for a few days) and I don't recall having the problem then.

Which settings did you change in BIOS?

---

### Post by plg on 2006-01-12
What chipset do you have?

What memory timings did you change?

Are there any good guides to setting timings anywhere?

There are reported system hangs in at least two other threads in Amd64.

* Re: ups.....problems: "Many Lost Ticks"...
* AMD64 and NVIDIA 78000 system hangs...

/ Patric

---

### Post by Frobean on 2006-01-13
I had the same issue with my Amd64 x2 system. The problems went away when I disabled ACPI in the kernel.

If you want to try it, edit your /boot/grub/menu.lst file and add acpi=off to the kernel parameters

---

### Post by Yob on 2006-01-14
I've gone back to the AMD64-generic kernel and the problem seems to have disappeared.

UPDATE:
I'm back on the K8 one again. Apparently it was the Cool 'n' Quit function that my system disliked.

---

