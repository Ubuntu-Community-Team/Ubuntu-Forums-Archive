---
title: "can't play dvds"
date: 2004-11-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by smoothrt on 2004-11-30
Has anyone here been able to view dvd movies with ubuntu amd64?  I tried following the restricted format directions on the wiki, but got errors when tried to apt-update (I think it's only for 386).  I currently have xine-gstreamer, totem, and mplayer installed, but none of them seem to be able to navigate through dvd menus.  Any amd64 people able to find and install the necessary codecs?

---

### Post by jdodson on 2004-11-30
you need to apt-get "decss" do a 

```
sudo apt-cache search decss
``` 

and look for the entry for dvd playback.

---

### Post by ubuser on 2004-11-30
I have an updated ubuntu installation on athlon64 with optimized kernel for k8.
I installed xine (and gxine...) and vlc.
I can read dvds with both. gxine is better because it plays audio while vlc not. Moreover i can read dvds true full screen (with vlc no).
The problem i have it is slow with both and too slow with xine.
I will check dma configuration.

So basically i didn't do anything special and it works.
I can't help.

---

### Post by verden01 on 2004-12-05
smoothrt if you live in australia you need a program caled libdvdcss to play dvd's

---

### Post by leech on 2004-12-08
Just type 'sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh' in a console and it'll download and/or compile the .deb you need, and then install it as well.  Bingo, you have DVD play back.

Leech

P.S.  Make sure you have 'build-essential' and 'fakeroot' installed.

---

