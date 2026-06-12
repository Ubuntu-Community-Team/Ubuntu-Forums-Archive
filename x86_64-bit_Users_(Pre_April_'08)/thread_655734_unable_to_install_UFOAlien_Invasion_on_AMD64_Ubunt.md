---
title: "unable to install UFO:Alien Invasion on AMD64 Ubuntu 7.10"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by borisattva on 2008-01-01
during the ./configure phase i had some libraries come up as missing (as expected).
installing one at a time and retrying worked until i reached package 'libvorbisfile'

in synaptics i have:
libvorbisfile3 (was already installed)
libvorbisfile-ruby
libvorbisfile-ruby1.8

i installed the other 2 and retried but still getting:
configure: error: couldn't find libvorbisfile!


please advise

---

### Post by ~LoKe on 2008-01-01
Try...
```
sudo apt-get install libsdl1.2-dev libsdl-ttf2.0-dev libvorbis-dev libjpeg62-dev \
libpng12-dev libncurses5-dev libcurl3-dev libsdl-mixer1.2-dev
```

---

### Post by borisattva on 2008-01-01
thanks! that worked.
though this is confusing my understanding of the ./configure process.

why would it claim that i'm missing a package that i have because others are not installed?
why doesnt it specify them instead?

---

### Post by ~LoKe on 2008-01-01
Well, in order to configure from source, you need the development files.  I think the one you were missing was **libvorbis-dev**.

---

