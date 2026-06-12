---
title: "How much better is 64 bit Ubuntu than 32 on an AMD64 machine?"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by matw on 2005-10-26
I wondering just how much better Ubuntu for AMD64 is compared with Ubuntu for i386 when run on an AMD64 machine.

My interests: sqrt() type floating point stuff, graphics, and Perl programming.

I'm thinking about switching to the i386 version because I can't get FreeNX to build from source, and I'm not too keen on spending the time it'll take me learn enough about package development to fix the build problems.

TIA

---

### Post by zekolas on 2005-10-26
well you probably will not notice much of a diffence at all, the only place were I notice a differnce is ecoding audio or video has maybe 10-15% prerformace gain on x64, however for most other apps I can't tell the differnce however I have not done any official benchmarking.

It also seems to me, that java applications run smoother under x64 with sun's x64 bit java runtime environment.

---

### Post by ikd69 on 2005-10-26
I will agree with zecolas.  It is more a matter of taste.  I use amd64 and a PIII box with the 64-bit and the 32-bit versions, respectively.  I use primarily for statistical programming.  Since I dont' care much for flash, the lack of a 64-bit native is not so much of a loss to me.

In the end if you can do all of your work with the 64-bit environment, stick with it, since it provides a much better platform to work on.

Cheers,

IKD

---

### Post by Navyblue on 2005-10-26
It appears to me that non-cached programs would load a tad faster, but for cached programs I'd say the diffrence is negligible.

Editted:
If my memery serves, I think it made my glxgears readout increase from about 1000 to 1600 FPS, which is about 60% jump! (on ATI Radeon 9550, AMD64 2800+, nForce3 chipset)

---

### Post by ubernoob on 2005-10-27
[QUOTE=matw]I wondering just how much better Ubuntu for AMD64 is compared with Ubuntu for i386 when run on an AMD64 machine.

My interests: sqrt() type floating point stuff, graphics, and Perl programming.

I'm thinking about switching to the i386 version because I can't get FreeNX to build from source, and I'm not too keen on spending the time it'll take me learn enough about package development to fix the build problems.

TIA[/QUOTE]

Maybe a bit off topic, but are you sure you are using the right compiler? I have had much trouble with compiling with gcc 4. Maybe you have the same problem?

If that is the case, you can solve it with:

export CC=/usr/bin/gcc-3.4
then do "make".

---

