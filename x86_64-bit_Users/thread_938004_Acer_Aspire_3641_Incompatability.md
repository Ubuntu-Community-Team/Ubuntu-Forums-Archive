---
title: "Acer Aspire 3641 Incompatability"
date: 2008-10-04
forum: x86 64-bit Users
---

### Post by ChazZeromus on 2008-10-04
I think my PC is completely unable to run Ubuntu.  I do the following:

Try Ubuntu Live:  It goes through loading the kernel, then after that it detects hardware then when it gets to starting bluetooth, it just freezes there.  And when I leave the computer there to freeze it actually just blanks out the screen and nothing happens.

Installing:  Goes through the entire setup and stops at the end quarter of installation and nothing works, I can't move the mouse or anything.

This computer's model is only a few weeks old.  So, I guess a kernel update is needed?

Here are my computer specs:

Processor

    * Type Intel Core 2 Duo E4700 / 2.6 GHz
    * Multi-Core processor technology Dual-Core
    * 64-bit processor Yes
    * Installed Qty 1
    * Max processors supported 1

Cache Memory

    * Type L2 cache
    * Installed Size 2 MB
    * Cache Per Processor 2 MB

Mainboard

    * Chipset type NVIDIA GeForce 7100 / nForce 630i
    * Data bus speed 800 MHz

RAM

    * Installed Size 3 GB / 4 GB (max)
    * Technology DDR2 SDRAM
    * RAM form factor DIMM 240-pin
    * RAM configuration features 1 x 1 GB + 1 x 2 GB

Storage Controller

    * Type 1 x Serial ATA - Integrated
    * Controller interface type Serial ATA-300

Storage

    * Floppy drive type None
    * Hard Drive 1 x 320 GB - Standard - Serial ATA-300
    * Hard Drive (2nd) None
    * Hard Drive (3rd) None

---

### Post by ChazZeromus on 2008-10-04
Bump

---

### Post by Merk42 on 2008-10-04
Did you check the disc for defects?

---

### Post by CouchGuy on 2008-11-29
I also have this problem. I have the acer aspire am3641-ed7200a. I have found that if I unplug the usb speakers, it will boot past the bluetooth line without problems, but when it finishes booting, my mouse and keyboard do not work at all.

---

### Post by igsimon on 2008-12-29
anyone had any luck with this yet? I am thinking of buying one if UBUNTU or Kubuntu works on it

---

### Post by goxmir on 2009-02-20
same thing here. Got my new desktop two days ago, it is Acer Aspire AM3641-ED7200A and absolutely no luck installing Ubuntu, or any other distro...


Please HELP!! I HATE Vista, I don't think I can stand it any longer...

---

### Post by Mr.Goose on 2009-08-30
1. Restart your PC and hit DEL key as you boot.

2. In the BIOS, navigate to the Advanced BIOS Features part and change "Installer OS Select" to "Others" (as opposed to "Windows") . 

3. Hit F10 key & select "Yes" to save these settings. Reboot as normal.

4. Worked for me - at least it got past that Bluetooth hanging nonsense. Please let me know if it worked for you.

Caveat:- There is a separate issue with this machine that I've not figured out yet. That is, how to make the NVidia SATA work properly. I actually installed Ubuntu 9.04 onto a PATA drive, just to test it. But everything else works OK - including the display if you install the proprietary NVidia display drivers.

---

