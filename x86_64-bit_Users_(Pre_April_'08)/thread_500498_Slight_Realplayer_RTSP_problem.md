---
title: "Slight Realplayer RTSP problem"
date: 2007-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaelfx on 2007-07-13
When I use RealPlayer to play RTSP files from the internet, the audio and video are very "jerky," which is not entirely unexpected. I suspect part of the problem is that I'm running it on the AMD64 version of Ubuntu and some C library is not loaded properly. Here is the output from running it in term:

```
realplay

(realplay.bin:28037): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

```

1. What does this mean?
2. Do I just need to wait for a native 64-bit version?

---

### Post by gaelfx on 2007-07-28
Well, the warning about the c library does seem to be related to the 64-bit version, which I know because I just installed the 32-bit version of Feisty on my computer and I no longer get this error when running realplay in terminal, however, the problem of 'jerky' playback in RealPlayer still persists. Does anyone have any ideas about why this might be?

---

### Post by John Jason Jordan on 2007-07-28
> **gaelfx said:**
> Well, the warning about the c library does seem to be related to the 64-bit version, which I know because I just installed the 32-bit version of Feisty on my computer and I no longer get this error when running realplay in terminal, however, the problem of 'jerky' playback in RealPlayer still persists. Does anyone have any ideas about why this might be?
I have RealPlayer 10 running in Feisty amd64 and I do not get jerky playback. 

RealPlayer for me sometimes pauses playing while it waits for the signal to catch up. While waiting it says there is "congestion." I wonder if you have a bandwidth problem, either from the station or on your connection.

---

