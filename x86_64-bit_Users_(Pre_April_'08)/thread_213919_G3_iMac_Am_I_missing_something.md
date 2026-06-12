---
title: "G3 iMac: Am I missing something?"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by L4m3r on 2006-07-11
Having been thoroughly impressed by (k)ubuntu, I am planning to switch my main system (a PC) in the near future. :)

In the mean time, though, I just happened to acquire a "graphite" imac G3 that a tenant left in one of my family's rental units in Vegas. 

The poor thing apparently has a software problem that the tenants didn't think was worth fixing, and was abandoned sans peripherals. Oh well, I don't think anyone is going to miss OS9. >_< I don't feel like paying for/dealing with OSX, and I figured kubuntu would be nice for my 16 year-old sister to be able to browse the web and such. After all, such an imac is perfect for the coffee table. ;)

Anyhow, I have no experience with macs or PPC systems whatsoever. I read on the forums that Dapper can't install directly on a G3 imac, so I got the PPC Breezy install disk and booted it. I get a boot menu, at which I hit enter, and then I get a weird sort of terminal, which suggests typing "mac-boot". This seems to kick me back over to the b0rked OS9, and I see a folder with an alternating Mac OS face and question mark.

Typing anything else, though, seems to start the actual loading process, but it fails with this message:

```
VFS: Cannot open root device "<NULL>" or unknown-block(0,1)
Please append a correct "root=" boot option
Kernel Panic: Not syncing: VFS: unable to mount root fs on unknown-block(0,1)
```

I tried adding a couple of random root= options, but nothing has worked. To put it plainly, I am completely lost. >_< I'm not even sure what/where I went wrong. So, any help, suggestions, advice, etc would be much appreciated. :)

TIA, L4m3r

---

### Post by linear on 2006-07-12
Not certain, but I don't think you're actually booting the CD - sounds like you end up at an Open Firmware prompt.

Did you hold down the "C" key after the startup chime?

Do you know the CD to be good? (iso file md5 checksum good, burned as image?)

---

### Post by L4m3r on 2006-07-12
I do get the open firmware prompt, yes. That isn't the CD? 

I do hold C when booting the system. I had thought that it could be a bad disc, so I had already tried re-burning it (at 16x). Results are identical.

---

### Post by linear on 2006-07-12
Nope, the Open Firmware prompt means the CD isn't booting.

Assuming the iso file is OK, and it really was burned as an image, you can try burning it at a slow speed (4x).

---

### Post by L4m3r on 2006-07-12
Ah. Just noticed something.

The CD DOES boot- I get the text Kubuntu message and the kernel menu. After I press enter, I get the open firmware screen.

What I noticed, though, was the error message in between- "ramdisk load failed!". Does this mean I don't have enough memory in the box? >_<

If this is the case, I noticed Dapper has an "alternate" version for installing on older/crappier systems, among other things. But, Dapper doesn't work (or so I'm told) and I don't see such a version for Breezy. 

I guess I'll give the Dapper "alternate" a go, and see what happens.

EDIT: Heh. Apparently, it was the RAM. I remembered that I have an unused Celly box in the spare room with a 64MB stick in it. I threw that in, and it booted fine. I'm installing now. :D

EDIT2: Finally installed, and KDE doesn't seem to work. It goes through the boot sequence until it tries to start kdm. The screen flickers, and then the nice kubuntu logo goes away and I see a plain-text screen of the loading sequence, which has stopped moving. I'll look around the forums for an answer...

EDIT3: fixed it, with help from another thread that linear resolved. Thanks for all the help, linear ^_^

---

