---
title: "Failed to start the server"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Topi on 2007-03-05
Hi,
managed to install Ubuntu 6.10 with alternate cd but when booting after install I get the error "Failed to start the xserver"...further "no devices detected" when running "startx" in recovery mode... I´m running an AMD64 3000+ with an ATI Sapphire x700 card.... I´ve tried all the common solutions provided on this board but nothing seems to work.... The problem is the graphics card, thats clear...but when trying to edit eg. the "xorg.conf" I just get a blank screen ?
Any help would be appreciated !

---

### Post by ffxr on 2007-03-05
what did you try?

did u do ?

```
 dpkg-reconfigure xserver-xorg  
```

are you sure your getting the path right to xorg.conf?

```
 sudo nano /etc/X11/xorg.conf 
```

note the capital X

bug report & fix here : [https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985)

---

### Post by Topi on 2007-03-06
BIG Thanks....no one ever pointed out that "x11" should be in CAPITAL letters :=)

---

