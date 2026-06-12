---
title: "Apple &quot;Boot Camp&quot;"
date: 2006-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Torrance on 2006-04-05
So, in case people don't already know, Apple has released "Boot Camp" for its Intel Macs which allows users a nice clean way to dual boot Windows on a Mac. It also provides users with a CD of drivers for windows to allow the software to run smoothly...

What I want to know is if those drivers could somehow be repackaged/engineered and made to help run the hardware of all Macs (ie. the sound on my iMac G5)... Like how there are proprietary Nvidea drivers - could this mean we could have proprietary Apple drivers and I could finally get my Apple system running properly??!?

---

### Post by Torrance on 2006-04-05
[http://www.apple.com/macosx/bootcamp](http://www.apple.com/macosx/bootcamp)

---

### Post by !nkubus on 2006-04-05
Actually later today they added Native Bios support to boot windows

[http://osnews.com/comment.php?news_id=14247](http://osnews.com/comment.php?news_id=14247)

so it's even better Mactel will support Ubuntu also :D well Linux and BSD

---

### Post by jdp on 2006-04-06
Sorry, but no way and no how. ;)  The drivers are **only** for the hardware in x86 Macs to use in WinXP.  There won't be a single driver in there that has PPC code.  At all.  XP doesn't have the Rosetta software, as that is a part of OS X.  Thus, when you boot XP on a Mac all you get is another x86 box with an Apple logo on it.  It bears almost no (hardware) resembalence to anything PPC.  Boot Camp won't do *anything* to help run XP on a PPC machine either.  It's 100% x86 Macs and it seems to add a basic BIOS layer to the EFI of the new Intel based macs.  There have been reports of someone booting a Fedora Core 5 CD on one, so I'm sure Ubuntu isn't far behind.  Somebody just has to try an x86 Ubuntu CD with Boot Camp on an Intel based Mac.

---

### Post by ssam on 2006-04-06
[http://perkypants.org/blog/2006/04/06/ubuntu-boot-camp/](http://perkypants.org/blog/2006/04/06/ubuntu-boot-camp/)

ubuntu dapper x86 will work intel macs. i dont think it will need boot camp as linux can boot from efi with elilo

---

### Post by AlphaMack on 2006-04-06
Okay, here's the next question.  If Ubuntu x86 dual boots on those puppies, how will wireless networking work?  If ndiswrapper can be used, which driver would be appropriate for the Airport Extreme?  Excuse my ignorance if this question has already been answered somewhere deep in these forums.

---

### Post by jdp on 2006-04-06
I guess people just aren't realizing that the Intel Macs are *totally* different computers than the PPC machines.  They are still Macs because Apple made them with the same cases and they run Mac OS.  Other than that they have almost no similarity to the PPCs in terms of hardware.  The intel Macs use an Intel chipset that includes almost everything, from video and audio to wired and wireless networking.  So, any Intel mac has a fairly regular Intel networking chip, not the Broadcom chip used in PPC Macs with Airport Extreme. ;)

Really, the Intel macs just are *not* the same thing with an Intel CPU.  Everything is new.

---

