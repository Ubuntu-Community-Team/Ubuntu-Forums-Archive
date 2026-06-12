---
title: "[SOLVED] Can't play Xvid/Divx Files (Totem)"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by Major_Kong on 2008-04-26
Despite having the good, the bad, and the ugly (plugins) installed, Totem doesn't seem to find the correct plugin. But it plays mp3 audio streams (haven't checked ac3 and aac, yet).

I get this output in the console:
> ** Message: don't know how to handle video/x-xvid, framerate=(fraction)24000/1001, width=(int)640, height=(int)480
** Message: Missing plugin: gstreamer|0.10|totem|Descodificador XVID MPEG-4|decoder-video/x-xvid (Descodificador XVID MPEG-4)



PS: Files coded with in H.264 also fail to play.

---

### Post by soxs on 2008-04-26
I use vlc or mplayer (both from the repos). Totem is a complete mess.

---

### Post by Half-Left on 2008-04-26
Install totem-xine and remove totem-gstreamer.

---

### Post by Major_Kong on 2008-04-26
> **soxs said:**
> I use vlc or mplayer (both from the repos). Totem is a complete mess.

I also use mplayer, but i like to use totem from time to time. Can't seem to find a gui for mplayer of my liking. (yes, i know of smplayer...)

So, this is not a 'known' problem ? 

PS: What do you think ? It's a gstreamer or totem problem ?

---

### Post by Major_Kong on 2008-04-26
Am I the only one having this problem ? (Using Ubuntu 8.04)

EDIT: Is there another video player (that uses gst) in the repos, that i can use to test if the bug's from gst or totem ?

EDIT2: Found out on my own, and i think it's a safe bet that the problem lies with the gstreamer plugins (probably something to do with the new .deb packages...).

---

### Post by soxs on 2008-04-27
you may use the plugins from the multiverse/universe repositories, this *may* help

---

### Post by Major_Kong on 2008-04-27
I am.

EDIT: Found the problem and fixed it. I was using a newer version of libavcodec that i got from the upure64 repos. And it appears it doesn't work well with the official ubuntu gstreamer packages built against the outdated version of libavcodec...

---

