---
title: "Brand new PC. Ubuntu won't boot"
date: 2007-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by seamusandboo on 2007-07-20
I tried researching the issue I'm having before I posted this but couldn't find any information on the issue. 

I just put together a brand new computer with the following specs:

Mobo: Biostar T-Force 550 SE
Processor: AMD Athlon 64 X2 Dual Core 5600+ 2.8 GHz
Memory: 2GB (2 x 1GB) G.Skill DDR2 800MHz PC6400 SDRAM
Video Card: EVGA GeForce 8600GT 256MB PCI-E
Hard Disk: Seagate Barracuda 200GB IDE 7200RPM 8MB cache
Optical Drive: Pioneer DVR-110D DVD-RW

I downloaded and burned the ISO for Ubuntu 7.04 for AMD64. When I try to boot from the CD, it gets to the welcome screen with the options. When I select to start from the CD, it starts loading the linux kernel, but when it's supposed to go to the Ubuntu loading screen, the screen just goes blank and all disk activity halts. Then the monitor goes on standby as if the computer was turned off and it stays like that until you reset the computer.

I am puzzled as to why Ubuntu won't boot. I'm sure that this CD works as I tried it on a different 64-bit processor computer and it worked fine. 

If anybody has any ideas it'd be highly appreciated.

---

### Post by Cappy on 2007-07-20
Try using boot parameter ```
nosplash
```
See if that works.
If that doesn't try this:
```
nosplash noapic nolapic
```

---

---

### Post by cprofitt on 2007-07-20
hit F6

and do what the poster stated above.

If that does not work you can also:

> 
hit F6 and edit the parameter that says silent-splash -> break=bottom
when you get to a command prompt type:

chroot /root nano /etc/X11/xorg.conf

edit out the NV driver with vesa

cntl+o - hit enter to save
cntl+x

type exit at the command prompt.


---

### Post by seamusandboo on 2007-07-21
The nosplash parameter made it work. I'm posting this from Ubuntu now. 

Thank you so much for the tips.

---

### Post by mbrady on 2007-07-23
I was having the same problem. The 32-bit CD booted up just find without any modifications, but the 64-bit CD and installed versions would show a blank screen. I was glad to find that using the "nosplash noapic nolapic" options worked like a charm on the CD -- but when I added them as boot option lines in GRUB, the screen went to standby and then the computer restarted back to BIOS... wierd. Why are the options not working, when they clearly worked on the live cd version?

---

### Post by Cappy on 2007-07-23
Hi, my guess is that you may have accidently added them onto the wrong line or may not have used sudo when you edited it and it did not save.
I recommend this guide for additional information (such as how to add this with only grub without booting to ubuntu or a live-cd first):
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

To edit:
```

gksudo gedit /boot/grub/menu.lst

```

Where you add it:
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
**kernel		/vmlinuz-2.6.20-16-generic root=UUID=Long_Number ro quiet nosplash noapic nolapic**
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Long_Number ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Long_Number ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Long_Number ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

```
I bolded the line I use to boot.

---

### Post by daveshields on 2007-08-12
Hi,

I have the same board and had similar problems. You need to update the BIOS on the motherboard. The latest (3 Aug 2007) version is  N5TBA626.BST and can be found at  [http://www.biostar.com.tw/app/en-us/t-series/bios.php?S_ID=180](http://www.biostar.com.tw/app/en-us/t-series/bios.php?S_ID=180) . You need to copy that file to a floppy and use the BIOS option to update the flash memory. When it reads the floppy it will display the name of the file. Then you need to press Enter.

Updating the BIOS made all my problems go away. I was able to install Ubuntu 7.04 and also OpenSuse 10.2

---

