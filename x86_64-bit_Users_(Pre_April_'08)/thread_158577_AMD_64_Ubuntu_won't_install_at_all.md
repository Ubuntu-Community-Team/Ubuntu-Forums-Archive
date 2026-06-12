---
title: "AMD 64 Ubuntu won't install at all"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by bobpur on 2006-04-11
When installing, the first screen of info seems alright. The second screen of info is a jumble of repetitive letters and numbers. The last three lines are:

42.583837 console shuts up ...
42.583846 <0>Kernel panic - not syncing: Aiee, killing interrupt handler!
42.583861 _ 

This is a new build with a AMD 64 +3000 chip on a Machspeed motherboard, 1gb DDR 400 RAM, 200 gb SATA harddrive.
At this time I am ruling out the install disk as it has been used on other computers ( 2 others ) with better results.
                                                             Thanks

---

### Post by mrchrisblau on 2006-04-12
I'd check the install disc. I'm no pro at Ubuntu installation, but that doesn't sound like an issue with your hardware or your hardware and Ubuntu (if it was, I doubt the first screen would come up at all).

On top of that, I just recently installed Ubuntu on a AMD64 3000+ (ECS KV2 mobo, 512 pc3200 corsair XMS, nVidia 6600 256mb).. so I know that it is possible. 

It can't hurt to try re-burning the iso on a new disc (or even redownloading the iso and reburning).

---

### Post by BjornHaland on 2006-04-13
Burn at 4x or lower, having a solid installdisk is worth the extra 10 minutes, especially if you encounter problems due to bad disk later on and have to spend hours fixing the problem.

---

### Post by dant on 2006-04-27
[QUOTE=bobpur]When installing, the first screen of info seems alright. The second screen of info is a jumble of repetitive letters and numbers. The last three lines are:

42.583837 console shuts up ...
42.583846 <0>Kernel panic - not syncing: Aiee, killing interrupt handler!
42.583861 _ 

This is a new build with a AMD 64 +3000 chip on a Machspeed motherboard, 1gb DDR 400 RAM, 200 gb SATA harddrive.
At this time I am ruling out the install disk as it has been used on other computers ( 2 others ) with better results.
                                                             Thanks[/QUOTE]

I've just had the same thing happen here... ended up installing a 32 bit version but can't seem to get everything working right.  The 64 bit cd checked out OK, it just wouldn't work; have you managed to get yours installed yet, and if so -- how?

Thanks,

Dan

---

### Post by Jason_25 on 2006-04-27
Run through memtest a few times.  Check that it's not overclocked, etc.

---

