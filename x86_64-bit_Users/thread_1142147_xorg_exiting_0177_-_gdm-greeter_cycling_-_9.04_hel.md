---
title: "xorg exiting 0177 - gdm-greeter cycling - 9.04 help!?"
date: 2009-04-28
forum: x86 64-bit Users
---

### Post by audacity on 2009-04-28
After upgrading to 9.04 the nvidia driver seem to have installed correctly (Xorg.0.log shows it loaded without issue), but I cannot seem to start gnome. 

X exits (no backtrace, no core dump, gdb shows a SIGPIPE and then X exits with code 0177). 

xsession-errors shows a gnome-session resource not available (11) but nothing further.

I have reset my xorg.conf to the barebones provided by nvidia-xconfig and still the cycling problem. 

I am able to start failsafe-terminal, but not failsafe-gnome. 

Any ideas? Help is much appreciated. Also let me know if there are other logs to look at, the ones mentioned above don't seem to have much helpful information. Thanks!

---

### Post by audacity on 2009-04-29
just a little bumpity-bump. 

Really, any places to look, procedures, etc. I can't find anything online...

---

### Post by audacity on 2009-05-01
well, I resized my main partition and installed a clean 9.04 in the freshly made one. So now I have the same kernel, same xorg.conf and same nvidia drivers running happily. What gives? 

I really don't like that "reinstall ubuntu" seems to be a solution to most problems around here. Seems too windows-esque for my tastes. 

To that end, anyone have any final suggestions before I diff my /etc/ directories?

---

