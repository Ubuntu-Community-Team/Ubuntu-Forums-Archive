---
title: "[SOLVED] 6.10 - Issues with Ventrilo under Wine"
date: 2007-09-23
forum: Wine
---

### Post by freyyr890 on 2007-09-23
Hey,

I'm running Ventrilo on Ubuntu 6.10 (I didn't feel like doing a clean install to 7.04 and I've had bad experiences with dist-upgrade) under Wine. So far I've been successful in getting the client working and receiving and sending voice messages. I got ventriloctrl setup without too much difficulty (a slight source code tweak to ventriloctrl.c to change the key sent to the ventrilo window from XK_A to XK_Alt_L, but that was the extent of it). I was also able to use Ventrilo just fine while running World of Warcraft, without sound conflict and good quality sound from both programs.

The one issue I still have, though, is after a few minutes of having ventrilo open, an alert dialog will come up with the error to the effect of "Sound input device has been closed. It was sending data faster than it should be. Enabling DirectSound may correct this problem."

Unfortunately, if I enable DirectSound, my CPU usage skyrockets through the roof, and WoW becomes unplayable. I'm using wine-0.9.41 with ALSA as my sound driver (OSS causes stutter for me). Any suggestions?

Thanks in advance.

---

### Post by Sockerdrickan on 2007-09-23
Get WINE 0.9.45 lol

---

### Post by freyyr890 on 2007-09-23
Thanks, I was able to use DirectSound without getting high CPU usage.

My only issue now is that in order to prevent Ventrilo freezing, I have to uncheck "Use DirectInput to detect hotkey."  Consequentially, It no longer reads the hotkey  even when ventriloctrl is running.

I'll play around with it and see if I can get it fixed.

---

