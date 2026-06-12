---
title: "xdtv amd64 marillat packages stupid (I think) error."
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2006-06-10
I`ve installed xdtv 2.3.2 from [this]("deb http://www.debian-multimedia.org etch main") repository and the following error comes up when I am running the program:

```
$ xdtv

This is xdtv 2.3.2 running on Linux/x86_64 (2.6.15-23-amd64-k8).
scandir: No such file or directory
filename = /home/cyber/.xdtv/xdtvrc
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
xdtv_v4l-conf had some trouble, trying to continue anyway
wmhooks: netwm detected
wmhooks: netwm state above supported
wmhooks: netwm fullscreen supported
wmhooks: nothing found...
DGA: server=2.0, include=2.0
VidMode: server=2.2, include=2.2
  available video mode(s): 1600x1200 1280x1024 1024x768 800x600 720x400 640x480
Selected XvImage adaptor with yuyv support: NV17 Video Texture on port 274 (grabdisplay)
Selected XvImage adaptor with yuyv support: NV05 Video Blitter on port 275 (grabdisplay)
No XvVideo port available.
The app-defaults file is not correctly installed.
You should have installed xdtv by issuing "make install".
Your fault (core dumped).
(you can also temporarily do  "cp XdTV.ad ~/XdTV",
but do not forget to remove it when xdtv is installed correctly)

```

The FAQ of xdtv writes the following solution :
```
    * XdTV crash at startup with this error message:

The app-defaults file is not correctly installed.
Your fault (core dumped)

The reason of this crash is the X11 ressource file. XdTV doesn't find it into the X11 ressource system folder (/usr/X11R6/lib/X11/app-defaults).
Rename XdTV.ad as XdTV and copy it this folder. That will resolve your problem!
```

First of all I am not having any file named XdTV.ad on my system.
Second is that on the above mentioned directory (/usr/X11R6/lib/X11/app-defaults) the file XdTV already exists!!!

If I copy this file (cp /usr/X11R6/lib/X11/app-defaults/XdTV ~/) on my home dir then the program starts normally [-(

---

