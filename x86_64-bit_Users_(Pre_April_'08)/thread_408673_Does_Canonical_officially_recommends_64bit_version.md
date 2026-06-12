---
title: "Does Canonical officially recommends 64bit version for Core2Duo ?"
date: 2007-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nirro on 2007-04-13
Well, in the download page it says :

"64-bit PC (AMD64) desktop CD
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead."

No word about Core2Duo.

Maybe Canonical prefer that we install the regular 32bit version, which is more mature or has less bugs ?

---

### Post by SpoZen on 2007-04-13
I read on wikipedia that there weren't any differences between AMD64 and EM64T.
I have seen many people using core 2 duo with ubuntu flawless, it shouldn't be a problem.

---

### Post by dptxp on 2007-04-16
Intel 64 bit came much after AMD 64. Maybe they have not tested so rigorously on Intel.

---

### Post by Ryan H on 2007-04-16
It will run just like it would on an AMD 64-bit processor.
It isn't an issue of bugs or more support.

-Ryan H

---

### Post by devnulljp on 2007-04-16
> **Ryan H said:**
> It will run just like it would on an AMD 64-bit processor.
It isn't an issue of bugs or more support
Coming late to this thread, my desktops are all AMD64 dual-dual core 2GHz Opterons and they work great with the AMD64 Kubuntu.
So, will this install work on a C2D? I'm thinking about a new thinkpad, and it'd be a shame to have to run 32bit linux on there...
I see Debian has separate IA64 and AMD64 releases...am I going to have to either use 32bit Kubuntu or move over to debianfor 64bit on the thinkpad?

---

### Post by daniel of sarnia on 2007-04-16
Core 2 duo is an EM64T bit architecture!!! It's just barding nonsense! 

The AMD64 iso supports EM64T too, and therefore supports core 2 duo!!

BTW IA64 is for intel itanium chips, and to my knowledge not at all compatible with EM64T or AMD64.

---

### Post by FrancoNero on 2007-04-17
works flawlessly on my HP laptop with core 2 duo, aside from the codecs and flash issues, which are publicly known and for all i care it is a shame that those problems still exist.... 32bit is how old? lol..... i hope adobe reads this...
so unless you hate messing around with a few codecs and flash and such, there is no problem running ubuntu 64 on a core 2 duo

---

### Post by vitalik on 2007-04-17
Ia64 Technology For Itanium Were Developed By Intel For Servers And Was Not Backward Compatible, Could Not Be Used On 32bit Os.  Amd64 Were Created By Amd A Little Bit Later For Desktops And Later Copied By Intel With Was Called Emt64. So Emt 64 Is Exact Copy Of Amd64 Technology. That Is Why You See Distros Call Their Images Amd64 Or Ia64, I386 For 32bit Cpus.

---

### Post by dabl on 2007-04-17
FrancoNero is right -- Feisty 64-bit  works flawlessly on my overclocked Core 2 Extreme, except for the known lack of some 64-bit plugins.  Add medibuntu to your sources list and you can get some needed codecs and Google Earth too -- you'll just have to make an idealogical compromise regarding "open source".  Amarok works great, plays everything in my collection but midis ( one of these days ...).

:)

---

### Post by Nesmontu on 2007-04-17
Works for me too. Guess that, seeing c2d's popularity, they should update that page... or use the more generic x86_64 instead of AMD64 *shrug*

---

### Post by russell.h on 2007-04-17
Only issue I have seen with core 2 is that for a while (not sure if its still true) the "best" chipset for it on the market used an IDE controller that Linux didn't support. Not sure if thats still true or what.

---

### Post by TheMono on 2007-04-19
It was a problem with the JMicron adapters. And it is fixed.

---

### Post by 9a3eedi on 2007-04-19
May be unrelated, but I'm running amd64 ubuntu on Pentium D flawlessly.. which isn't mentioned on the download page either. It's considered EM64T as well :)




..

somebody needs to edit that page.. rly.. so decieving

---

### Post by wadeall on 2007-04-26
I agree with the commentor about updating the official instructions.  This processor has been outfor a while now and its this little bits of confusion and uncertainty which turn people off Ubuntu.

---

### Post by ghandi69_ on 2007-04-26
Do you guys think 64 bit processors will ever reach their full potential??  I mean, seemingly, the advantage of using a 64 bit processor should be two fold, but with just day to day use, there is relatively no performance increase.  Especially with the focus these days seeming to be on taking advantage of multi-core technology, I'm worried 64 bit has been left behind.  Do you guys think there will be a time when 64 bit will just be "standard", and we will wonder how 32 bit processors were ever able to keep up??

The one reason I still have faith is the memory limit on 32 bit processors, I think once people start "needing" more than 4 gigs of ram, that might be when they really start to take off, but I dont know.

---

### Post by rsambuca on 2007-04-26
> **ghandi69_ said:**
> Do you guys think 64 bit processors will ever reach their full potential??  I mean, seemingly, the advantage of using a 64 bit processor should be two fold, but with just day to day use, there is relatively no performance increase.  Especially with the focus these days seeming to be on taking advantage of multi-core technology, I'm worried 64 bit has been left behind.  Do you guys think there will be a time when 64 bit will just be "standard", and we will wonder how 32 bit processors were ever able to keep up??

The one reason I still have faith is the memory limit on 32 bit processors, I think once people start "needing" more than 4 gigs of ram, that might be when they really start to take off, but I dont know.

There were similar discussions prior to the move from 16 bit to 32 bit processors.  I have no doubt that 64 bit will eventually be the norm.  Especially as people start getting higher and higher resolution digital cameras, and HD camcorders.  Fiddling with these files on the computer is much quicker on a 64 bit platform.

The Software developers are always behind the hardware developers, as they have to be.

---

