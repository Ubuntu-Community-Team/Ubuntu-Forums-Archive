---
title: "Why do I get some APIC error on bootup if I &quot;Enable mouse/keyboard&quot; in my MoBo bios?"
date: 2008-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by inktri on 2008-01-04
My 64-bit Ubuntu 7.10 keeps on rebooting while trying to load on startup. Another strange fact to add is there's a 1 in 20-30 chance my computer will successfully login and that doesn't correspond to the flags I append to the end of the kernel boot command (as described below) -- it's completely random!. This problem exists for everything: trying to start Ubuntu via the Live-CD, via hard drive, via recovery mode. I also believe this is a 64-bit problem because my 32-bit Live-CD works perfectly

I've checked the threads on these forums and have tried what people have suggested with little success:
> 1. appending noapic nolapic nosplash to boot sequence
2. updating my BIOS
3. appending noapic nolapic
4. appending noapic
5. acpi=off
6. acpi=ht


My relevant computer specs:
> 64bit Ubuntu 7.10, Gigabyte P35-DS3L (with latest BIOS), Q6600, GeForce 8400GS, LSI 21320 SCSI hba, 2x Hitachi 15k300 Ultrastar hard drives.

During bootup I'm getting:
> Inquiring remote APIC #2...
... APIC #2 ID: failed
... APIC #2 VERSION: failed
... APIC #2 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 2/3 APIC 0x1
Not responding.

Inquiring remote APIC #3...
... APIC #3 ID: failed
... APIC #3 VERSION: failed
... APIC #3 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

Inquiring remote APIC #1...
... APIC #1 ID: failed
... APIC #1 VERSION: failed
... APIC #1 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

The only solution to the above problem is to disable USB mouse/keyboard during bootup in my during bootup (USB mouse/keyboard still works, it's just I can't use them before Ubuntu is loaded -- in the Live CD, etc.) in my motherboard bios.  So I guess one solution would be to rely on a PS2 keyboard for that stuff; however my USB keyboard is really nice and I'd only like to bring that back to college. 

Anyone know a remedy?

Thank you very much

---

### Post by ushimitsudoki on 2008-01-28
Ubuntu 7.10 amd64, Gigabyte P35-S54, Intel Core2 Quad 6600, GeForce 8800GTS 512.

I have the same exact problem, 9 out of 10 or more boots fail with the same error text you mention. If it does boot though, all seems to work as expected. I have experienced this problem on BIOS revisions 9 and 11. I did not notice it before that, and I did not use revision 10.

The only difference I have is my mouse and keyboard USB support is disabled by default in the BIOS (even though I am using a USB mouse and keyboard).

I too tried all sorts of noapic/noacip/irqpoll switches from GRUB. If I disable all USB support in the mobo BIOS, I can boot every time - or at least every time I tried, which was about 10 times in a row.

I have not tried the 32-bit Live CD. It's gotten to the point where I am scared to reboot my machine for the frustration of not knowing if it will come back up!

Extremely frustrating because it does appear that it's a random thing on whether the reboot will succeed or not. Posting to the thread in hopes someone has an answer!

EDITED TO ADD:
It appears that disabling "Legacy USB Support" has fixed the problem.

---

### Post by amanfredi on 2008-02-09
My friend and I were having the same problem and just got this running tonight. 

Core 2 E8500
P35-DS4 rev 2.1 F11 Bios
8800gt 512

The system seems to be working 100% with legacy usb, usb keyboard, and usb mouse all disabled in the bios.

With usb keyboard and usb mouse enabled (didn't test legacy usb), nosmp and acpi=off were required to boot successfully (plus nosplash if the graphics card drivers are not available). Unfortunately, this method results in only one processor core being detected. 

I have no idea why this might be.

P.S. We also discovered that the Ubuntu livecd 'helpfully' auto-mounted the swap partion on the disks that we were trying to set up for raid. If you get errors during your raid configuration, check that first.

-Anthony

---

### Post by gohanssjn on 2008-02-12
EXACT SAME PROBLEM HERE.

God, I thought I was the only one :(

Guess I'll go back to F4 for a while then!

---

### Post by fjgaude on 2008-02-13
I have the same F11 DS4 MB... I use USB mouse but not keyboard, but I don't have such enabled in the BIOS. I have all USB options enabled, including Legacy.

That could be the difference. F4 didn't likely have the features that F11 has, and "bugs" have been introduced. F12 is being awaited! <smile>

---

