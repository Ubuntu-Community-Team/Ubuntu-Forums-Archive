---
title: "Grub Error 22"
date: 2007-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by pnotequalsnp on 2007-09-08
"Error 22: No Such Partition"
"Press any key to continue"

I have just installed 7.04 (64 bit version) with the Alternate Install CD (I have access to both) because graphics did not work on the original one.  I rebooted the system as requested and I get this error.  I have read online about this error and obviously grub cannot find the right HD/partition where the OS is loaded.  

I do not have windows installed (this is a new build).  I have 4 SATA HDs installed (none formatted or used at the moment), 1 IDE HD where 7.04 is installed, and 1 IDE DVDROM (slave to the IDE HD).  Therefore I have hd0, hd1, hd2, hd3, and hd4 to choose from when executing grub.  

When I edit the kernel entry (by pressing e), I see that the "root" is "(hd4,0)".  When I go to the grub command line I find that there are no partitions on hd4 (I do this by typing in "root (hd4," and then pressing TAB to see all available partitions).  If I do this for hd0 (typing in "root (hd0,") I get my root partition and my swap partition (yay!).

So obviously grub thinks it should boot from hd4 when it should be hd0.  When I try to edit "root (hd4,0)" by pressing 'e' and modifying the entry, I try to boot, it fails and I find it has reverted back to hd0.  That is problem #1.

If I press b to boot, it finds the kernel and begins to boot but then the screen goes blank (monitor is shut off) after the kernel is loaded.  That is problem #2.

XFX GeForce 8500 GT 512MB DDR2
Abit AB9 QuadGT Motherboard - Intel Socket 775, RAID ready
CP2-DUO-Q6600 - Intel Core 2 Quad Q6600 Processor - 2.40GHz
500GB Seagate Barracuda SATA - 4 of these in total
300GB Seagate Barracuda - 1 of these total (OS drive)
OCZ Dual Channel 4096MB PC6400 DDR2 800MHz Memory (2 x 2048MB) - for a total of 8GB of memory

---

### Post by Cappy on 2007-09-08
Extra info: [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

On the kernel line take out "splash" for problem #2.

For problem #1 once you get into ubuntu edit /boot/grub/menu.lst and change the hard drive settings you have found to work.
You can do this with
```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by pnotequalsnp on 2007-09-08
Great response time.   Thank you for your help, it resolved both problems.  If there is a forum reward system, let me know, I'll send some karma your way.

---

