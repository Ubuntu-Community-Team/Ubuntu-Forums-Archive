---
title: "Corrupted video, freezing with a black screen on boot after RAM upgrade"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by dbsanfte on 2008-04-26
This is a frustrating problem. My specs:

Ubuntu 8.04 64-bit
Biostar NF4U AM2G Motherboard
AMD X2 5600+
2GB (upgraded to 4GB) DDR2-800 RAM
Radeon X1950 Pro PCI-X 256MB

Now, I originally installed the system while I had 2GB of ram. Everything worked fine, I loaded up the proprietary ATI driver and all was well for a few months.

Today I got another 2GB of RAM, put it in...and the problems begin. System posts perfectly, BIOS reports 4GB. Windows XP Pro loads up fine, shows 2.75GB of RAM. 

Ubuntu, however, loads up with a corrupted loading bar. The bar background appears in the normal spot, but the "progress" as it fills, actually fills up lower on the screen...then I get weird green/blue corrupted text (I assume), squished vertically across a 1inch space on the monitor, spanning the middle of the screen.  Finally, once the loading bar is full, X tries to start (I use GNOME if that makes any difference), and hangs at a black screen. I can't switch to terminal either before or after this process. The system will respond to CTRL-ALT-DEL, but that's it.

Now, removing the RAM, Ubuntu boots up fine, all is well. Swapping the old RAM for the new RAM is also okay, Ubuntu works fine with 2GB, the DIMMs are okay. When I put all 4GB in, Ubuntu displays the above issues and hangs loading the X server.

I've tried popping out to 2GB, going in and disabling the proprietary ATI driver (it's now running generic VESA), and putting the DIMMs back in and booting with 4GB again...same issue. 

I'm really at a loss here. Any idea what could be causing this?

---

### Post by Bluekkis on 2008-04-26
> Windows XP Pro loads up fine, shows 2.75GB of RAM. 

Only that with 4GB installed or 3.75GB? Try with 2GB but now shuffle them around different memory slots, one of the slots might be broken if even windows is missing more than GB.

---

### Post by dbsanfte on 2008-04-27
Still not fixed. I've tried swapping sticks, single- and dual-channel modes alike, and booting up with 3GB, same problem in Ubuntu (Windows works fine as always).

Here's something curious though. If I disable Memory Hole Remapping in my BIOS, with all four sticks installed and running in dual-channel mode (4 x 1GB), it results in the BIOS reporting 2.75GB of RAM. Then Ubuntu will boot with no issues. 

Problem is, when I turn Memory Hole Remapping back on, changing nothing else, BIOS reports 4GB of RAM, back to the same problems as before (Ubuntu's weird behaviour as described above).

Memtest86 overnight on the full 4GB reported no errors.

So, I am really perplexed here. I'm running a 64-bit OS and can't address all 4GB of RAM.

---

### Post by Julius on 2008-04-27
Have you tried booting the live CD ? Try and report how much memory ubuntu sees there.

Also try adding the option "mem=4096" to the boot command... although I'm not sure if grub lets you change is during boot-up. I know you can change it in menu.lst for sure!

---

### Post by Bluekkis on 2008-04-27
Memory hole remapping is bit of a hack and in my experience rarely works correctly. Often many integrated devices refuse to work with it enabled. Try updating bios if you haven't done that yet.

---

