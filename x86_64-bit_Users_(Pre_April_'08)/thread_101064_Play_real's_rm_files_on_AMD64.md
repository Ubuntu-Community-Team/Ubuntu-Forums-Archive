---
title: "Play real's rm files on AMD64?"
date: 2005-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by MighMoS on 2005-12-09
I've recently moved from Gentoo on a 32 bit processor, to Ubuntu on an AMD64 processor (mobo fried and I wanted to try something new).  My problem is that I've installed most of gstreamer's plugins, but I can't seem to find **anything**, not even mplayer, that can play real video files.

I get 
```
Requested video codec family [rv3040] (vfm=realvid) not available.
Enable it at compilation.
Requested video codec family [rv40] (vfm=realvid) not available.
Enable it at compilation.
Requested video codec family [rv40win] (vfm=realvid) not available.
Enable it at compilation.
Requested video codec family [rv40mac] (vfm=realvid) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!
==========================================================================
```

Is there anything I can do to play these files?

---

### Post by kerinin on 2005-12-09
you can try to install the proprietary Real player from real.com, but i have had all sorts of problems caused by this on the 64bit system.  

search for realplayer on the AMD64 forums, there are a couple threads about this issue.

---

### Post by rplantz on 2005-12-09
Perhaps my remarks at [http://ubuntuforums.org/showthread.php?t=75940&page=2](http://ubuntuforums.org/showthread.php?t=75940&page=2)
(#19) will point you in a good direction.

I would like to hear how this works, or not, for you.

---

### Post by MighMoS on 2005-12-11
I really don't want do deal with a chroot right now, and the real player binaries off of real.com segfault.  Waiting for mplayer to support realvid now, I guess.

---

