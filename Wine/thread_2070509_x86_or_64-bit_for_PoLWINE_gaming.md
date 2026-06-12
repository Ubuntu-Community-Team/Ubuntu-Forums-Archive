---
title: "x86 or 64-bit? for PoL/WINE gaming"
date: 2012-10-12
forum: Wine
---

### Post by martialartist81 on 2012-10-12
So I'm harking back into Linux more/less full-time, but I'm doing so to tinker and get gaming to work (well... use the info/tools out there already to get my games to work).  I'm stuck though... I remember (a handful of years ago) that WINE in x86 was the preferred method of madness (I'm not entirely sure why.. but I do remember that 64-bit was likely to encounter more problems).  

So my question is... do I fire off a 64-bit install or the x86?  And then from there, if I do 64-bit OS, can I fire up an x86 variation of WINE/PoL for specific games?

---

### Post by dak0 on 2012-10-13
First of all it's very important what are you going to do with your Linux installation, if it's for everyday usage, like browsing, facebook, youtube, email and gaming then go for x86 version.

---

### Post by holastickboy on 2012-10-13
The whole "Linux x64 has issues with flash, etc" is about two years old. 64 bit Linux is far more mature than it used to be, and you can do all the stuff you can on x86 on it.  I would also look at what games you intend on playing with WINE, for example you may get improved frame rates on 64 bit binaries over their 32bit counterpart on some of them (eg, WoW).

How much RAM does your system have? If less than 4GB, stay with x86, but if 4GB or higher, 64bit is the way to go!

---

### Post by dak0 on 2012-10-13
> **holastickboy said:**
> The whole "Linux x64 has issues with flash, etc" is about two years old. 64 bit Linux is far more mature than it used to be, and you can do all the stuff you can on x86 on it.  I would also look at what games you intend on playing with WINE, for example you may get improved frame rates on 64 bit binaries over their 32bit counterpart on some of them (eg, WoW).

How much RAM does your system have? If less than 4GB, stay with x86, but if 4GB or higher, 64bit is the way to go!

What the hell are you talking about, x86, 64-bit have noting to do with GAMING, you'll get equally same FPS on 64bit and x86, GAMES use CPU like 20% for ex. reading files from the HDD, everything else is doing the GPU.

---

### Post by thatguruguy on 2012-10-13
> **dak0 said:**
> First of all it's very important what are you going to do with your Linux installation, if it's for everyday usage, like browsing, facebook, youtube, email and gaming then go for x86 version.

Why?

I run the 64-bit version, and do all of those things. I can't think of a single reason it makes sense to run a 32-bit OS on 64-bit hardware.

---

### Post by thatguruguy on 2012-10-13
> **dak0 said:**
> What the hell are you talking about, x86, 64-bit have noting to do with GAMING, you'll get equally same FPS on 64bit and x86, GAMES use CPU like 20% for ex. reading files from the HDD, everything else is doing the GPU.

That depends. If you're using an emulator like dolphin-emu, for example, it makes use of multi-threading, and runs much better on a 64-bit OS than on a 32-bit OS.

---

### Post by martialartist81 on 2012-10-13
Yes, I'll use it for some internet, email, etc, however, the goal is migrating away from Wind-blows and moving more into full-time Linux.

holastickboy: I'm running 8GB of RAM, AMD Phenom II 955 Black Edition, with a GTX 550 TI for GPU.  In Wind-Blows, I'm able to run 90% of all my games in max to near-max settings without hiccups.

I realize that through WINE/PoL, I'll take an immediate performance hit simply because the games aren't scripted to run in the Linux OS natively; and that's fine.  The goal is to be able to get my games to run at a rate that's slightly higher than playable.  GW2, Borderlands 2, Half-Life (and variations), mostly Steam-based games.

Admittedly so, it's been a couple years since I dove head-first into Linux as a primary OS and tinkered with gaming in it.  I know that its come a long way, and happily so.  

Seems like 64-bit is going to be the way to go; even after reading a ton of test results on both the WINE appdb and the PoL supported games, looks like most people doing testing are doing so in 64-bit OS environments.

Thanks all for the feedback!

Cheers!

---

### Post by dak0 on 2012-10-13
If your system have 5+ Gb's of ram then go for the 64bit version if it's 4 Gb's or <, then x86.

Goodbye.

---

### Post by cgolson84 on 2012-10-13
> **dak0 said:**
> If your system have 5+ Gb's of ram then go for the 64bit version if it's 4 Gb's or <, then x86.

Goodbye.

This has been my experience.  I haven't seen any reason to not run 64 bit if you have more than 4 GB's of ram.

---

### Post by martialartist81 on 2012-10-13
"Back in the day...."  the issue with >4GB of RAM was really with OS utilization.  Wind-blows (to this day) doesn't see higher than 3.75GB in a x86 OS (anything higher than 4GB to be recognized and utilized required the 64-bit OS).  With Ubuntu, back to my memory, it was the dev's (overly generalizing here) priority to get the x86 client up to snuff prior to the 64-bit.  So the 64-bit Ubuntu's had less "support" for WINE and other various issues (like the Java issue mentioned earlier).  After spending a good portion of my night last night and today digging around, that's by far and away, no longer the case.  

Though I am curious to do a little more research and find out what the differences are between x86 architecture and 64-bit architecture with regards to *nix distros.  I understand the fundamental differences in Windows, but with Linux, even the x86 sees more than 4GB of RAM immediately.

Oh well... that's for a different topic/sub-section!

---

### Post by holastickboy on 2012-10-13
> **dak0 said:**
> What the hell are you talking about, x86, 64-bit have noting to do with GAMING, you'll get equally same FPS on 64bit and x86, GAMES use CPU like 20% for ex. reading files from the HDD, everything else is doing the GPU.

Well, that actually depends on the game, particularly if they have 64 bit binaries. World of Warcraft, for example, is extremely CPU bound (which is why we need to hack wine to enable multiple cores for decent performance under Linux).  Other 64 bit games, such as Farcry, will load the entire game into RAM if using the 64 bit client and you have at least 4Gb of RAM, which is a HUGE boost over the 32 bit client. No hard drive fetching, the games run completely from within RAM! I'm not saying you will get any performance increase using a 64bit operating system and running 32bit programs, I am saying if you use 64 bit operating system, and using 64 bit binaries, you will see a performance increase (in most cases).

Problem is that there are not a lot of 64 bit binary games out there because of the large portion of the population with processors that are incapable.

EDIT: I should probably mention that games like Farcry64 only run in RAM in 64 bit mode because the applications do not have enough access to RAM in 32 bit mode to do so.

---

### Post by martialartist81 on 2012-10-13
That makes a lot of sense: even from a development side.  

Cheers, holastickboy.  Thanks for the info!

---

### Post by thatguruguy on 2012-10-14
> **dak0 said:**
> If your system have 5+ Gb's of ram then go for the 64bit version if it's 4 Gb's or <, then x86.

Goodbye.

You are, quite simply, wrong on this. Here's some benchmarks that came out today that show the [64-bit build of Ubuntu tends to perform better than 32-bit]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1"). That's not surprising, since we've known that since at least [2009]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1").

If you have some benchmarks that show that 32-bit consistently out-performs 64-bit, I'd be happy to look at them. Otherwise, please stop posting things that cannot be supported with anything other than either a) your own personal opinion, or b) what you think you heard some guy say once.

---

### Post by holastickboy on 2012-10-16
> **thatguruguy said:**
> You are, quite simply, wrong on this. Here's some benchmarks that came out today that show the [64-bit build of Ubuntu tends to perform better than 32-bit]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1"). That's not surprising, since we've known that since at least [2009]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1").

If you have some benchmarks that show that 32-bit consistently out-performs 64-bit, I'd be happy to look at them. Otherwise, please stop posting things that cannot be supported with anything other than either a) your own personal opinion, or b) what you think you heard some guy say once.

Phoronix is great for stuff like this. It's also important to note that because of the limitations of 32 bit operating systems, they only did the tests with 4GB of RAM.  x64 lets you expand that a lot, so performance can improve even more for some applications. Having the equipment for x64, and not using it seems to be nipple crippling your computer!

---

