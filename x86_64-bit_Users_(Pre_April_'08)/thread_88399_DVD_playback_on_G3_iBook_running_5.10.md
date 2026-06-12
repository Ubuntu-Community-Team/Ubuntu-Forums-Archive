---
title: "DVD playback on G3 iBook running 5.10 ??"
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by sgartner on 2005-11-10
Hi I have just completed an install of 5.10 on my 500 Mhz iBook (380 MB RAM), everything is great so far... except DVD playback...

It's just not happening full stop. :confused: 

Totem boots up and then seems to choke. Playback does not commence ??? Although the status bar in the Totem window says that it is playing it remains at 0.00

I have checked that the DVD drive has dma enabled &#8211; using_dma = 1(on)

Is there another player out there that I should be using?

Any suggestions greatly appreciated.

Thanks.

---

### Post by ssam on 2005-11-10
have you followed the instructions for getting restricted formats to work? [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

i'd recomend you try xine, ogle, mplayer or vlc

also what is the speed of your computer. it may not be fast enough to play a dvd. when you run mac os x the mpeg decoding work is shipped out to the graphics cards, but on linux you usually need to do that in software on the cpu. G4s benifit from altivec, but you need a fast G3 to be able to watch a dvd smoothly.

sam

---

