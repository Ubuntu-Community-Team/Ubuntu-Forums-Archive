---
title: "Is new kernal in 8.10 torpedoing Crossfire and causing memory problems?"
date: 2008-12-26
forum: x86 64-bit Users
---

### Post by lyricalpapa on 2008-12-26
I had the dual video card ATI Crossfire feature working great on my system with 64bit Ubuntu 8.04, but the system began freezing on boot with the latest 8.04 update. 64bit Ubuntu 8.10 was worse. I've had to disable Crossfire and revert to just using one card in the PCI-e slot. My screen still blanks out every few minutes.

I'm also now getting memory aperature warnings on boot, and had to insert "iommu=noaperature" to get 64bit 8.10 to load.

After much research, I come across a bug analysis that points to a PCMCIA card "workaround" that was placed in the Linux kernal beginning with 2.6.22 that is causing the memory handling problems for systems with more that 2 gigs:

[http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm](http://tjworld.net/wiki/Linux/Bug/PciAllocationAlgorithm)

I've also come across other postings of people who have now recognized the same problem in both 32/64 bit kernals, and who are recompiling the kernal with their own patches.

For the rest of us that can't pull this off, is anyone (including Linus) taking a look into this problem? Can anyone point me to guidance as to how to post a bug report that might be looked at by the kernal people?

This is really crippling my Ubuntu system and it seems to be a major problem for people having portables or and motherboards with more than 2 gig of memory and with built-in video chips.

I've kept a partition with Vista for some applications. I'm sad to say that it doesn't suffer from any of these new memory mapping problems and it's running even faster now with both video chips running together with CrossfireX and the lastest Catalyst video drivers.

Gigabyte  GA-MA78GM-S2H MB
AMD Phenom 9450
4 Gig 1066 DDR2
ATI 3200 HD on MB UMA=512Meg
ATI 3450 HD in PCI-e 512Meg

---

### Post by Bloemetjesgordijn on 2008-12-29
Hi,

Not realy an answer on your post, but how did you get Crossfire working...?? I have the same config (on the old kernel, so I can verify for you)

Cheerz,

Bloemetjesgordijn

---

