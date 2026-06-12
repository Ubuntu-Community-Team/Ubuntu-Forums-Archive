---
title: "no Xvideo support for your video card available"
date: 2007-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by murraypatterson on 2007-02-08
Hi,

I just installed ubuntu 6.10 on my amd64 and I thought I'd test out the video capabilities, so I first installed mplayer.  Then I downloaded an avi file and ran it under mplayer.  The video played perfectly fine as its default size, but when I change the size (ie: full screen it) it slows down . . . probably becuase of no xvideo support . . . as I get this message when playing the avi file:

It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
SDL: Using driver: x11

so I ran xvinfo and I got:

X-Video Extension version 2.2
screen #0
 no adaptors present

I have no idea what this means, nor what DOCS/HTML/en/video.html#xv! is.  I did run mplayer -vo help and tried some other drivers.  None of them worked but x11, but when using x11 it wouldn't allow me to resize the window, so it's essentially useless

any help would be great, thanks
Murray

---

### Post by cylon359 on 2007-02-10
What video driver are you using?  If it's vesa, then there is no Xv support for that...

---

### Post by murraypatterson on 2007-02-11
how do I find out what video driver I am using, and if it vesa, is there a way to get some sort of good video support (so that I can watch dvd movies full screen) . . . or is there even a way to change the driver to something that has xv support?

thanks,
Murray

---

### Post by buMPer on 2007-02-12
> **murraypatterson said:**
> how do I find out what video driver I am using, and if it vesa, is there a way to get some sort of good video support (so that I can watch dvd movies full screen) . . . or is there even a way to change the driver to something that has xv support?

thanks,
Murray

check your xorg.conf file in /etc/X11/xorg.conf.  use gedit but don't sudo.  go down until you reach the line that says something about your video card.  if you're using nvidia you should see "nv" or if it's legacy something like "vesa"

ubuntu has a video player but it doesn't have enough codec to run most video formats.  i suggest use vlc

```

sudo apt-get install vlc

```

never had any problem with windows (sic) video formats that you find on the web

have fun!

---

### Post by Nameless_one on 2007-02-13
I am having the same problem, and I suspect it's because I am using the vesa driver, but I thought I wasn't. My xorg.conf reads as follows:

```
Section "Device"
	Identifier  "ATI Radeon X1650PRO"
	Driver      "vesa"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection
```

I have installed the fglrx driver according to [this](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) guide, and I supposed that is had been installed and used. However, I get the vesa error from mplayer, and my configuration file lists both. 

Am I using vesa? How do I correct this?

---

### Post by Nameless_one on 2007-02-13
Anyone?

---

### Post by Nameless_one on 2007-02-22
Bump. 

Update: I read the xorg.conf manual page and commented out the vesa related lines from my xorg.conf. Gnome still works. I think that means that I am using fglrx, but I still receive the same error in mplayer, and the gui version doesn't work (it fails to initialize the cideo output).

---

