---
title: "Hard Disk device not detected ( gparted )"
date: 2007-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Szabo on 2007-01-12
Trying to install ubuntu edgy eft via the live CD.

Using the Install Icon the automatic partition select thing comes up then is blank, click manual and nothing else appears.

System | GParted

"No Devices Detected"

Any suggestions? the fact this is on a 64bit system I feel is irrelavent, will move accross to x86 if no suggestions :)

TIA

James

Dell 1501
AMD Turion 64
SATA HDD
Radion xpress 200 gfx card

---

### Post by davidfield on 2007-01-12
Hi there, this is documented elsewhere, i found the same problem, i have a similar machine... 

A google search of dell 1501 install ubuntu

Found 

[http://ubuntuforums.org/showthread.php?t=299929](http://ubuntuforums.org/showthread.php?t=299929)

Which suggests

adding pci=nomsi to the grub startup line when the CD first boots...

the same page has a really good URL [http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/) 

which is basically about setting up Ubuntu on a Dell 1501

hope that helps..

---

