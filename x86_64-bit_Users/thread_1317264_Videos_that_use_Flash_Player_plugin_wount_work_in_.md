---
title: "Videos that use Flash Player plugin wount work in Fire Fox."
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by BigBig5 on 2009-11-06
When I play videos that use flash player plug-in like YouTube won't let me use the controls. I can see the video playing, but can't use the controls. Can anyone help.

---

### Post by mykie on 2009-11-06
Not much help but mines doing exactly the same :( no more bbc i player

---

### Post by andreasis on 2009-11-06
There are other threads on this forum regarding this problem, but after reading a fair amount of feedback, I did the following which solved the issue of not being able to use the controls/fullscreen.

1)uninstall flashplugin from synaptic
2)download libflashplayer.so 64bit from adobe
3)sudo mv libf*.so /usr/lib/firefox-3.5.4/plugins directory (or whichever version you have)

---

### Post by BigBig5 on 2009-11-06
That didn't work at all.

---

### Post by efflandt on 2009-11-07
What flash plugin did you install originally, something using Synaptic package manger (which is actually 32-bit with a wrapper), or something that popped up to install flash when a website used flash (also 32-bit)?  Somewhere in the flash sticky at the top of this forum is a list of commands you can run to make sure that all previous flash browser plugins have been removed.  And you also need to make sure that you get the 64-bit flash plugin per those instructions.

But what tripped me up for awhile was my early Athlon 64 3200+ 2000 MHz 1024K cache (from 2004) that lacks the "lahf" instruction (missing in /proc/cpuinfo).  So web ads using 64-bit alpha flash would sometimes vaporize Firefox until I also added flashplugin-lahf-fix.so.  Although, that should not be a problem for newer 64-bit CPUs.

---

