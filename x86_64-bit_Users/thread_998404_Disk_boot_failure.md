---
title: "Disk boot failure"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by Nugget_Mon on 2008-11-30
Hello All,
I am trying to get to the bottom of this problem. I left my computer on while I went to run some errands, when I got back the screen was frozen, like when the screen saver gets hung up. I shut it down and didn't worry about it much. When I re-booted this morning all I got was the "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".
My system is:
Ubuntu 8.04 on /dev/sda1
Kubuntu 8.10 on /dev/hda1
AMD64 X2 4400+ @2300MHz

So far this is what I have tried(all end with a reboot and the error):
1. Went into BIOS, no SATA drive found but IDE slave was found.
2. Used the Live CD to boot, main SATA drive still not found, but I could mount the slave and read the drive.
3. Made the slave drive the Master, and disconnected the SATA and the DVD-RW, made sure the changes were reflected in the BIOS.
4. Updated the BIOS.
5. Made a GRUB boot USB drive.

I'm out of ideas, anyone else got some?

Thanks,
Mon

---

### Post by cariboo on 2008-12-01
I would suggest you go to your hard drive manufacturers web site and download the diagnostic tools. It sounds like you suffered a hard drive failure, but use the diagnostic tools just to be sure.

Jim

---

### Post by felker2 on 2008-12-01
> **Nugget_Mon said:**
> 
So far this is what I have tried(all end with a reboot and the error):
1. Went into BIOS, no SATA drive found but IDE slave was found.
2. Used the Live CD to boot, main SATA drive still not found, 

Did you check the SATA cable (on both sides), and the SATA power cable? Did you try other cables and other connector positions?

Is the SATA drive detected in another system?

---

### Post by Nugget_Mon on 2008-12-01
> **cariboo907 said:**
> I would suggest you go to your hard drive manufacturers web site and download the diagnostic tools. It sounds like you suffered a hard drive failure, but use the diagnostic tools just to be sure.

Jim

Could be, but if it were just the drive, I think when the IDE drive was hooked up as Master the Kubuntu should have loaded.

---

### Post by Nugget_Mon on 2008-12-01
> **felker2 said:**
> Did you check the SATA cable (on both sides), and the SATA power cable? Did you try other cables and other connector positions?

Is the SATA drive detected in another system?

Yes to checking the cable, both sides. All positions on the motherboard were tried as well. Same result.
No other system as yet to check the drive on, will have to get an adapter for my laptop.


I thought about using G-parted to detect the disk. It comes up with a repeating error, something like:
: SATA link down
: hard resetting link
There's more but I can't recall off the top of my head, and I'm not near it.

---

