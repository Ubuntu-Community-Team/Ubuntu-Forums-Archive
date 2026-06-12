---
title: "Problems Running Team Fortress 2 + NVIDIA Driver Issues"
date: 2008-09-06
forum: Wine
---

### Post by nikki93 on 2008-09-06
Hello!

I've recently switched over to (Ubuntu) Linux as my primary development environment (I'm a hobbyist programmer), and I'm loving it. :)

I have an NVIDIA GeForce FX 5600 graphics card and BenQ T905 Monitor, and when I try working with the latest (173.14.12) version of the NVIDIA driver, I get horizontal artifacts, and my screen flickers and moves horizontally. This also happens with the 96.43.05 version. However, with the 71.86.04, everything works fine, I am able to run 3D applications I develop, but not Compiz (because of lack of Texture from pixmap, but this is fixed using Xgl). However, I had to uninstall Xgl because Team Fortress 2 wouldn't work with it at all for some reason (without Xgl, I get a little further, but it still crashes).

The past few days, I've been trying to get Team Fortress 2 to work, but in vain. I already got Steam to work, and I copied over the relevant game files from my Windows partition.

If I run Team Fortress 2 using -dxlevel 81 or -dxlevel 90, it gets past the Valve logos, and loading screen, but the screen is black after the logos (I can hear what's going on though, like the clicks in the menus). With -dxlevel 70, it runs fine, it even reaches the loading screen, but crashes after that saying I should support at least pixel shader 1.1.

Any ideas how I can fix the Team Fortress 2 problems, or even the NVIDIA driver problems?

Thanks a lot for your help!:)

---

### Post by aoanla on 2008-09-06
The TF2 problems are almost certainly caused by the driver problems you're having.

I'm running the latest 177.70 beta drivers, and it's fine with my 8800GT.

However, if you read the README that comes with the 177, I note that this doesn't help you much, as the 177 series removed support for FXs.

Try posting in a more general forum here - perhaps the Graphics and Multimedia one - to get you card fixed. I'm fairly certain that this will also fix your TF2 experience.

---

