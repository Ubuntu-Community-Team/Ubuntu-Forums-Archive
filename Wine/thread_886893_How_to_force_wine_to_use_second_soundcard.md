---
title: "How to force wine to use second soundcard?"
date: 2008-08-11
forum: Wine
---

### Post by Quapcio on 2008-08-11
Hi!
I have 2 soundcards - ICE1724 - Audiotrak Prodigy 7.1LT is the default one (ALSA dmix through spdif) and the crappy Intel8x0 (integrated) is used with headphones in skype - everything works fine (even AC3/DTS through SPDIF :))

But recently I installed SuperMemo (@ wine) and no matter how hard I search, I can't find how to force wine to use headphones attached to the second soundcard while leaving main soundcard alone ;)

I found page [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) (and many related) but it doesn't help

I tried to enter as DevicePCM1 "hw:1,0" (second soundcard, first "output"), "skype" (ALSA profile created for skype working with both skype and mplayer) but none of them succeeded

Any ideas?

---

### Post by MemoryDump on 2008-08-12
dealing with 2 sound cards on 8.04 is a huge pain IMO ever since they switched to PulseAudio. Actually, dealing with 2 sound cards is a pain for whatever sound daemon you use. *sigh* I wish somebody would make it simpler and not require having to edit thousands of files to make 2 sound cards works flawlessly.

---

### Post by Quapcio on 2008-08-12
> **MemoryDump said:**
> dealing with 2 sound cards on 8.04 is a huge pain IMO ever since they switched to PulseAudio.

I recently switched from Gentoo and I just copied some config files including /etc/asound.conf :) 
as a consequence I'm still on dmix @ 1st soundcard and with second one working "one source at a time" (typically skype) - copying this file took me 10s instead of hours spend on reading manuals ;)

---

### Post by MemoryDump on 2008-08-13
> **Quapcio said:**
> I recently switched from Gentoo and I just copied some config files including /etc/asound.conf :) 
as a consequence I'm still on dmix @ 1st soundcard and with second one working "one source at a time" (typically skype) - copying this file took me 10s instead of hours spend on reading manuals ;)

you should post these files in the Multimedia section of these forums! It might prevent some huge headaches for many users :D

---

