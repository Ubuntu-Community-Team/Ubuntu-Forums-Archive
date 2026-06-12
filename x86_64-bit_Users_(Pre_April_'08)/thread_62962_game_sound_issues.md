---
title: "game sound issues?"
date: 2005-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flac on 2005-09-06
Ok, I didnt even realize this untill i installed 32 bit ubuntu on my lappy... I dont get sound on 64 bit ubuntu when i play games such as Tuxracer, Supertux, Chromium... Is this a 64 bit problem? or am i missing some wierd permission somewhere? i have sound everywhere else, but not with games....

---

### Post by DRF on 2005-09-06
I'm trying to remember this from memory but a quick and easy fix for some of the sound problems with SDL based games (I think tuxracer was one that was fixed by this method) was to:

Open up synaptic and do a search for SDL.

There should be a number of audio libarys for SDL with the default being either:
libsdl1.2debian-alsa
OR libsdl1.2debian-esd
OR libsdl1.2debian-oss
(I forget which)

I think if I remember right I fixed tuxracer by changing that to:
libsdl1.2debain-all

As I say this is from memory so make a note of the change, so if it doesn't work you can change it back.

Daniel

---

### Post by emperor on 2005-10-25
Yes, ibsdl1.2debain-all should be the correct choice!

---

