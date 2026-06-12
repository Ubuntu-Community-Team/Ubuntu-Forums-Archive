---
title: "Pulseaudio PLEASE HELP"
date: 2008-05-31
forum: Wine
---

### Post by damis648 on 2008-05-31
I need audio to work in wine. I have tried all possible options in winecfg with no luck in getting pulseaudio to work. I have gotten it once with 
```
padsp winecfg
```
but that has stopped working. I have an Sound Blaster Audigy HD card on a Dell XPS M1530, and when running winecfg i always get
```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```
as terminal output. Any ideas?

---

### Post by damis648 on 2008-05-31
bump??

---

### Post by damis648 on 2008-05-31
bump again? please, any help would be appreciated.

---

### Post by cogadh on 2008-05-31
PulseAudio doesn't really work with Wine. From the [Wine FAQ](http://wiki.winehq.org/FAQ):
> **2.25. Why isn't PulseAudio available?**

The Wine project has decided not to pursue a Pulse driver for Wine, at this time. We feel it is best to keep working on the more mature Wine Alsa driver. We are aware that some distributions use Pulse as the default, and this is unfortunate. PulseAudio is also known to be buggy when emulating Alsa/OSS and should be disabled for Wine.

There is an unofficial PulseAudio driver for Wine, but it is unsupported and do not submit bug reports while usuing it
You could try replacing PulseAudio with ALSA, but I will leave instructions on that to others who have actually done it.

---

### Post by Ron Overdrive on 2008-05-31
Make sure you have the pulseaduio esd module installed and when you run winecfg uncheck Alsa and check ESound. Thats how I get audio in WINE.

---

### Post by damis648 on 2008-05-31
Thanks for the suggestions. All i had to do was install libao-pulse and select Esound as the driver. Thanks, your suggestion led me to this dicovry of libao-pulse!

---

