---
title: "Short, low noise audio crackling"
date: 2009-04-16
forum: x86 64-bit Users
---

### Post by bomanizer on 2009-04-16
Hi, I'm posting over here, though I'm using Linux Mint ATM. I would file a bug report, but I'm not sure where to post it. I get little audio crackling on a 64bit Intrepid-based Mint. So far, I've observed that the noise happens when:
- Loging screen becomes ready (before the sound event)
- Skype starts
- Pidgin starts
- Volume is muted/unmuted form the laptop volume keys or from the volume applet
.. etc. In general, it happens just before a sound event.
First, it starts when the app is run the first time, then it becomes seemingly random.

So far I've tried these solutions:
- Reconfigure Pulseaudio
- Reconfigure Alsa
- Reset all audio settings
- Disable Pulseaudio

These do not work.
Any ideas? :)

EDIT: I've pretty much exhausted myself googling and searching bugreports...

---

