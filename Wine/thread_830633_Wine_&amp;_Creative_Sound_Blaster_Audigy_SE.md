---
title: "Wine &amp; Creative Sound Blaster Audigy SE"
date: 2008-06-16
forum: Wine
---

### Post by MechWarrior001 on 2008-06-16
I just installed my Audigy SE & disabled my motherboard sound. But now Wine gives me audio errors no matter what driver's I select & I don't hear any sound from my games.

Any fixes?

---

### Post by cogadh on 2008-06-16
What errors do you get? If it is this one:
```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
```you can ignore it, it just indicates that your card is not capable of hardware mixing (which it isn't) and does not have a master volume control. I get the same error all the time with my Audigy LS and sound works fine. Any other errors you are getting might indicate what the actual problem is.

---

### Post by MechWarrior001 on 2008-06-16
I fixed it.

It turned out I had to many audio packages installed. I pretty much removed every one that wasn't natively supported by *Ubuntu*. Because the error would say things like the *ALSA* driver is being use or something.

---

