---
title: "AMD Athlon 64x2 Install Problems"
date: 2007-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by FloSynergy on 2007-06-17
Hi all,

I recently acquired a new box with the following specs:

NF61S Micro AM2 SE Motherboard
AMD Athlon 64x2
80Gb Samsung IDE HDD
2 GB Ram

Tried to install ubuntu 6.06 from disc. 
Get to startup page, with all the different options. If I choose option 1 run/install ubuntu, the splash page appears, and immediately freezes -no activity whatsoever.
Ditto for check disk option.

After surfing various posts, I tried booting using various options: acpi=off; noapic; nolapic.
Using this option, the splash screen appears, pauses briefly as the hdd is referenced, then proceeds to load up - all seems well, until:

the process bombs out and dumps me in a garish blue vga-land, saying that the x-server has failed to start. Log entries claim that there is no screen, that the PCI indicated doesn't exist. Xserver is now disabled, which dumps me into text-based linux (running from disc, i assume). from here, i am unable to continue the installation.

i have tried running this with various other boot options:
noapic nolapic pci=irqroute pci=noacpi acpi=off pci=acpi fb=false irqpoll (thanks, SD Plissken)

the result remains the same.

does anyone have any idea how to resolve this? i really wanna run ubuntu on this system, and there is no way that i'll host another virus like windows on my system ;-)

be well,

flo

---

### Post by Ocxic on 2007-06-17
try the alternat cd, that may work better for you,.
try checking you bios settings, try a make sure averything you  can put on auto is on auto, and just do a general check, you can even try resetting your bios to defaults.

---

### Post by FloSynergy on 2007-06-17
i tried again, this time chopping out the boot option relating to the splash page and adding apic=off - this seems to have worked.

ubuntu booted up, with the install icon on the desktop.

used this, have divvied up the hard disk into various partitions,

it is now busy installing/copying files.

i'll know in about 15mins if it has worked or not...

bingo!

it seems to be working fine - now it's just a matter of installing software and doing all the config!

thanks for your help, SD Plissken!

be well,

Flo

---

