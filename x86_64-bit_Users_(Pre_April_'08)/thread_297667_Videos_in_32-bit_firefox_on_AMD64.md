---
title: "Videos in 32-bit firefox on AMD64"
date: 2006-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Reducer on 2006-11-11
Hello, I followed [this great guide]("https://help.ubuntu.com/community/FirefoxAMD64FlashJava") to get java, flash and realplayer working in AMD64 edgy.  Is there something similar to get videos to play?

---

### Post by Azakus on 2006-11-12
Yes. If you have mplayer, install the 32-bit mplayer plugins. They work with the 64-bit mplayer, so you'll get video.
The 32-bit mplayer plugins can be found here: [http://mirrors.kernel.org/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb")
To actually install this, place the .deb file in your home folder and use this code.
```
sudo dpkg -i --force architecture mozilla-mplayer_3.17-1ubuntu1_i386.deb
```

Restart your browser and enjoy video.

---

### Post by Reducer on 2006-11-12
Thanks for the reply.  I've done this, but still don't get any video in Firefox.  The sound works fine and I've verified that the mplayer-plugin is working and not the totem plugin.

---

### Post by TuxMax on 2006-11-13
Thanks Azakus, nice.

---

