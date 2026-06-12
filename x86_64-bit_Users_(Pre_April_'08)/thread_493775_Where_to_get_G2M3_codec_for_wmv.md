---
title: "Where to get G2M3 codec for wmv?"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by D!mon on 2007-07-06
I wish to play wmv file; when I open it with totem (totem-xine), it says that there is no support for G2M3 video codec. I guess it's 'fourcc' codec.
I've installed all automatix codecs, gstreamer plugins, w64codecs from medibuntu repository and all other packages with codecs that I could find in Synaptic, but it didn't help :(
So where should I go next and is this codec available for linux and amd64 or I should use a kind of win emulation to play this file??

Upd: btw, it's gotomeeting codec; is it possible to play or convert such video format without running WMP?

---

### Post by rjz35 on 2007-07-07
D!mon,

sudo apt-get install mplayer

then you should be able to play all.

mplayer [your file name]
if not go to "www.mplayerhq.hu" look for the codecs, install them as stated in the readme inside the package.

good luck

---

### Post by D!mon on 2007-07-11
rjz35, I do have mplayer and all the available codecs already installed. the it seems that there is no linux version of gotomeeting codec..

---

