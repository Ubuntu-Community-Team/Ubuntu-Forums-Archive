---
title: "X11 fails to load (2.6.20-16) and computer freezes (2.6.20-15)"
date: 2007-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by pnotequalsnp on 2007-09-09
A fresh install of 64-bit 7.04 resulted in random freezes (firefox, updating, terminal) using kernel version 2.6.20-15.   I was able to update a lot of the system but this did not help.  The random freezes are NOT just the display.  Any combination of keys to try to get to the terminal/command line did not work.  Therefore, it must be the system that is freezing (it could be caused by X11 but my system feels the pain too).

I proceeded to update to kernel version 2.6.20-16 and now X11 crashes i.e. says "fix me".

If I go back and use the 2.6.20-15 kernel I do get X11 to work but the random freezes continue (immediate, 2minutes, 2hours).

Any help on what is going on would be great or maybe some tool to narrow down the problem.  

Setup:
Nvidia 8500 GT (used "envy" to install drivers)
Abit AB9 QuadGT (Bios v1.4)
Intel Quad Core Q6600 2.4 GHz
8GB DDR2 RAM
1 150GB Raptor
4 500GB Barracuda
...

---

### Post by ahuffman on 2007-12-22
I am receiving the exact same symptoms with my new system.

ABIT AB9 Quad GT
Intel Core 2 Quad 2.4 ghz
4GB Corsair DDR 800

Random lockups

I had to add irqpoll to the boot options to even get into X11.
Prior to that I was receiving an error message Unable to set xfer rate 0x41.  (roughly what it said).


I also have a NVIDIA card.  I just disabled the restricted NVIDIA drivers (which was the first thing I enabled prior to having issues booting i.e. my first boot into Ubuntu), so I will see what happens.

I've been trying to upgrade the system, but it locks prior to the installation of anything.
I'll post the results.

---

### Post by ahuffman on 2007-12-22
Definately not the restricted NVIDIA drivers.

I'm going to try to get the newest kernel before the system locks this time.

---

### Post by ahuffman on 2007-12-22
Well, I almost got the kernel upgraded before it froze, but unfortunately it froze prior to completion.
Now I have a completely broken install.

I'm reinstalling the entire system now.
I originally could not install from the live cd, and so installed from the alternate installation disk.
Now I found that if I add the irqpoll option by pressing F6 so the end of the line, I can get it to boot to the safe graphics mode.

Hopefully I'll have better luck this time around.

---

### Post by ahuffman on 2007-12-22
OK, I think I have it corrected now.
I have not yet had any more lockups.

I reinstalled the entire system and continued to have issues with lockups.
I tried another grub boot option which did not work.  (MEM=2048M)

I found another article that suggested setting the bios mode of the SATA controller to AHCI mode.
I did this and booted without the irqpoll boot option.

The system still locked up after a few minutes.
I went back and added the irqpoll grub boot option again and managed to get most of the 148 updates I had waiting for me.

The system locked up right at the gdm package, so I had issues getting back into X.

I had to run dpkg --configure -a from one of the tty's.
This picked up where the updating system left off, and corrected the X issues once I rebooted (tried restarting X a few times, but to no avail.)

I also ran sudo apt-get update and sudo apt-get upgrade to make sure I hadn't missed any upgrades.

So apparently with the new 2.6.22-14 generic kernel and irqpoll boot option I'm good to go on the Abit AB9 Quad GT board.

I'll post if I have any further lockups, but the lockups I had been getting were occurring within 1-5 minutes of logging into X.

-Andrew Huffman

---

### Post by ahuffman on 2007-12-22
After a little more testing it appears to be an issue with compiz.

I tried opening a few jpegs, and maximizing them.
As soon as I maximized, I received complete system locks.

I tested this twice (after reboots).

The third try, I completely disabled compiz-fusion and began opening jpegs, and ordinary files.
Everything seems to be functioning correctly with compiz turned completely off.

This is a rather unfortunate bug. :(

Oh well, they'll fix it eventually.

---

### Post by ahuffman on 2007-12-23
I was wrong again.

The lockups continue.
Check out this post.
[URL="http://ubuntuforums.org/showthread.php?t=587905&highlight=sata+driver+issues%3F"]
http://ubuntuforums.org/showthread.php?t=587905&highlight=sata+driver+issues%3F[/URL]

I found deleting the hidden nvidia file in /lib/linux-restricted-modules/
and removing the new nvidia glx packages and installing the old worked in conjunction with the acpi=off option so far.
I did receive lockups with just moving to the older nvidia glx drivers.
So try just the acpi=off option to grub first.
I'm sick of playing with it now.

sudo apt-get remove nvidia-glx-new
sudo apt-get remove nvidia-new-kernel-source
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-kernel-source
sudo nano /boot/grub/menu.lst

add acpi=off to your kernel= line

ctrl+o
ctrl+x
sudo reboot

PS: I re-enabled all of my advanced desktop settings and removed irqpoll from the boot options in /boot/grub/menu.lst

Seems solid so far.

I'll post if there's any further issues

---

