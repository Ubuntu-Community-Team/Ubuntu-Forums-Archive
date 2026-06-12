---
title: "Can't install Dapper Drake on iMac 233... Not even Breazy..."
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by PsychoSync on 2006-03-24
When i boot the Dapper Drake Flight 5 CD, right after the loading of the kernel, more precisely the ram disk, it stops and there is this white Open Firmware screen. 

It gives me this error: Can't locate device-tree chunk

I tried booting with video=of...... thing, but no luck...

What's the problem?

iMac 233Mhz rev-B
160 m RAM
40 g HD

Breazy boots the CD, installs perfectly but at reboot when it tries to load kernel, it fails showing something like this: /pci@80000000/mac-io@10 ... /vmlinux : input/output error. So the install process does not seem to detect hd and partitions setting correctly?

I changed my old 4,3 g HD for a Maxtor 40g...

ps.: Yellow Dog Linux does something similar, it install ok but at reboot it can't find the kernel, same error but instead of "i/o error" its "invalid device".

---

### Post by imacQ on 2006-04-23
help] have burned second (dapper flight-6](*,)  iso disk and get this error after booting the cd, and hitting return button goes to open firmware and says "can't allocate initial device-tree chunk". what to do? anybody got ideas??? pleeeeeeease.  

prior to this i had breezy running dual boot w/ os x quite well on this imac for several months. i really want to try dapper on this computer before moving to my imac g3 600. all suggestions greatly appreciated! 

:-k  i guess i could try installing breezy again and go from there to updating, but would rather not spend that amount of time seeing how i've got several hrs. into this operation already. anybody go info?

---

### Post by Kalif on 2006-07-26
I got almost the same config as PsychoSync except
rev-a and 80G hard drive.

As far as I remember I got the same error message as
you when trying to install Warty which is the newest
CD I have ever been able to load on my imac. Hence
it is kind of rewarding to see that you at least have
been able to run the installation.

From what I have been able to deduce from several
mac-oriented forums having the both partition _completely_
within the first 8 gigabyte of the disk seems like
a wise first step when installing. De Gentoo paradigm
of having a separate boot partition seems as valid on
this kind of machines as it is for x86:s.

And, no, I have not been able to boot any newer CD:s
than Warty, sorry. Did you do anything "special" to
do so? Fancy open firmware commands?

I know burning CD:s at low speed increases the likliehood
that an old reader will be able to pick up the filesystem.

/r

---

