---
title: "Hardy NVIDIA display problems (Google Earth)"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by robinPain on 2008-08-23
My NVIDIA GeForce 7600 is working at last having just discovered this post:
[http://www.thinkingserious.com/2008/04/19/fix-nvidia-drivers-after-hardy-heron-rc1-upgrade/](http://www.thinkingserious.com/2008/04/19/fix-nvidia-drivers-after-hardy-heron-rc1-upgrade/)

Now Google Earth works for the first time on my AMD64 Ubuntu running Hardy.

I have been trying, on and off various suggestions listed here previously for the last six months or so, and got, at least the 1280 * 1024 resolution but not e.g. nvidia-settings without the following error requiring nvidia-xconfig and then the xorg.conf file was always ignored by Hardy and I had the do the manual resolution setting.

Now, for the first time, I try nvidia-settings and it WORKS!

Just in case the above link breaks, the packages you need to load  in Symantec are 
envyng-core 
and 
envyng-gtk
and then you run
envyng -g
(having closed Symnatec first!) in the terminal (and use the autodetect and then save the xorg file)

---

