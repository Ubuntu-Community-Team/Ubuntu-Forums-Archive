---
title: "Ubuntu suddenly thinks I have no sound card."
date: 2009-06-23
forum: x86 64-bit Users
---

### Post by Cadeyrn on 2009-06-23
Being a x64 Jaunty user who is completely unable to install any other operating system for certain unfixable partition glitches, I wanted to get TeamSpeak 2 working under aoss. Kilz's package installer helped, but the sound was still very choppy, so I tried searching more for fixes. Soon enough I found out that OSS 4.1 actually supports more than one app using sound, so I downloaded oss-linux-4.1-1052_amd64.deb from the OSS wesbite and installed it. At first everything seemed to work, but a few minutes later my computer magically lost all sound. The Volume Control app that used to have mixers for PulseAudio, OSS, and ALSA now only has Playback and Capture for "PulseAudio Null Output," and my sound card that used to be listed under the Device drop-down menu of the Volume preferences is not there anymore. I fear Ubuntu has forgotten I have a sound card. How do I fix this???

Note: My user with no sound is a total admin superuser, with rights to all audio groups in the etc/groups file.

EDIT: What the hell! WINE, which uses ALSA, has sound! But all 4 of my sound servers (PulseAudio, OSS, ALSA, ESD) no longer realize I have a sound card. ALSA-configuring apps either act like there's no ALSA or no sound card, PulseAudio sound sources are called Null because there's no sound card in PA, OSS and ESD have no GUI, and Linux-native apps are getting no sound output. Yet WINE which directly outputs through ALSA, is giving me flawless sound.


EDIT: Solved! All I had to do was uninstall OSS:
sudo apt-get remove linux-oss (or sudo apt-get remove oss-linux, I forgot which)

---

### Post by Therion on 2009-06-23
You don't mention what version of Ubuntu you're using so I don't know if alsa config will work or not.  Try it though...  

Open a Terminal, drop to root and type in```
alsaconf
```

---

### Post by Cadeyrn on 2009-06-23
> **Therion said:**
> You don't mention what version of Ubuntu you're using

I'm posting in the x64 forum with the prefix [gnome] and I said I'm running Jaunty (9.04) on the first post...

And Sudo and BASH both told me alsaconf was not found, as in not a command. I guess I'm not in the version that has it.

---

### Post by Cadeyrn on 2009-06-23
Bump. I need helps!

---

