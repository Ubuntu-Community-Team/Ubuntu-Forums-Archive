---
title: "Sound eventually fails in Wine"
date: 2008-08-11
forum: Wine
---

### Post by Methuselah on 2008-08-11
I'm running Hardy with Pulseaudio and I'm having this weird problem with wine sound.
Right after rebooting my machine, sound works in wine.
After running for a while, it stops working.
If I test sound in wineconfig I get an error message.
If I then restart, it'll be fine again for a while.

I have no idea what triggers this.
Even if you don't know a solution, do you know of any troubleshooting tools that will help me figure out what's going wrong?

Thanks.

---

### Post by Ferrat on 2008-08-12
I have noticed this aswell, altho 99% of the time it takes a few hours before it gives out and I just need to restart that specific app and not wine itself, also noticed that some programs in wine look the audio so that no other program can reach it.

---

### Post by k@e on 2008-08-12
I'm suffering the same issue although I have completely uninstalled PulseAudio. Sound drops a few minutes in wine, mostly after a new area is loaded in a game etc. Updating ALSA didn't help as well. I have a workaround to get sound running.

Open up wine configuration, go to audio tab and change hardware acceleration to "Emulation". This does it for me, however, the sound may run faster at times until it "catches up" with video.

I hope it helps you, too.

---

