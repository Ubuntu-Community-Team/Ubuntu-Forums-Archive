---
title: "can't install ubuntu x64 at all"
date: 2008-07-28
forum: x86 64-bit Users
---

### Post by smooth3006 on 2008-07-28
i need help here guys, i can't install ubuntu at all on my pc for some reason. all it does is hang on the boot screen and doesn't load past that. then after a few minutes it goes to a blank screen and starts giving me error codes. at first it was I/O errors pointing to a floppy drive that i don't even have installed. then i get these errors :

ata 1.00: status :drdy
ata revalidation failed errno=5

can someone give me any advice here ? i even tried the alternative desktop cd with no luck, it does install then i get the same problems / errors.

---

### Post by Sef on 2008-07-28
1) Have you checked the disks?  Go down to check disk for errors.

2) Did you burn them at 4x or less?

---

### Post by nikgare on 2008-07-28
You might be better off using the **Alternate** install disk

---

### Post by IwasAnex on 2008-07-28
Can we get some more info on your machine,  ie processor, hd, board, display, stuff like that? Its hard to help without the full story.

---

### Post by Neo0351 on 2008-07-28
i think you are having the same problem many of us are having so try this, when u boot the cd and it askes u what to do, press F6 and add this after quiet splash
```
all_generic_ide floppy=off irqpoll
```
should look something like this
```
quiet splash all_generic_ide floppy=off irqpoll
```
if that works, when you reboot and you get to the grup menu, hit esc and then hit the "e" key and arrow down to the kernel line and hit "e" again. then enter all_generic_ide floppy=off irqpoll then hit enter, and then "b" that should get you booted, once booted
```
sudo gedit /boot/grub/menu.list
```
find this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
edit it to look like this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash all_generic_ide floppy=off irqpoll
```
save your changes and exit, then
```
sudo update-grub
```
after that you should be good to go

---

### Post by smooth3006 on 2008-07-28
here are my specs :

intel core2duo 6550.
OCZ Reaper HPC Edition 4GB DDR2 800 (PC2 6400) Dual Channel
nvidia geforce 8800GT 512MB. / thermaltake dual orb vga cooler.
DFI LANPARTY DK P35-T2RS LGA 775 Intel P35 ATX Intel Motherboard.
western digital 250gb & 80gb. 7200 RPM 8MB Cache SATA 3.0Gb/s Hard Drives.
acer 19" x192w widescreen lcd.
raidmax scorpio atx case.
cooler master extreme 500w psu.

i tried the fix mentioned above and it works but then i started experiencing alot of other issues with the install. i then tried to install kunbuntu x64 and the fix didn't work for that at all, won't get past the boot screen. 

yes i checked the disk for errors and burned at the lowest speed. it must just be a serious bug with x64 installs.

---

### Post by him610 on 2008-07-28
I experienced a similiar problem on an HP 64bit Turion laptop with both 64bit Ubuntu 8.04 and 64bit Suse 10.3; I had to revert to the 32bit version of Ubuntu 8.04.

Your mileage may vary.

---

### Post by smooth3006 on 2008-07-28
> **hgh9mrp said:**
> I experienced a similiar problem on an HP 64bit Turion laptop with both 64bit Ubuntu 8.04 and 64bit Suse 10.3; I had to revert to the 32bit version of Ubuntu 8.04.

Your mileage may vary.

yeah i figured it had something to do with x64 installs. it sucks because i need to utilize my 4gigs of ram. looks like ill wait for ubuntu until they fix this issue.

---

### Post by tuxxy on 2008-07-28
Damn this sucks, have you tried the alternate CD yet?

---

### Post by smooth3006 on 2008-07-28
> **tuxxy said:**
> Damn this sucks, have you tried the alternate CD yet?

yes and it installed on ubuntu x64 but after restart it just hangs at the boot screen. i know the person above gave the fix but i don't think you should have to do all of that just to get linux on your pc. besides as ive stated i had alot of other issues after i got it working.

---

