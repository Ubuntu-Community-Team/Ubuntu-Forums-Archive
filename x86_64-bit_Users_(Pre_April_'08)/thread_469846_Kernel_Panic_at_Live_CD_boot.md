---
title: "Kernel Panic at Live CD boot?"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by scarboni on 2007-06-10
Verified MD5 on AMD64 .iso.  Used two different CD's & two different .ISO burners and same result:  When choosing to start Ubuntu in normal or VGA mode from the Live CD it seems as though initrd & kernel are decompressing but then some quick flash message about live kernal at the bottom & "NO SIGNAL" on the monitor.  Keyboard caps & scroll lock lights flashing in sync (although not num-lock).  Preliminary research indicates kernel panic signal sent via these leds.

32-bit desktop CD loads fine.  Vista Ultimate 32-bit loaded fine on this machine.

Hardware:
MSI 7025 K8N-Neo Platinum with NForce3 chipset.
AMD64 3200 @ 2Ghz 
2x1GB DDR-1 RAM Dual Channel
1x250GB Seagate IDE
ATI X800 Pro 256MB which works great with 32-Ubuntu (even Compiz during Live CD boot)
Used BIOS -safe defaults on a 2005 release BIOS and successfully updated (flashed) to the most recent 2007 release with no change in behavior
Board supports raid but verified off.
Board supports SATA but all SATA disabled in BIOS

Tried Turning off IOAPIC completely in BIOS as well as using it in version 1.1 mode as opposed to the stock 1.4 version - no change.

I haven't tried a 64-bit version of Windows on this board yet but I'm starting to suspect there's nothing 64-bit about this system... :(

Any tips, comments, clues any/all would be appreciated.

---

### Post by Cappy on 2007-06-10
If you aren't able to boot to GNOME after install follow these instructions:
[http://ubuntuforums.org/showthread.php?t=464513&page=2](http://ubuntuforums.org/showthread.php?t=464513&page=2)

---

