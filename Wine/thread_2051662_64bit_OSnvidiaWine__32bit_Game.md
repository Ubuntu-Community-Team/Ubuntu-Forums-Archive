---
title: "64bit OS/nvidia/Wine / 32bit Game"
date: 2012-09-01
forum: Wine
---

### Post by JustinR on 2012-09-01
Hey everybody. I have an Alienware M18x-R2 with a NVIDIA Geforce GTX 675M (optimus support doesn't appear to be enabled). I'm on Ubuntu 12.04 64bit, along with the latest nvidia 64 bit drivers (304.43).

I have Wine version 1.5 which should work with a game I want to play, The Sims 3. 

When I run the game I get a message saying from wine saying that direct rendering is disabled (it's not), and that I don't have the correct OpenGL drivers to run the game. The game itself says that there is no enumerable graphics device on my system.

So far, after researching for a few hours, I should preload 32 bit binaries of openGL from /usr/lib32/libGL.so before launching the game, however this results in a segmentation fault with there other information.

Can/should I install the 32 bit version of the nvidia driver instead of/alongside the 64bit nvidia driver?

Is there anyway I can fix this?

---

### Post by JustinR on 2012-09-02
I uninstalled the nVidia driver and reinstalled it. I forgot to check enabled 32bit libraries for OpenGL the first time. 

The game now works in Wine!

---

