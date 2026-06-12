---
title: "XGL Absent on ATI Card
beryl-xgl: No composite"
date: 2006-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by arksan on 2006-11-13
I run Dapper on A64 with X800GTO card on PCIE. I got the A64.deb beryl packages and force installed all the beryl components. 
I even get the beryl gem on my trap. But when I say

> beryl-xgl

i get..

> XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl-xgl: No composite extension

I dont know what to do from here. I run fglrx.

---

### Post by RAOF on 2006-11-14
You need to also install and set up XGL.  There are numerous howto's around, although I can't remember any off-hand.  If you can't find one here, you may have better luck on the Beryl forums.

Additionally, your x800 is probably old enough to be properly supported by the open-source drivers in Edgy, which would require no extra configuration or XGL.  Since you're running Dapper, however, that's probably not very interesting for you :)

---

### Post by earthfall on 2006-11-14
[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu) can be a good starting point to install XGL.

---

### Post by WalmartSniperLX on 2006-11-14
Another thread on the forums about the same problem (I'm having too). I've been trying many things to configure XGL >.< no luck, yet ;) Ill make sure to post how I get it fixed once I do :D

---

### Post by Circus-Killer on 2006-11-15
okay, i'm not sure exactly what your problem is, but if i understand you correctly, you have no composite support with your fglrx driver. that is cos the current ati drivers in the repository doesnt support composite.

however, if this is your problem, there is a possible solution.
goto [this]("http://albertomilone.com/driver.html") site and select your version of ubuntu. follow the instructions to add repository and update to latest fglrx drivers. it might help.

taking a look at [this thread]("http://ubuntuforums.org/showthread.php?t=255929") might also help. the thread is pretty much just the thread for the website mentioned above.

hope you have better luck than i did. personally, my next gfx card is gonna be an nvidia. :P

---

### Post by RAOF on 2006-11-15
What, you mean the latest fglrx drivers support Composite and OpenGL on at the same time?  Wow!  They're now as good as nVidia drivers from a year ago :p.

Alternatively, the XGL server neatly sidesteps that problem by providing the Composite extension **using** OpenGL :).

---

### Post by Circus-Killer on 2006-11-16
> **RAOF said:**
> Alternatively, the XGL server neatly sidesteps that problem by providing the Composite extension **using** OpenGL :).

sorry, can you explain that one. afaik, and many others, we have to disable composite in order to get 3d acceleration. so im not sure what you meant by that last statement.

---

### Post by RAOF on 2006-11-16
OK.  The Composite extension is an X extension that provides the ability to do composite effects on X windows - things like alpha blending (translucency), etc.

The fglrx drivers, when last I saw them, could either support the Composite extension **or** GL acceleration, not both at the same time.  XGL sidesteps this: it **only** uses OpenGL, to do all of its drawing.  It also provides the Composite extension to programs running on it, and it does this, like all of its drawing, by translating stuff into OpenGL calls.

So, since the fglrx driver supports OpenGL acceleration, you can use XGL to "fake" the Composite extension using OpenGL.

However, using XGL will disable direct rendering for everything else.  At least, it did last time I tried it, so all the other OpenGL programs will run a bit slower.

---

