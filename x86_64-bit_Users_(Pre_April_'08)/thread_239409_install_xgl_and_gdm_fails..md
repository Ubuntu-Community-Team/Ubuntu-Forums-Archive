---
title: "install xgl and gdm fails."
date: 2006-08-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jkarpago on 2006-08-19
Hi:
I followed the steps of that page: [http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D)

and I have this problem:

When I finish all the steps and I reboot gdm fails, it gives me the error that does not find the file libglitz-glx1... 
I install the package again and gdm works but xgl does not, so I followed the
guide again and again the same error with gdm and xgl.

I installed xgl to a friend with this guide and it works perfect for him, so maybe the error is that the updated files for xgl does not work?
Has someone installed xgl succesfully recently?

---

### Post by TripleE on 2006-08-19
I had the same problem.  I did a:
```
sudo apt-get install libglitz-glx1

```
That worked for me.  You can check out my thread:
[http://www.ubuntuforums.org/showthread.php?t=236578](http://www.ubuntuforums.org/showthread.php?t=236578)

---

### Post by jkarpago on 2006-08-19
I did sudo apt-get install libglitz-glx1 but the problem continues, now gdm works but it gives an error when starts, and xgl still does not work, well, to be fair, works but I have no window titles, just the window that I can not move, and all the keyboard shortcuts for xgl do not work either.

---

### Post by TripleE on 2006-08-19
It looks like your GDM config is not right.  I used the following in th /etc/gdm/gdm.conf-custom:
```
[servers]
[LEFT] 0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbufferbuffer
flexible=true

```
[/LEFT]
  
 This is the thread I followed to install XGL: [http://www.ubuntuforums.org/showthread.php?t=225141](http://www.ubuntuforums.org/showthread.php?t=225141)

It is for i386, but it works for xgl also.

---

### Post by jkarpago on 2006-08-19
I did what you say and everything is as allways.
I followed the link you say and did every step and no change.
when I start compiz-start I have this in the shell:


compiz.real: No XKB extension

** (cgwd:22805): WARNING **: Cannot open pixmap: close

** (cgwd:22805): WARNING **: Cannot open pixmap: max

** (cgwd:22805): WARNING **: Cannot open pixmap: restore

** (cgwd:22805): WARNING **: Cannot open pixmap: min

** (cgwd:22805): WARNING **: Cannot open pixmap: help

** (cgwd:22805): WARNING **: Cannot open pixmap: menu

** (cgwd:22805): WARNING **: Cannot open pixmap: shade

** (cgwd:22805): WARNING **: Cannot open pixmap: /home/jk/.cgwd/theme/buttons.glow.png

** (cgwd:22805): WARNING **: Cannot open pixmap: /home/jk/.cgwd/theme/buttons.inactive_glow.png
*** glibc detected *** free(): invalid pointer: 0x0000000000420684 ***


I do not know what happen

---

### Post by checkup on 2006-08-21
Take this repos :

[http://ubuntu.moshen.de/dists/dapper/eyecandy/](http://ubuntu.moshen.de/dists/dapper/eyecandy/)

Then make all this successfull:

- an xerver with glx is running (glxinfo...) no mesa openGL Provider!
- (if ati)start xgl on another display (:1)
- start a session manager on display:1 (like with startgnome.sh)
- on this display start compiz with mesa libGL. if problems appear strace the start and look for the paths compiz is touching. This is often only a problem of symlinks of libGL.so

This is the hardest part. If you get errors, google after them. Like i said most problems arise from compiz not using the correct libGL so track that down. start compiz with --replace to replace the session manager.

- start "dbus-launch cgwd" on the xgl x server 
- xmodmap to your keymap


If all points are successfull you have xgl.

---

### Post by jkarpago on 2006-08-21
Thanks so much:
with this repo all works, thanks so much.
The only thing is that now cgwd themer does not refresh my default theme, It does not give me an error neither.
Is the only thing, but all works perfect now, thanks so much

---

