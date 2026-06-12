---
title: "Blender not working in Breezy"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by juah on 2006-02-06
After standard installation via apt-get, Blender just won't start. On the application menu, nothing seem to happen. On the command line it just tells "Using Python version 2.4" and stucks there. "top" tells blender-bin uses 98.9 %CPU.
All the dependencies are ok. Yafray also installed as suggested. Anybody familiar with this? I haven't got a faintest idea how to carry on. I also downloaded the binaries from [www.blender.org](www.blender.org) and extracted them. The result is the same: doesn't work.

I didn't find any bug reports about this. Is it that this software is so rarely used or what does it mean. Or is it that for everybody else Blender works well on 64-bit arch. 

Interestlingly enough - 64-bit Blender works fine in 64-bit Suse 10.0 (on this same computer), But using mainly Ubuntu it's just a nuisance booting up Suse once a while.

---

### Post by juah on 2006-02-07
I got it solved a few minutes ago.

It was a graphic card compatibility problem. The card is no fancier than ATI Radeon 9250 and so far it has been running decently with the initial 'open source, generic' drivers by ati, but obviously Blender requires better proprietary driver by ati

From this discovery on, it was easy to follow the instuctions [here]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI"). For me the fglrx -driver found in ubuntu repositories was enough and really made the difference.

---

