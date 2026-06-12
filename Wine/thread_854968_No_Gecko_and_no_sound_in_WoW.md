---
title: "No Gecko and no sound in WoW"
date: 2008-07-10
forum: Wine
---

### Post by gluonman on 2008-07-10
Greetings.
   I have two basic problems.

   1) Firstly, while installing WoW wine kept attempting to install Gecko whenever a launcher or downloader needed to open up that displays HTML. I would click install on the Wine Gecko installer pop-up and it would do absolutely nothing, and the launcher or downloader would have a blank white space upon which is written HTML display disabled, or something of the sort. I can't figure out any alternative method of installing Gecko and making it work. It is not a severely limiting problem, just annoying and something I want to take care of just the same.

   2) After WoW was fully installed, I discovered a couple of problems with its performance. The first problem was its nasty habit of screwing up my screen resolution whenever I ran WoW.exe, requiring a full system restart to get my resolution back. I fixed this problem by opening winecfg and just checking off the box with the option to emulate a virtual desktop. This way, when I open WoW.exe it does nothing to the screen resolution and just opens as if it were a window. I'm fine to continue playing it like this, but the one problem remaining is the fact that I have absolutely no sound. In winecfg I went to the audio tab and tested the sound and it seems to be recognizing my sound card and working with it fine. But it is just in WoW that there is no sound at all. I'm not really sure why, and I'd much appreciate if someone could key me in.

   Responders may provide suggestions/comments on either or both of the 2 stated problems. Any help or feedback will be much appreciated.

---

### Post by thisismalhotra on 2008-07-10
2. Go to winecfg, change wow to use winxp settings and try different audio option. usually ALSA works but try OSS and others too.

1. This has happened to me before, I reinstalled wine than but you can completely skip the launcher and start wow directly. Instead of running Launcher.exe run WoW.exe

---

