---
title: "gutsy radeon 9250 can't set 1024x768 resolution"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by gallux on 2008-01-18
Hi,
I've installed ubuntu 7.10, I use open source drivers with my radeon 9250
Test with glxgears works fine
glxinfo | grep "direct rendering" the answer is YES
Compiz effects work.
Everything seems ok but I can't set my monitor resolution.
Every session starts with awful 1280x768
I change resolution with tool in system---admistration---screen to 1024x768.
It keeps this resolution until I restart my session, then it returns to 1280x768.
I'm not able to save the right resolution.

I've tried to edit manually my xorg.conf, changing sections "monitor" and "screen" but nothing happens, session starts at 1280 and when I enter system---admistration---screen to set up again the right resolution the configuration file is overwritten.
So in /etc/X11 I find a lot of xorg.conf.1  xorg.conf.2 xorg.3 etc etc

thx in advance for your help

---

### Post by him610 on 2008-01-18
I experienced the same symptoms with an nvidia chip and a 19 inch monitor. You are on the right track - xorg.conf file is the one you need to concentrate on; however, you can't edit it directly.

Try this link first for an introduction to xorg.conf and its characteristics. 

[http://www.linux.com/feature/118108](http://www.linux.com/feature/118108)

Then go to this post...

 HOWTO: change resolution/refresh rate in Xorg in Tutorials & Tips

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Good luck.
Have fun.
Live long and prosper.

---

### Post by Yellow Pasque on 2008-01-19
A possible workaround might be to go to System -> Preferences -> Sessions and add a startup program that simply runs the command:
```
xrandr -s 1024x768
```

---

### Post by gallux on 2008-01-19
Thx for your suggestions
I tried every way to edit xorg.conf with no results.
Now I solve the problem with a simple tip.
I've searched in /usr/bin the gnome-control-center application.
There's a display configuration inside, with an option "set as default for this computer".
Now it works... :)

---

