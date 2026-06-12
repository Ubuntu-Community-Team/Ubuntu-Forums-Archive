---
title: "dummy sound device in ubuntu Xen guest for Steam"
date: 2013-07-07
forum: Wine
---

### Post by FORCED-INDUCTN on 2013-07-07
Hello,

I am trying to run wine inside an Ubuntu 12.04 X64 Xen guest for Steam. Wine fails to start because of the lack of a sound card. Here is the full output when attempting to start Steam.exe with wine: [http://paste.ubuntu.com/5852725/](http://paste.ubuntu.com/5852725/)

The guide I am fallowing ([http://forums.bistudio.com/showthread.php?149892-ARMA-III-on-Linux-servers-via-WINE](http://forums.bistudio.com/showthread.php?149892-ARMA-III-on-Linux-servers-via-WINE)) recommends modprobing a dummy sound device. However I don't have a module called "snd-dummy," only one called "snd-seq-dummy." Loading "snd-seq-dummy" has no effect.

Kernel version: 3.2.0-24-virtual

Any ideas?

--Will

---

