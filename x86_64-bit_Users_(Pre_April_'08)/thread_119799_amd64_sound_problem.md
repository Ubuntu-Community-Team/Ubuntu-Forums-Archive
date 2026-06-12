---
title: "amd64 sound problem"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by nubbe on 2006-01-20
I got an amd64 install and there is a problem with the sound. A slight distorsion that shouldn't be there. In win xp the sound is fine.

I wonder if someone has any ideas what's wrong and how to fix this?

Maybe use the latest nvidia audio drivers? since I have internal integrated sound with nvidia chipset.

I also wonder if anyone has any experience using nvidia proprietary audio and/or network drivers? Good? bad? Absolutely never do??

Linux nForce Driver - AMD64/EM64T

Version: 1.0-0310
Release Date: November 23, 2005

Should be the one for my system...

Any thoughts would be appreciated.

---

### Post by FluffyElmo on 2006-01-20
Try reducing the volume level for PCM in *Applications->Sound & Video->Volume Control*. When the volume controls are set at maximum I get distortion. Reducing the PCM volume to ~90% solves it for me.

---

### Post by Fallen Guru on 2006-01-21
Sound on my main card was distorted as well in breezy amd64, upgrading to dapper fixed this and a few other problems - sound's crystal clear now. Maybe ALSA is a bit broken in the stock ubuntu kernel? (I have a TB SantaCruz, using the snd_cs46xx driver as hw:0)

---

### Post by nubbe on 2006-01-24
I'm not brave enough to go to Dapper just yet..  :)

Reducing the pcm volume has made it better, not quite fixing it, but it's noticeably better, so thanks a lot for the advice.  :)

---

