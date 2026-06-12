---
title: "no sound using alsa with netflix-desktop (no pulseaudio)"
date: 2013-08-04
forum: Wine
---

### Post by millerthegorilla on 2013-08-04
Hi I have tried everything that I can think of to get netflix-desktop working with sound.  I had it working with pulseaudio but uninstalled pulseaudio to use alsa only with snd-aloop module (I am using cadence-gtk from the kxstudio repos).  At first it worked fine, but then it stopped working and so I reinstalled it, purged it, tried all the different mono and gecko installation stuff, and eventually on a clean install of the whole lot, I installed lib-gstreamer-alsa:i386 (sic) and was able to have sound.  I then restarted the machine and it had stopped working.

I'm at my wits end - can you help?

Many thanks.

ubuntu studio 13.10 64bit

---

### Post by millerthegorilla on 2013-08-05
Hey - I solved it!  I opened a terminal and typed 'export WINEPREFIX=~/.wine-browser/' and hit return.  I then typed /opt/wine-compholio/bin/winecfg and set the wine audio to aloop pcm.

Now I start cadence with jack and alsa aloop running and netflix plays audio just fine.

---

