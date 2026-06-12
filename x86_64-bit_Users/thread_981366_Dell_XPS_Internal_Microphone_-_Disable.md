---
title: "Dell XPS Internal Microphone - Disable?"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by tim_wright on 2008-11-13
Hello, I'm running Ubuntu 8.04 // AMD64

I've noticed a particular issue with regards to the internal microphone and skype. When calling someone with a microphone headset the sound of even the fan is audible. Typing whilst in a call is another very big nusience to the person on the other end of the phone. 

Is there anyway to disable the internal microphone whilst keeping the jack at the front for the mic working?

Any help would be much appreciated,
Tim

---

### Post by xen-uno on 2008-11-13
Have you looked into your BIOS to see if there is a setting there? The internal mic and the jack are probably on the same circuit, with the jack plug acting as a switch to turn off the internal. If that's the case then you should be able to stick an open circuited (as in unconnected) 1/8" phono plug in the jack, which should turn off the mic.

---

### Post by bro on 2008-11-14
Hi, Quite possible you enabled 'analog loopback' (volume control > preferences > analog loopback > close, and back in volume control switch if off). 
Or maybe read what I just wrote here (about enabling mic in the firs place): [http://ubuntuforums.org/showthread.php?p=6175407#post6175407](http://ubuntuforums.org/showthread.php?p=6175407#post6175407) 

also, i didn't manage to automatically switch between plugging in and out the mic, but it can be done manually (Volume control > Options > digital input source)

---

