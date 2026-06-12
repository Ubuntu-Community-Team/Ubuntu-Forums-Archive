---
title: "Sound broken"
date: 2008-10-11
forum: Wine
---

### Post by *malagant* on 2008-10-11
My sound under wine sounds as if it is running with a sample rate of 1000 or so. As if you would play something at full volume on the cheapest speakers you can imagine...

Sound driver is set to ALSA, sample rate 48k, , Hardware Acceleration Full, Driver Emulation enabled. Outside wine, (ALSA-)sound is working perfectly.

Any ideas?

---

### Post by Unanimated on 2008-10-12
I'm having the same exact issue. What a coincidence. It's weird, because my sound is only choppy during games, but when I'm running Feedback, everything is perfect, and there's no sound at all in Halo.

---

### Post by *malagant* on 2008-10-12
I solved my problem, and i have no idea how.
I changed this, tuned that, restarted those, reinstalled etc., and all of a sudden, my sound in wine works.

---

### Post by Unanimated on 2008-10-12
Could you elaborate a little? Say what you changed, what you installed, please?

---

### Post by Canislupus on 2008-10-15
I am having the same problem with Wine 1.16

It was working fine a week or two ago. Wine has updated a couple of times since then through auto update.

I have tried everything.  OSS doesn't even work on my system.

I really suspect that PulseAudio isn't playing nice with wine, but I don't know how to fix it.

My sound stutters constantly on about a 2-3 times per second cutout rate.

Also (not sure if this is significant) winecfg often hangs when I use the "test sound" button.

---

### Post by *malagant* on 2008-10-18
The test sound option in winecfg is very broken...

I reinstalled my System, and now the sound is broken again. But i switched to OSS and use aoss to start the games, and that seems to work fine for me.

@Unanimated: I think it was something in the game options, cause at some point, game 1 (WoW) worked, and game 2 (Colonization2) not, and after some more Try&Error both games worked.

---

### Post by deruberhanyok on 2008-10-19
Canislupus - I'm having the same problem. My regular system is out of commission so I'm running 8.10 Beta (32-bit) on an older box.

If I switch Wine to using OSS the test sound button works fine, after I've exited the app once and re-opened it. I've only tried playing one game so far - Jedi Academy - and found that as soon as I try to launch the game it actually mutes my PCM sound volume. 

I bring up the Gnome desktop (CTRL-ALT-D), right-click on the game in the taskbar and send it to the second workspace. Then I can adjust the volume and it works, though the sound quality is similar to what *malagant* describes (If I don't send it to the second workspace it steals focus as soon as I try to adjust volume). Keeping the PCM volume about halfway up eliminates the sound distortion.

If Wine is set to use ALSA I can't even get the app to start, it freezes as soon as the menu to launch the game plays a sound (much in the same way that Winecfg stops responding when I try playing the test sound).

Dunno what's all changed... but my main system has been down since mid-September (upgrade gone awry). At the time I was using 8.04 64-bit and whatever was up-to-date and didn't have any issues.

Given that the problem seems to involve sound specifically I'm going to also guess this has something to do with the combination of wine/alsa/pulse.

[edit] - I've just discovered that setting wine to use OSS doesn't mute any sound if you launch with the alsa-oss wrapper (aoss wine appname.exe). So there's that. But man, I haven't used aoss in a long while now. I wonder what changed to cause the incompatibility suddenly?

---

### Post by Ng Oon-Ee on 2008-10-19
Not sure if mine is the same problem, but I've been getting stuttering in NWN2 and Warcraft III. What I did was, in the audio configurations, select Full (not emulated) and select Esound instead of ALSA. Seems to work so far....

---

