---
title: "Totem video pauses, audio keeps playing..."
date: 2008-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by High_Yield on 2008-01-31
Hi-

Using 64 bit Gutsy and Totem, every ~30 seconds or so the video pauses for ~10 seconds, the audio keeps playing however, then it continues on as if nothing ever happened.

Note, the videos are fine and play in 32 bit land, and also just fine in 64 bit Gutsy using VLC.

So - why does Totem "pause" video like this ?  Anyone else having this same problem ?

- B:confused:

---

### Post by coskierken on 2008-02-02
Try looking up Quickstart.  It is an all inclusive install program for making backups, to installing the codecs needed for smooth video playback using Totem-Xine.  My buddy wrote it.  I helped out by finding the correct files needed for my computer.  It is very good.  Hope this helps.

---

### Post by SpiderGorilla on 2008-02-02
Have you tried the Totem with the xine back-end instead? It might do you some good. Bear in mind, however, that you have to uninstall the gstreamer backend before you can do the xine backend. The two apparently cannot co-exist. But if you use Add/Remove, it'll do that for you on its own, and you can easily go back if it doesn't work.

At least... I can easily go back...

---

