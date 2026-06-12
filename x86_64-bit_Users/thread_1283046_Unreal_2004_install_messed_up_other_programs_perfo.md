---
title: "Unreal 2004 install messed up other programs performance"
date: 2009-10-05
forum: x86 64-bit Users
---

### Post by danielkabrinski on 2009-10-05
OK.  I got Unreal 2004 to install and I followed all the steps to get it to work, even checking off the stuff in the beginning, and installing the 64 bit patch.  It worked and I got really excited.  It was running pretty choppy compared to all the other games I had running...  so I went back and tried them again.

Now, all of the other games I have like Vendetta Online, Assault Cube, Armagetron Advanced...  run choppy (the refresh rate is delayed) and lack sound.  This is funny because sound works everywhere else even in Unreal.

Here are the packages I tried reinstalling:

```

Reinstalled the following packages:
libopenal1 (1:1.4.272-2)
libsdl-gfx1.2-4 (2.0.13-4)
libsdl-image1.2 (1.2.6-3)
libsdl-mixer1.2 (1.2.8-5)
libsdl-ttf2.0-0 (2.0.9-1)
libsdl1.2debian (1.2.13-4ubuntu3)
libsdl1.2debian-alsa (1.2.13-4ubuntu3)
libsmpeg0 (0.4.5+cvs20030824-2.2)
libopenal1 (1:1.4.272-2)
libsdl-mixer1.2 (1.2.8-5)
alsa-base (1.0.18.dfsg-1ubuntu8)
alsa-source (1.0.18.dfsg-1ubuntu8)
alsa-utils (1.0.18-1ubuntu11)
lib32asound2 (1.0.18-1ubuntu9)
libasound2 (1.0.18-1ubuntu9)
libesd-alsa0 (0.2.40-0ubuntu3)
nvidia-173-modaliases (173.14.16-0ubuntu1)
nvidia-180-kernel-source (180.44-0ubuntu1)
nvidia-180-libvdpau (180.44-0ubuntu1)
nvidia-180-modaliases (180.44-0ubuntu1)
nvidia-71-modaliases (71.86.08-0ubuntu1)
nvidia-96-modaliases (96.43.10-0ubuntu1)
nvidia-common (0.2.11)
nvidia-glx-180 (180.44-0ubuntu1)
nvidia-settings (180.25-0ubuntu1)
xserver-xorg-video-nv (1:2.1.12-1ubuntu5)

```

This got the sound to work in the programs but the refresh rate for everything is still choppy.

Can anyone help me?  Do you need more information?

EDIT:

I followed [this](http://ubuntuforums.org/showthread.php?t=599243) guide.

---

### Post by psavva on 2009-10-05
You may have made changes to your Graphics Card Driver.  Which in that case, it would explain the slowness of games.

I would recommend you find which Graphics Card you are using, and follow a guide to install the graphics driver correctly.

If you have Nvidia or a ATI Card, look at this:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by danielkabrinski on 2009-10-05
Thanks for the response but it actually didn't work.

Now that I've been using it a lot more though it looks like it affected the performance or just about everything.  I uninstalled the game and it didn't even solve the problem.

:confused:

---

