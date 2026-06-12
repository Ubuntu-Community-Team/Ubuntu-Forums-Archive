---
title: "Wine GeForce FX 5700"
date: 2007-08-10
forum: Wine
---

### Post by SaiyanEye on 2007-08-10
I am using Nvidia GeForce FX5700 w/ 256mb, and I can't get Wine to detect it?  I have installed the drivers for it, I just can't get Steam to recognize it when I try to launch CS:S.  I will play CS:S and get about 15fps.  Any ideas or do you need more info?

---

### Post by splintercellguy on 2007-08-10
Have you tried restricted drivers or the latest via the Envy script?

---

### Post by misfitpierce on 2007-08-10
Yes use envy to install nvidia drivers and 1-2 trys with it should install it... after install use glxinfo in terminal and see if it says direct rendering : yes

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb) - Envy direct link

---

### Post by cogadh on 2007-08-10
Wine does not have the ability to detect your video card, it just passes graphics instructions from the game to the Xserver. As long as you have an accelerated driver installed for your graphics card and the Xserver is properly configured to use it, Wine will use it.

---

