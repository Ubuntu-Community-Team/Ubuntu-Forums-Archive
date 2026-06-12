---
title: "XGL session causing unreadable picture"
date: 2007-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gegenki on 2007-07-13
Ok I've been searching for about 3 days now and I can't even get XGL sessions to work let alone compiz or beryl or find people with the same problem as me

I'm using
AMD64 x2 3800+
ATI Radeon x1950pro - FGLRX Drivers from the website.
Feisty Fawn 
2.6.20-16-generic

Tried to get beryl to run and I kept getting faced with 1 error. Eventually I uninstalled it all. Then that the various guides I had looked at didn't say you needed to set up an XGL session.
I took to this and found this webpage

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)


Everything installed just fine, I already had xserver-xgl installed from when I was trying to get beryl to work.

I went for method A of starting XGL on the website, XGL session on login window.
My XGL session script contains

```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session 
```

As specified under  "ATI or Intel (using GNOME)" On the webpage but when I login I get a completely distorted screen.

[http://members.lycos.co.uk/gegenki/xglscreenshot.png](http://members.lycos.co.uk/gegenki/xglscreenshot.png)

---

### Post by victorhouston@gmail.com on 2007-07-14
The latest (8.38.6) ati drivers did that for me too...

I reverted to the 8.36.5 drivers and Ive have got compiz to work, although not compiz fusion , dont ask me!


Heres my fglrx driver list...

victor@Cheetah:~/Desktop$ dpkg -l | grep -i fglrx
ii  fglrx-amdcccle                             8.36.5-1                                   Catalyst Control Center for the ATI graphics
ii  fglrx-kernel-2.6.20-16-generic             8.36.5-1+2.6.20-16.29                      ATI binary kernel module for Linux 2.6.20-16
ii  fglrx-kernel-source                        8.36.5-1                                   Kernel module source for the ATI graphics ac
ii  xorg-driver-fglrx                          8.36.5-1                                   Video driver for the ATI graphics accelerato
ii  xorg-driver-fglrx-dev                      8.36.5-1                                   Video driver for the ATI graphics accelerato

Heres my compiz debs installed...

victor@Cheetah:~/Desktop$ dpkg -l | grep -i compiz
ii  compiz                                     0.5.1+git20070712~jbs3                     OpenGL window and compositing manager
ii  compiz-core                                0.5.1+git20070712~jbs3                     OpenGL window and compositing manager
ii  compiz-extra                               0.3.6.1-0ubuntu2                           extra third party plugins for compiz
ii  compiz-gnome                               0.5.1+git20070712~jbs3                     OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             0.5.1+git20070712~jbs3                     OpenGL window and compositing manager - plug
ii  emerald                                    0.3.0+git20070621~jbs1                     Decorator for Compiz and Beryl
ii  gnome-compiz-manager                       0.10.3-0ubuntu1                            Compiz Gnome Manager
ii  libcompizconfig0                           0.0.1+git20070711~jbs0                     Settings library for plugins - Compiz Fusion
ii  libdecoration0                             0.5.1+git20070712~jbs3                     Compiz window decoration library
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu1                            Compiz Gnome Manager

Ive a Radeon Xpress 200M card so I had to  preload some libs before running compiz...

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz-manager & gtk-window-decorator --replace &

---

### Post by Schleeb on 2007-08-29
I'm both relieved, and upset to see your post.

I've been trying to figure out how to get this up and running myself, and I kept running into that screwed up/distorted Xgl as well.

For what it's worth, I'm running
ATI Radeon x1900 AIW - FGLRX Drivers from the website.
Feisty Fawn (x64 version)
2.6.20-16-generic
And the 8.40.4 drivers. I also followed the guide you referenced on installing Xgl.

I'm hoping to find a way to get it to work with the 8.40.4 drivers, but if the 8.36.5 drivers work, I might try finding them and reverting down to them, at least worth a shot I guess.

I'll try to remember to post anything I find out.

---

### Post by bdoe on 2007-08-29
Hey, that's exactly how MY screen looked as well when I tried XGL!  I was able to get it working by completely rebooting after each session instead of just logging out.

ATI Radeon 9600 Mobility (so it's affecting us AGP guys as well),
Feisty Fawn (x64 version)
2.6.20.16-generic kernel
and both the official and the updated fglrx drivers.

---

### Post by Schleeb on 2007-08-29
Ok...that was strange....shortly after posting that...I made one simple change based on something i read here: [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

I honestly have trouble believing it worked, and initially it didn't, though I did a full reboot afterwards and tried again...and was amazed to see it worked...

I eventually want to install compiz-fusion, but in the mean time I'm happy watching the Desktop Effects works.

Anyway, to save you time...and see if this actually was the solution, and not a random fluke...it recommended editing the start script (sudo gedit /usr/bin/startxgl.sh) as follows:

   Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & 
   sleep 2 && DISPLAY=:1 exec gnome-session

The only difference I saw really, was the addition of sleep 2 && in front of display...not sure if that effected things or not, but hey, good luck to you.


Sorry about the stupid smilies...can't figure out how to turn them off...but it's : p without the space...

---

### Post by bdoe on 2007-08-31
> **Schleeb said:**
> Anyway, to save you time...and see if this actually was the solution, and not a random fluke...it recommended editing the start script (sudo gedit /usr/bin/startxgl.sh) as follows:

   Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & 
   sleep 2 && DISPLAY=:1 exec gnome-session
Quoted for clarity
> Sorry about the stupid smilies...can't figure out how to turn them off...but it's : p without the space...
lol...  Yeah, the option to disable it is down a ways, and only if you don't use the quick-reply window.

---

### Post by Arkillion on 2007-09-22
Confirmed! I had the same distortions on my X1600. After 10 hours of agony, this simple change worked... Thanks!

> **Schleeb said:**
> Ok...that was strange....shortly after posting that...I made one simple change based on something i read here: [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

I honestly have trouble believing it worked, and initially it didn't, though I did a full reboot afterwards and tried again...and was amazed to see it worked...

I eventually want to install compiz-fusion, but in the mean time I'm happy watching the Desktop Effects works.

Anyway, to save you time...and see if this actually was the solution, and not a random fluke...it recommended editing the start script (sudo gedit /usr/bin/startxgl.sh) as follows:

   Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & 
   sleep 2 && DISPLAY=:1 exec gnome-session

The only difference I saw really, was the addition of sleep 2 && in front of display...not sure if that effected things or not, but hey, good luck to you.


Sorry about the stupid smilies...can't figure out how to turn them off...but it's : p without the space...

---

