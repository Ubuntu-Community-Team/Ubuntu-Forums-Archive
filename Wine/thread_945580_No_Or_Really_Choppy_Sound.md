---
title: "No Or Really Choppy Sound"
date: 2008-10-12
forum: Wine
---

### Post by Unanimated on 2008-10-12
When I open Halo, it does its thing, then it plays absolutely no sound. On the other hand, when I open Unreal Tournament (the original), it plays extremely choppy sound. When I open Feedback (chart editor for Frets On Fire), the sound plays perfectly fine. I've been messing with the bitrates and hardware acceleration for UT, and it turns out that Emulation acceleration, with 8000 bitrate with 8 bits, the background music usually plays fine, but when the announcer lady comes on, her voice gets all choppy and not-understandable. In a regular game, you can hear the background music, but not any death noises or gun fire. I haven't messed with the sound settings for Halo yet. What's going on?

---

### Post by Unanimated on 2008-10-13
bump

---

### Post by Unanimated on 2008-10-13
...

---

### Post by orzechowskid on 2008-10-13
Not sure if it's the same problem, but I've recently started having sound trouble with Team Fortress 2 in WINE.  Music, sound effects, and voice chat are all choppy or static-y.  I think it started happening after an apt-get dist-upgrade to get the last few Intrepid updates, but I'm not 100% positive.  winecfg says I'm using the ALSA driver at a 44.1KHz sample rate and 16 bits per sample, with hardware acceleration set to 'Full'.  wine --version says 1.1.6, and pulseaudio --version says 0.9.10 - what versions are you running?

---

### Post by Unanimated on 2008-10-13
My WINE version is 1, and my PA version is .9.1.

---

### Post by Marantz on 2008-10-13
I'm having choppy sound and sound dropping in Neocron also. I believe it has to do with PulseAudio and Wine.

---

### Post by orzechowskid on 2008-10-14
> **Marantz said:**
> I'm having choppy sound and sound dropping in Neocron also. I believe it has to do with PulseAudio and Wine.

yeah, I've had plenty of problems with PulseAudio in the past, though it seems to be playing nice right now (YouTube videos don't hang anymore when rhythmbox is playing).  Maybe when I get home from work I'll try downgrading to Hardy's versions of PA and/or WINE and seeing if that makes a difference.

---

### Post by orzechowskid on 2008-10-15
well.  Looks like I didn't have to downgrade anything - killing the pulseaudio process and starting WINE with aoss seems to fix my problem.  In TF2 now anyway, the Valve intro music is still a bit choppy but the TF2 sound effects, voice chat, and menu music work fine (and as a bonus, mic input works now too!).

```
[user@host:~]$ killall pulseaudio &>/dev/null && aoss wine steam.exe
```

Drop that into a text file, chmod +x it, and run it to play your game.  I guess you can re-enable pulseaudio after you're done playing, but everything's working fine for me without it.

---

### Post by Unanimated on 2008-10-15
Is there a command to open it again when I close the program?

---

### Post by orzechowskid on 2008-10-15
> **Unanimated said:**
> Is there a command to open it again when I close the program?

yeah, add this to the bottom of the script:
```
[user@host:~]$ pulseaudio -D
```

---

