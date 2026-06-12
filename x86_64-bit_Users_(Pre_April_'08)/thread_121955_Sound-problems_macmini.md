---
title: "Sound-problems macmini"
date: 2006-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by mr.lamp on 2006-01-26
Hi,

i got problems with the audio-output on my macmini running breezy.

i'm using alsa and changed the audio-output to alsa in each program.

e.g. listening to music with beep-media-player works, but if there are sounds in gaim, gnome or somewhere else while beep is playing music....i don't here them.

I do not know how to solve this soundproblem. I thought ESD is not needed....is it?


sorry for the bad english :oops:

---

### Post by qball on 2006-01-27
the mac-mini soundcard doesn't support hardware mixing.
So you need either a sound daemon (f.e. esd) to mix the sound.
or (a possible nicer solution) is dmix (mixing is done in alsa), I though in newer alsa's this is done by default.

You can try "googling" on dmix.

---

