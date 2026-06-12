---
title: "Boot Issue: Grub Editing Most likely... need advice please."
date: 2007-05-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by youbuntwho on 2007-05-11
Hi,

Spec

AM2 64bit 6000+
Nforce570 chipset on MOBO
8800GTS
2Gb pc6400 DDR2

Insallation required noapic and had to ensure that all FDC options in bios were disabled or of null value.
nosplash helped in identifying what was needed in that instance.
Install went through fine from there, no problems.

The problem now is booting into the newly installed OS (fiesty64-desktop), it returns a blank screen (i.e. i cannot get to OS at all). I suspect grub attempts to load the splash screen but suffers from a case of epic failure.
I have read that I need to edit the grub boot options like noapic and no splash but I am not entirely sure what I am doing (CLI and BASH Noob here *raises hand*).
I get as far as hitting 'e' for editing but I do not know what to do from there as the instructions were a little vague.

Are there any links or anything that could assist me. Any advice (that involves getting the OS useable) would be valued.

---

### Post by mckryptyk on 2007-05-12
The last thing I wrote was really unhelpful, so here I go again.

I have something like this:

title		Ubuntu, kernel 
root		(hd0,1)                                                                                                                                                                              #(where the boot files are located)
kernel		/vmlinuz ro quiet splash
initrd		/initrd.img
quiet
savedefault

you need to remove the following:
"quiet splash"
*Do not remove anything else.*

Post back if you have any more problems.

Cheers.

---

