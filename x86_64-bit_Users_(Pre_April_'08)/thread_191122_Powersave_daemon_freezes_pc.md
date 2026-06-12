---
title: "Powersave daemon freezes pc"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmontburns on 2006-06-07
hi

does anyone know how i can disable the startup of the cpu scaling daemon powersave as this always freezes my pc unless i do so.

have tried nopowernow on boot parameter with no success...

on gentoo i used nocpufreqscaling (as i recall !! ) as a boot option - note i need to stop this daemon launching totally or it messes everything up.

Mboard is Gigabyte GAK8NS sempron 3000 cpu.

cheers

cm

---

### Post by bulldog on 2006-06-07
Can't you simply put it out in the BIOS?

---

### Post by cmontburns on 2006-06-07
oddly its not in the bios settings anywhere - fact am beginning to think its not on my board somehow and it shud have been ROFL

saying that my mobo is not on the ubuntu supported list mind ...

shame now have to go back to mandriva 

:-(
](*,)

---

### Post by Hendrik van den Boogaard on 2006-06-07
Can't you reboot Ubuntu in 'safe mode' (that sounds like Windows :mad:) and remove the Daemon with 'apt-get remove powernowd' or something like that?

Or try to start ubuntu from grub with the added number '1' to the bootup line, so it won't start any daemons?

---

