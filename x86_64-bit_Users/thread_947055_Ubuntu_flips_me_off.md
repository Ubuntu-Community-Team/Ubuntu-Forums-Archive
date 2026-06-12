---
title: "Ubuntu flips me off :/"
date: 2008-10-13
forum: x86 64-bit Users
---

### Post by SunFanBoy on 2008-10-13
Hi guys. I got a new computer, all the best consumer level hardware, and both Ubuntu 32-bit and 64-bit refuse to boot at all from the livecd. It just drops to ash and doesn't let me do a thing. Specs are:

-Gigabyte GA-EP45-DS3 Mainboard
-8Gb Corsair Dominator DDR2 RAM
-1Tb SATA hard drive
-22x Samsung DVD-RW
-1Gb GF 9800GT, PCI-E 2.0, DDR3

I know it's not the hardware, as I managed to get OpenSolaris to boot, install and run with the only issue resulting from my lack of appropriate nVidia drivers. Anyone here know what's going on?

---

### Post by tjotser on 2008-10-13
Do you have the official ISO ?  
Are you burning at LOW speeds, on "certified" medias?
What kind of processor do you use ? (the 8GB of RAM tells me you need x64..)

---

### Post by SunFanBoy on 2008-10-13
I'm using a core 2 quad Q9550 with an 8.04.1 CD I got from ShipIt. I have the 32-bit CD as well

EDIT: This is probably unrelated, but my computer doesn't like my USB keyboard before it has booted an OS. Could this be contributing to Ubuntu falling down? I'm getting a PS/2 adapter today to see if it helps anyway

---

### Post by iponeverything on 2008-10-13
> **SunFanBoy said:**
> Hi guys. I got a new computer, all the best consumer level hardware, and both Ubuntu 32-bit and 64-bit refuse to boot at all from the livecd. It just drops to ash and doesn't let me do a thing. Specs are:

-Gigabyte GA-EP45-DS3 Mainboard
-8Gb Corsair Dominator DDR2 RAM
-1Tb SATA hard drive
-22x Samsung DVD-RW
-1Gb GF 9800GT, PCI-E 2.0, DDR3

I know it's not the hardware, as I managed to get OpenSolaris to boot, install and run with the only issue resulting from my lack of appropriate nVidia drivers. Anyone here know what's going on?

When edit the grub boot options, when the cd splash first comes up.

remove "splash and quite" maybe we can get an idea of what is going on with it by watching the kernel load.

---

### Post by SunFanBoy on 2008-10-13
EDIT: Sorry, just reread that post :( I don't have the net at home atm, so I'm going to have to wait for another couple of hours

---

### Post by swells5 on 2008-10-13
try downloading the "alternate" installation iso - burn to cd and see if you can install ubuntu from that.

---

### Post by Jouke74 on 2008-10-14
I had the "no-keyboard" problem as well with my new Logitech keyboard. Not really a joy since it's also not possible to get into the BIOS. I tried many things, but the only thing that worked was to use a USB to PS2 converter for the mouse, and leave the keyboard in the USB port. I read, but don't know if it is true, that legacy support only worked for one USB device (mouse or keyboard).Anyway, it may help you.


As mentioned before, try the alternate cd AMD64 and install in text mode. Then after install try to install the Nvidia drivers.
(one problem).

I know this sounds funny, but you may need to update your BIOS. (Just make sure you are comfortable with that before trying, because if done wrong it might mess up your motherboard). A few days back there was a post indicating that this solved the Ubuntu boot problem.

---

### Post by iponeverything on 2008-10-14
This might be the issue that your having.
See post #28 in this thread:

[http://ubuntuforums.org/showthread.php?t=828568&highlight=grub+generic_ide&page=3](http://ubuntuforums.org/showthread.php?t=828568&highlight=grub+generic_ide&page=3)

---

