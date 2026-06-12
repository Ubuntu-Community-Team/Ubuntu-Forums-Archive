---
title: "Internet problems w/ Ubuntu on Core 2 (Merom) laptop"
date: 2006-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by tmad on 2006-09-19
Hi,

I'm a new user of Ubuntu, and would like to report on my success/failure with getting ubuntu to work on a new Core 2 Duo (Merom) laptop.

On the plus side, the AMD64 version of ubuntu installed w/out a hitch. However, I noticed that my built in ehternet card won't work. (Broadcom BCM4401). Ubuntu does detect my hardware on install and appears to install the correct drivers.

I've tried everything I can think of to get it to work (checked ifconfig, used Network Manager, etc) and nothing has so far. I have even tried using ndiswrapper and the windows drivers, but no success there either. The main problem seems to be that it either can't find my network or when requesting an ip using dhcp, there are no offers.

To make things more interesting, I ran the normal 32bit intel livecd version of ubuntu, and my ethernet card works perfectly on startup with no modifications necessary!

If anyone has any suggestions on how to get things working in the 64bit version, I'd really appreciate it.

P.S. I would like to use the 64bit version over the 32bit since I will be doing some intensive programming and need all the power/time savers I can get. 

Thanks.

---

### Post by kick6 on 2006-09-20
Question: are you doing this "intensive programming" for school or for work?

The reason I ask, for shoolwork you normally just turn in your source.

If its for work, you might be turning in an executable, and if you're compiling executables on your 64bit machine, they're naturally going to be 64bit executables.  Someone running a 32bit processor isn't going to be able to run them.

Just something you might want to think about.  Its possible to build 32bit binaries on a 64bit machine, but it does take extra work.

---

### Post by tmad on 2006-09-20
My programming is actually required as part of my research for my PhD. No one will ever have to look at/use the code but me.

---

### Post by Speedster on 2006-09-20
Regardless of what tmad is doing, the issue remains that the BCM4401 isn't working with the amd64-generic kernel that ships with Dapper amd64 - I am having the same problem on my Core 2 laptop with the same network card.

I have tried booting the kernel with "nosmp noapic" to test whether it was a SMP issue and was still having problems. There are no replies to arp or any traffic going out the interface...

Anyone got any ideas?

---

### Post by tmad on 2006-09-20
Well, it's at least good to hear that I'm not the only one having issues with this.

I am currently installing the amd64 version of Gentoo to see how that works out. I tried the live cd, and that worked fine, but I won't know for sure until I do a real install. I figured I'd tried this since a colleague of mine just got a new Core 2 desktop that seems to be running the 64 bit version of Gentoo quite well thus far.

---

