---
title: "Firefox 1.5, Foxytunes and XMMS"
date: 2006-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Randomskk on 2006-01-07
Heya
I installed Ubuntu, then used apt to get kubuntu-desktop, and am now using KDE.
I've only managed to get MP3s playing on XMMS, so that's what I use for audio.
I installed Firefox 1.5 using ROAF's guide ([here]("http://www.ubuntuforums.org/showthread.php?t=90106")) and that works fine.

However, I then installed Foxytunes as an extension for Firefox, and told it I was using XMMS (player / select / XMMS from Foxytune's menu).
However, it doesn't seem to reconise XMMS, neither controlling it or showing what it's playing.

Any idea what might be up?

edit: just to note, if I swap FoxyTunes to using AmaraK, it seems to work - it can play and pause files, etc but amaraK can't play my MP3 files (GStreamer error: unreconised stream or something, and using xine as the engine makes a nasty glass-breaking sound and complains about sound drivers)

---

### Post by bannerboy on 2006-01-09
if your not set on using xmms, simply install the gstreamer-plugins and gstreamer-plugins-multiverse packages, and you can play mp3s on amorak

---

### Post by Randomskk on 2006-01-10
adam@random:~$ sudo apt-get install gstreamer-plugins
Reading package lists... Done
Building dependency tree... Done
Package gstreamer-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer-plugins has no installation candidate


gstreamer-plugins-multiverse can't be found, and yeah I've got multiverse repositry on (should do, anyway...)

Thanks for the reply, though - if I can get amorak to work, I'll use that happily :)

---

### Post by Randomskk on 2006-01-13
Well, after being forced to reinstall Ubuntu, I tried again with amaroK - install xine again, and this time it took.
Loving amaroK :D

---

