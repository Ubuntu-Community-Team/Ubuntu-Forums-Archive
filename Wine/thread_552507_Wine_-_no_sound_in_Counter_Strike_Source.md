---
title: "Wine - no sound in Counter Strike Source"
date: 2007-09-16
forum: Wine
---

### Post by danmurf on 2007-09-16
Hi

I've just set installed Counter Strike Source through Wine - so far everything seems to be running well, except I have no sound :(. I'm still new to Ubuntu and Linux in general so maybe this is a really obvious fix, but it looks like Steam is grabbing the sound so nothing else can use it, even Counter Strike. I found this out because I can't play MP3s once Steam is launched - it says the sound card is busy :confused:

Is there any fix for this, or any way to allow more than one application to use the sound card at once?

Many thanks

---

### Post by splintercellguy on 2007-09-16
You can set the audio driver in winecfg to ALSA (may lag the game) or EsounD (again, may be slow).

---

### Post by daInvincibleGama on 2008-01-19
I'm having the same problem. At some point after I start up steam, sound disappears entirely from my Linux environment and Counter-Strike.

The other guides say that the ALSA driver will crash the game, but I'm going to try it anyway.

---

### Post by raafaell on 2008-02-14
I've got the same problem,  the game starts normally, but the sound gets quiet, any suggestion?

---

### Post by blackdragon1157 on 2008-02-14
[Fixes in a different thread.]("http://ubuntuforums.org/showthread.php?t=556795")  You basically have to have something lock the device BEFORE you launch steam.

---

