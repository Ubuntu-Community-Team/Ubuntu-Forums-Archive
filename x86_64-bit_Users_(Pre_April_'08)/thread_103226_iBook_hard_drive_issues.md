---
title: "iBook hard drive issues"
date: 2005-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by kidcharles on 2005-12-13
Ok folks, my advising professor is having iBook (G3 I think?) issues. He's using OS 10.3 I believe. When he tries to boot it sticks at the Apple splash screen and gets no farther. Trying to boot up with CD 1 for OS X 10.3 by holding down 'c' doesn't even work. The Ubuntu Breezy Live CD does work though (go Linux!). I was able to mount the hard drive using "sudo mount -t hfsplus /dev/hda3 /mnt".  However, there is an error and only files up to 'B' alphabetically show up using 'ls'. What might be the problem here? Corrupt filesystem? Can I fix this with Ubuntu? Thanks.

---

### Post by ssam on 2005-12-14
you guys find the craziest problems :-)

looks like disk corruptions. though there is a small chance reseting the PRAM will help (boot with apple+alt+P+R help down until you have heard 3 or 4 chimes).

you could try the magical target disk mode. if your ibook does it. hold down T at boot and it should boot to a screen with a firewire logo. now the ibook pretends to be a firewire hard disk and you can plug it into another computer via firewire and mount it. you'll probably have most luck pluggin it into another mac, and macos x has good disk repair tools.

i have heard of a boot key sequence to load a disk repair utility, but i can't remember what it is, and i've never tried it.

good luck

---

### Post by chascon on 2006-01-12
> hold down T at boot and it should boot to a screen with a firewire logo. now the ibook pretends to be a firewire hard disk and you can plug it into another computer via firewire and mount it

I hope you don't take this to be chronological instructions.  Please read apple documents on the apple site for instructions.

---

