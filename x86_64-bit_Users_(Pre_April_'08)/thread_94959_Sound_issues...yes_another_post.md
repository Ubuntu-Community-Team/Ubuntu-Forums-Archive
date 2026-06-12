---
title: "Sound issues...yes another post"
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Snipersnest on 2005-11-25
Ok so I'm new to the 64bit scene of Ubuntu. My last install was Hoary 32bit with my Athlon 2600+ XP.

**This time my hardware line is up is as follows:**
Asus A8N-SLI Premium mobo
AMD 64bit X2 4400+ Processor
Western Digital SATA II hard drives, x2 250gb (no raid yet)
Geforce 6800 Ultra video cards (SLI)(single till 8xxx drivers)

I need help getting my sound to work... it works ya, but if I use more than one program at a time with sound only the first one has sound. I use TeamSpeak when I play Counter-Strike and if I have TeamSpeak open, I get no sound in CS.

Also the sound seems a little fuzzy sounding..not to clear. I'm using headphones and its normally like crystal.  

I tried to get the nvidia chipset drivers from the website but they appear down for me.. the 310 drivers anyhow.. but I don't think that will fix my problems.

Anybody out there that can give a linux gamer a hand?

---

### Post by teaker1s on 2005-11-25
linux deals with one output at a time I believe

---

### Post by katu on 2005-11-25
If you're using oss as the sound system, then indeed a lot of cards can't deal with more than one sound output. Try, if possible, setting the sound output in team speak to alsa or alsasink. It's a newer architecture and in principle should support software mixing. if not alsa, you'll have to play around with soud daemons. I believe the default for gnome is esd. 

Mind you, I don't know if it's possible to choose with these apps and on a 64 bit system. but it just  might work. 

cheers,
Katu

---

### Post by Snipersnest on 2005-11-25
ok so I'm figuring my ALSA isn't configured?? OSS is the only sound system I have working I think.. I can use OSS on TeamSpeak...but ALL my games crash if I put them on ALSA.  

XMMS works with ALSA, but TeamSpeak won't even though its using OSS... I'm stumped any other ideas?

---

### Post by Snipersnest on 2005-11-28
Bump... Any other ideas on what I can do?

---

### Post by RAOF on 2005-11-28
Search the forums for asound.conf.  I found [this howto]("http://www.ubuntuforums.org/showthread.php?t=32063&highlight=alsa+asound.conf").  It's for hoary, but I don't think there's any hoary-specific stuff in there.

Edit: you might also be interested in [this]("http://www.ubuntuforums.org/showthread.php?t=79274&highlight=alsa+asound.conf").  Some combination of the two threads should see you right :)

---

### Post by Snipersnest on 2005-11-29
hmm I haven't seen that thread yet..I found that other one you were talking about but it didn't seem to help much...but this one, it shows you a part that was missing... alsa-oss ... I was wondering why my asound.conf was blank.

---

### Post by Snipersnest on 2005-11-29
Well none of those did the trick for me.... Is it maybe because I don't have my chipset drivers installed?  I'm 64bit and still haven't gotten my nvidia chipset stuff installed... 

Maybe thats part of my problem?

---

