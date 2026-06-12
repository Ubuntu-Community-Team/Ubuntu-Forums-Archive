---
title: "mp3 player and wine together?"
date: 2008-08-17
forum: Wine
---

### Post by javafiend on 2008-08-17
Has anyone had any luck running an mp3 player such as Exaile while also running a game in Wine?  Precedence seems to be whichever I start first.  The other one doesn't work.  If I try to play an mp3 with Exaile after starting my game, it won't even start playing the track.

What are your experiences?

---

### Post by Brynster on 2008-08-18
I suspect that is due to Wine not supporting PulseAudio as yet (Ubuntu's current Sound Server)

This maybe whats causing it. I would suggest that you try change the sound server in System>>Preferences>>Sound in the devices tab set all the drop downs to Alsa and run winecfg and select alsa there also. 

Give that a try, it may not help but its a suggestion...

---

### Post by javafiend on 2008-08-18
Thanks.  I'll give that a shot.

---

