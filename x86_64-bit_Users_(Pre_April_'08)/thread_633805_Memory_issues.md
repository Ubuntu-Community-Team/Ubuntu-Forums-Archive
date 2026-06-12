---
title: "Memory issues?"
date: 2007-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mcgodx on 2007-12-06
I have had a lot of success in the past about Linux staying running for long periods of times without crashing or just running out of memory.  Lately though, something has been acting off.

When I installed 7.10 x86_64, it worked fine for a while, until I settled down and started to use it for prolonged periods.  We're talking 12-24 hours on, a lot of that time just sitting there doing nothing.  However after this period of time it just starts to slow to a halt.  I somehow got it to open a terminal and ran free -m when i can, and it basically tells me the same thing every time.  I have about 15MB of RAM free.

Here are some system specs:

HP Pavilion DV2100
Core 2 Duo processor at 2.0GHz
2GB RAM
100GB hard drive (I have XP installed on one partition, but it hasn't worked in a long time... never tried to fix it)
nVidia GeForce Go 7200

I use Compiz and Emerald, but I keep the effects down somewhat, Firefox is usually on, as is Thunderbird.  Sometimes I'll listen to music / watch videos, but relatively rarely.

Does anyone have a tip on what may be causing it?  I tried it without Compiz, and it didn't seem to do a whole lot to fix it.

I thought that Linux was good at keeping things organized, was that wrong?  It seems like the memory keeps getting clogged up after a while and that's what is causing it, because even if I shut everything down... the memory is still full.

---

### Post by rsambuca on 2007-12-07
I assume you are using the nvidia-glx-new drivers?  There is a memory leak.

---

### Post by mcgodx on 2007-12-07
> **rsambuca said:**
> I assume you are using the nvidia-glx-new drivers?  There is a memory leak.

Really?  Is there a better set of drivers out there?  If that's the case, it seems that would be very easy to fix.

---

### Post by rsambuca on 2007-12-07
You have to install one of the older ones.

---

