---
title: "zomg, embedded sound and stuff"
date: 2007-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by survient on 2007-01-11
ok, having fun with x64 ubuntu, like it better than the standalone flavors, but, still having a problem. I've gotten crazy things to work, such as SPDIF optical out for my mobo, and firefox32 bit, as well as flash 9 and even java jdk 6 running in x64.... but I can't get embedded sound to work, nor can I get the mplayer plugin to work in either firefox 32 bit or 64 bit. I believe the plugin could be working, but that I just can't configure the plugin's alsa settings properly. Does it use the alsa the OS is using? Agh, to state my question plainly. Embedded sound doesn't work, how do I get it to work? I think the SPDIF optical is my biggest obstacle of overcoming, even though mplayer and vlc player both love it, also, I can run totem standalone, and it plays out my SPDIF optical out. But if I go into preferences > sound settings, and set everything to ALSA, and test it, it doesn't work. If I login to "root", which uses my default settings, I hear system sounds, but I don't hear anything in my only user account. WTFOMGBBQ!??? I care about embedded sounds in my browser, that's it, but, how do I fix it? tank you....

---

### Post by play0r on 2007-01-11
is your user account part of the audio group? :-# 

ez,
play0r

---

### Post by survient on 2007-01-11
it is, and I bet all I need to do is config the mplayer plugin for firefox, however, it doesn't allow me to access the alsa mixer settings specific to the mplayer plugin.

---

### Post by Snookered on 2007-02-22
When configuring my printer I had to make sure the permissions were set right. If it could only work as root then the permissions needed changing. Maybe it has something to do with that, maybe not.
I are a n00b, me.

---

