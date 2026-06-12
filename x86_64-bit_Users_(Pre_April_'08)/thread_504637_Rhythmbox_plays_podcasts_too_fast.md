---
title: "Rhythmbox plays podcasts too fast"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rizlaw on 2007-07-19
I am using Rhythmbox in Ubuntu 7.04 AMD64 to play back podcasts. I find that the speed of playback is too fast and results in the voices sounding high pitched and "Mickey Mouse" like.  There are no settings that I can select to remedy this problem, although, sometimes hitting > play > pause > play will correct the playback speed. It's not file specific and happens with mp3 as well as ogg formatted podcasts. Playing back the same podcasts in the gnome movie player works fine - no speed issues.

Has anyone run into this problem and found a way to fix it? If not, what would be another good podcast player to install and use?

---

### Post by macabro22 on 2007-07-23
My MP3 playback is too quick seemingly independent of the player program.
What might be happening?

---

### Post by Iudex on 2007-08-12
I have the same problem running Ubuntu 7.04 on a 32 bit Intel based system.  I have tried 6 different audio players including Rhythbox with the same result.  Video playback and audio sync fine in Totem, but MP3 playback is too fast.
I am working under the assumption that some shared resource is causing this (the MP3 codec maybe), but being a Linux noob, any help would be much appreciated.

---

### Post by macabro22 on 2007-08-12
Actually,

Banshee plays MP3 properly.

Formerly Amarok did too. I am clueless.

---

### Post by Iudex on 2007-08-13
I am trying to figure out what is common between our systems.  Could you send me details on yours?

I am outputting directly to IEC958 (the AC97 SPDIF on my Intel Motherboard).  This is going to the decoder of a Logitech Z-5500 Digital speaker system.

I have also attempted to uninstall all media players and then installed XMMS.  No luck.
Since I can't get my music to slow down, a good alternative may be to use Coke so that I can catch up to it...?

P.S.  I also tried Banshee.  It did not work.

---

### Post by Iudex on 2007-08-13
The playback issue appears to be resolved using Xine or a Xine based player e.g. Kaffeine.  For some reason CD or MP3 playback is only on the direct analogue channel though i.e. I  cannot get playback on the SPDIF.  DVD playback still fine.

---

### Post by Iudex on 2007-08-15
Through a process of elimination I established that this problem was occurring on anything using the GStreamer framework.  I don't know what the problem was, but I resolved it as any good noob would by doing a complete reinstall of Feisty Fawn followed by an installation of Banshee 0.13.0.  When attempting to play an MP3, I selected the GStreamer codec when prompted by Banshee.   Rhythmbox also works fine now with PodCasts and MP3s playing at the correct speed as well as outputting to the SPDIF.

Not exactly an elegant solution but I hope it helps someone with more experience figure it out.

---

### Post by Esben Kramer on 2008-01-23
I have this problem. Has there been found a solution?

---

### Post by Lobais on 2008-05-17
I have this problem in efdora 9, and it is the same problem also for youtube videos, mplayer, rhythmbox, totem, playback. Only I hear no sound at all.

---

