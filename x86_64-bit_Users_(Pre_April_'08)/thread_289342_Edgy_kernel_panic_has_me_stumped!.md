---
title: "Edgy kernel panic has me stumped!"
date: 2006-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by paulphillips on 2006-10-30
I've already raised a bug on this in Launchpad:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/69046](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/69046)

...but thought there might be some useful knowledge out there.  

I can't figure out what is causing the kernel (2.6.17.10) to panic.  I had Breezy 64bit working fine, with kernel 2.6.12, then I upgraded to Dapper, but none of the 2.6.15.x kernels worked - they all panicked in a similar vein to my bug as listed above, except I had to pass "pci=nommconf" to the kernel first. With this Edgy kernel, I don't have to do that, but it dies in the IDE DMA routines.

I'm using the MSI-RS480M-IL motherboard which uses ATI's Radeon 200M chipset. According to my googling, there have been issues with this chipset and IDE DMA in the past, but I was able to get DMA turned on for my drives in Breezy.

The panic output seems to suggest that the ide device code in the kernel is attempting to get DMA working for one/all of my drives, then when that fails for some reason, tries to "turn dma off quietly" but panics in the process. 

Even more strange, I tried the dapper i386 live/install dvd, and it booted up fine!  (I can't try edgy i386 as my system, as you might imagine is only half working, with no burner capability)

Has there been a change to the "atiixp" section of the kernel since 2.6.12 that is has been broken since, and only for 64 bit builds?

Drives:
80GB standard IDE (master channel 0)
20GB standard IDE (slave channel 0)
Pioneer DVR-109 (master channel 1)

PS. I've tried lots of suggested kernel options including: noapic, acpi=off, nolapic, pci=nommconf, pci=noirq, irqfixup and dma=off - all to no avail.

---

### Post by paulphillips on 2006-11-01
As a further update to this:

I tried last night to run up the Dapper DVD again with the "quiet" kernel option removed.  This enabled me to see all the kernel messages just prior to the panic.  It seemed to be printing out drive seek errors and finally something saying that dma was disabled on hda, just before the panic (at atiixp_ide_dma_host_off)

So... I thought, if hda is causing problems, remove it!  So I did.  I removed hda (80 GB normal IDE drive), and hdb (20GB normal IDE drive) and swapped the DVD to IDE channel 0.

It booted!  Not very useful, but it booted nonetheless.  Now the question is, does this info add anything useful?  And why would it not boot for an IDE HDD, but boot with no probs with just an IDE DVD?  Aren't they both IDE? ](*,)

---

### Post by kuja on 2006-11-01
It's really hard to say. Maybe the kernel is having trouble interacting with your drive, maybe it's a bios issue, maybe the drive is just going bad. There's so many possibilities of what could go wrong :(

---

### Post by paulphillips on 2006-11-01
> **kuja said:**
> It's really hard to say. Maybe the kernel is having trouble interacting with your drive, maybe it's a bios issue, maybe the drive is just going bad. There's so many possibilities of what could go wrong :(

The most puzzling thing about all of this is:
a) this setup worked on Breezy AMD64 (kernel 2.6.12-10)
b) this setup works with a Dapper 32bit Live DVD

So... I keep thinking that it has to be:
a) specific to 64 bit
b) specific to kernel versions >= 2.6.15

And yet... 
[http://www.ubuntuforums.org/showthread.php?t=191452&page=2](http://www.ubuntuforums.org/showthread.php?t=191452&page=2)
nicko7i doesn't experience this at all (although he does have SATA, not PATA).

---

### Post by kuja on 2006-11-01
My bets are on the current Linux kernel disliking your motherboard. Have you tried it with the kernel in edgy? (2.6.17)

---

### Post by paulphillips on 2006-11-01
Yeah - tried edgy (2.6.17-10) - exactly the same error unfortunately :(.

---

### Post by uniko on 2006-11-02
Maybe you should try the hdd manufacturers diagnose programs to make sure you don't have a faulty drive. All major manufacturers have their own programs, most of which are bootable cd type. I had similar problems (kernel panics) with a faulty maxtor drive before it totally crashed. Worth a shot anyway.

---

### Post by iyeo on 2006-11-05
This is weird.  I upgraded from Dapper to Edgy and I didn't encounter this error until I just tried to do a fresh install to sort out xgl/mesa/glx issue.  When I installed Dapper, the livecd booted fine and I had no issues.  When I upgraded, I had no issues.  I just tried booting the edgy livecd and I get the kernel panic/vfs error.  The CD won't do anything but kick back that error, even when I try to do a media check.  When I take the cd out and boot to my hd already installed with Edgy (upgraded from Dapper), I'm fine again.  I'm downloading the alternate livecd to see if it makes a difference.  I'm running amd64x2.

---

### Post by kuja on 2006-11-05
You should definitely check the md5s of the burnt media as you burn it. I have K3b verify that it burnt the cd/dvd okay when I do my burns, even though it takes a few extra minutes, it saves me so much trouble.

---

