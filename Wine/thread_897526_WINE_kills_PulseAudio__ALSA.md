---
title: "WINE kills PulseAudio / ALSA?"
date: 2008-08-22
forum: Wine
---

### Post by chris062689 on 2008-08-22
I'm having a few issues with PulseAudio and WINE.
If I have anything playing music (VLC, Rhythmbox, etc.) and launch a WINE application, I do not get any audio from any WINE process.
If I don't have music playing, and launch a WINE program, I hear sound from the WINE program, but if I launch VLC, I don't hear any audio from any Linux programs.

Here's settings.  Thanks.

[EDIT: Title is misleading, It doesn't physically kill either ALSA or PulseAudio process, I don't think...]

---

### Post by YokoZar on 2008-08-22
The problem is that Wine doesn't have a PulseAudio sound driver, only an ALSA one.  The two don't work that well together in the current state of things, unfortunately.

---

### Post by chris062689 on 2008-08-22
So all I would have to do is change my sound settings all to ALSA, reboot, and it should work again?
Yep that did the trick.
But of course as soon as I did that, WINE posted a new version with a fix for PulseAudio lol
Oh well, if it's not broke, don't fix it!

---

