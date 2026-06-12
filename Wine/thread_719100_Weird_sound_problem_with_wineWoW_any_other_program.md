---
title: "Weird sound problem with wine/WoW any other programs`"
date: 2008-03-08
forum: Wine
---

### Post by Separ on 2008-03-08
First off, I am using the ALSA sound system and can get one of two outcomes. If I open WoW first, I get sound in it but nothing else on my system or I can open any non-wine application such as rhythmbox or youtube in firefox and get sound on my whole system but not WoW.

If I use OSS, I am completely unable to get sound at all in WoW but get it anywhere else no matter what I open first.

winecfg settings are set to use ALSA and DirectSound settings are set to emulation, sample rate at 22050, default bits at 16 and driver emulation unticked.

System > Preferences > Sound settings are:

Sound Events > Sound Playback: ALSA
Music and Movies > Sound Playback: ALSA
Audio Conferencing > Sound Playback: ALSA, Sound Capture: ALSA
Default Mixer Tracks: HDA Intel (Alsa Mixer)

Any help at all will be greatly appreciated, thanks.

---

### Post by GSF1200S on 2008-03-09
Ehh.. you should check out your sound module devices- I dont exactly know how to help you here, as I didnt have this issue with wine.

I did, however, have this problem with Cedega. I fixed it by selecting ALSA, unchecking mmap, and typing default in the sound device sections. I dont know how to accomplish this in wine, but im guessing its a problem with you using a sound device.

I use KDE. As an example, before I made the changes listed above, I would try to start playing amarok while i was playing a game. Amarok would just starting going from song to song, and not actually playing anything. When I exited the game, amarok had a message up that said "the audio device was busy." So, im guessing that meant that cedega was linking directly to the sound device and thus other applications couldnt access it. I think thats whats happening to you, but I dont know how to fix it with winecfg or regedit... maybe google "wine audio device busy" and see what it turns up?

good luck...

---

### Post by Separ on 2008-03-09
This is starting to get weird, switched back to OSS (with wine still using ALSA) and everything works o_O

---

