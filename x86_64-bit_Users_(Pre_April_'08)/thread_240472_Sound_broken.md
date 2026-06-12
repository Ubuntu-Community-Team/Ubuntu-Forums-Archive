---
title: "Sound broken"
date: 2006-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2006-08-20
Hi, I was just using Ubuntu Dapper 64 6.06.1.

I followed some HOWTO's to make multiple simultaneous sound with ALSA, but now my sound is broken, and everything that I try to do does no good.

Tried to undo the HOWTO's configurations, to dpkg-reconfigure all alsa packages, and also reinstall all the alsa packages.

I can see my sound card with aplay -l, dmesg, and also in the System->Preferences->Sound, but in "Media Selector", ALSA, OSS, ESD and AUTOMATIC just works without any sound out.

alsamixer already configured.

What else should I try?

---

### Post by cocteau on 2006-08-21
I don't know if this might be your problem but when I used to install alsa from source the pcm output was always muted at first and you needed to unmute it manually in alsamixer to get it working.

If that's not it, I'm afraid I'm out of ideas.

---

### Post by rogeriovinhal on 2006-08-21
I can't belive that I spent so many time working on such a stupid problem.

Thanks, now I can see that before I learn about the sound system core, I should learn about the way alsamixer works. Damn you PCM! :)

---

### Post by curvedinfinity on 2006-11-20
> **rogeriovinhal said:**
> I can't belive that I spent so many time working on such a stupid problem.

Thanks, now I can see that before I learn about the sound system core, I should learn about the way alsamixer works. Damn you PCM! :)
Oh my freaking god -- THANK YOU COCTEAU!!!!!!!

---

