---
title: "What exactly does flashplugin-nonfree install?"
date: 2009-09-16
forum: x86 64-bit Users
---

### Post by iamringo on 2009-09-16
Hi all,
I apologize whole-heartedly for posting this, when I'm sure there's a better way to find an answer. That said, I couldn't really find one after searching. Anywho, I was wondering, when one installs flashplugin-nonfree on a 64 bit system, does one get the thirty-two bit version with some kind of wrapper or Adobe's 64 bit alpha? I noticed this, which makes me think it might be wrapped:
```
locate libflashplayer
/opt/google/chrome/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
```
Anyone have a clear definitive answer? Thanks a ton!

---

### Post by kerry_s on 2009-09-16
it's the 32bit version. you can remove it & download the 64bit version.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

make a folder named "plugins" in ~/.mozilla, then unpack the flash & move it there.

---

### Post by iamringo on 2009-09-16
THanks a bunch!

---

