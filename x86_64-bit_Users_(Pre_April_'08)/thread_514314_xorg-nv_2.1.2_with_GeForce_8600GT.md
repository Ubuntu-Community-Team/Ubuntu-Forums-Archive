---
title: "xorg-nv 2.1.2 with GeForce 8600GT"
date: 2007-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by fox112 on 2007-07-31
Hi this is fox112,

I just bought a Geforce 8600GT (MSI) but it won't work correctly. I tried to install the official nvidia driver 100.14.11 but they did not work, i get no signal at all. lspci does not recognize the card. I tried different guides to install the nvidia driver, used envy to install it, tried everything using the .15 kernel but nothing worked. It wouldn't be a problem for me to use the nv driver but it won't display 1280x1024 on my TFT. The max is 1024x768. I tried adding the resolution to my xorg.conf and even added a modeline but it didn't work at all. Looking around i found a bug report on launchpad and saw that the new xserver-xorg-video-nv 2.1.2 ,which is said to support the 8xxx series well, was backported from gutsy to feisty but only i386. Has anyone an idea how i can get 1280x1024 to work? Nvidia or nv driver does not matter to me.

thx

---

### Post by buckrodgers on 2007-08-12
I have a 8600GT, and the install was not straight forward, Ubuntu drivers do not work, envy neither. however I found the instructions form the Nvidia forum: 
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

and on this page: 
[http://www.robdian.co.uk/content/view/56/](http://www.robdian.co.uk/content/view/56/)

This worked for me perfectly :)

it is very important to really uninstall all the older NV drivers & stuffs installed oder wise it will complain of version mismatch

---

