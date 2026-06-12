---
title: "Wine (ALSA?) sound problems - AC'97 Intel ICH6"
date: 2008-03-20
forum: Wine
---

### Post by cisforcojo on 2008-03-20
Although there have been a lot of thread from people who can't get any sound from their AC'97 Intel ICH6 cards, I've always gotten it to work perfectly out of the box. However, I do have some problems with WINE. I'm not sure if it's an ALSA problem or a WINE problem.

Here's the error I'm receiving:
```
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
```

I've attached a photo of my winecfg Audio settings.
I'm running wine version 0.9.57.

I've noticed that my Wave Out Device in ALSA is dmix but in OSS my options are:
Realtek ALC250 rev 2 
SAA7134 Mixer

Same for the Mixer Devices.
Is there a way to make sound more stable?
I've been trying to get Gothic 1 to work (it has a Gold rating) and it crashes if I don't select "Emulation" for my card. Even then it only works half the time. Sound is really choppy in the game and the game is still really unstable. I blame it all on the sound. I've tried using the DirectX DLL overrides listed on the WineAppDB and still no luck.

---

### Post by hyperair on 2008-03-20
Try using OSS emulation. Uncheck ALSA, but check OSS in the sound control panel. Install the alsa-oss package. Then every time you run the game, make sure it is run with "aoss" in front. This method worked well for me when I was using ALSA, and works just as well now that I'm using PulseAudio.

---

### Post by cisforcojo on 2008-03-20
Hey thanks for the info! It didn't solve my problem, but I didn't know about aoss before. WINE is just acting really weird and I'm pretty sure it's because of an unstable sound setup. Sometimes sound will just stop working and I'll have to reboot my computer. Hopefully this will be fixed in Hardy Heron.

---

### Post by hyperair on 2008-03-21
Wine's ALSA driver has always been a little buggy, so usually I see the recommended workaround is using aoss emulation with Wine's OSS driver.

---

