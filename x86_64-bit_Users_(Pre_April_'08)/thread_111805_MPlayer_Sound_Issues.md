---
title: "MPlayer Sound Issues"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by obama on 2006-01-03
I have 5.10 running on a 733mhz G4.  I recently installed mplayer via apt-get, and it plays movies fine, but no sound.  I'm wondering if anyone has encountered this before and can help me out.

---

### Post by richardhp on 2006-01-08
I had the same problem, and I just tried "killall esd" at the terminal

I have no idea what it does, but it seemed to work. I'm guessing it frees up the audio device since at the command prompt it said something about "resource busy.." or something.

Anyway, try it and see what happens

---

### Post by slux on 2006-01-08
It kills the enlightened sound daemon, in other words the GNOME sound system that is responsible for all the drum sounds you're hearing when you use Ubuntu. :P

mplayer can be set to use a more esd-friendly audio driver, you can enable playback of multiple simultaneous sounds in alsa (see a HOWTO on that) or use one of the other solutions (including disabling esd which you kind of did by killing it but could also do for good from the GNOME multimedia settings).

Reasons for using esd include wanting to hear those drum sounds, needing it for simultaneous playback of multiple sounds if alsa doesn't support it and requiring a network-aware sound system. Most users will probably do just fine without it.

---

