---
title: "fglrx/mesa issues"
date: 2005-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by gazzie on 2005-05-12
Hi there

I've sucessfully installed fglrx:

```
gareth@pogo:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)
``` 

```
gareth@pogo:~/quake$ glxinfo | grep direct
direct rendering: Yes
``` 

However, when I run FuhQuake-GL (a Quakeworld client), and indeed ZQuake-GL (Fuhquake is based on the ZQ source), I get really bad FPS and a generally rather "laggy" experience. I'm talking 2/3 frames per second here, and the keyboard/menus lag too.

Anyway part of the problem seems to be that when I load fuhquake, it gives me some info about mesa - am I right in thinking that is some kind of GL implementation that does not speak directly to the gfx card like the driver does? - anyway before I had got fglrx working properly, fglrxinfo was bringing up some mesa stuff... so the issue appears to be that FuhQuake is not using fglrx as it should be.

I guess... :P


Any ideas?

---

### Post by gazzie on 2005-05-12
I should add:

Here's the fuhquake screenshot with the mesa blurb:
[http://ninjapirates.net/fuhquake116.jpg](http://ninjapirates.net/fuhquake116.jpg)


Here's the *glxgears stuff:

```
gareth@pogo:~/quake$ fgl_glxgears
2847 frames in 5.0 seconds = 569.400 FPS
3179 frames in 5.0 seconds = 635.800 FPS
3176 frames in 5.0 seconds = 635.200 FPS
3184 frames in 5.0 seconds = 636.800 FPS
```


```
gareth@pogo:~/quake$ glxgears
13676 frames in 5.0 seconds = 2735.200 FPS
13707 frames in 5.0 seconds = 2741.400 FPS
12568 frames in 5.0 seconds = 2513.600 FPS
12552 frames in 5.0 seconds = 2510.400 FPS
12578 frames in 5.0 seconds = 2515.600 FPS
15785 frames in 5.0 seconds = 3157.000 FPS
29113 frames in 5.0 seconds = 5822.600 FPS
20115 frames in 5.0 seconds = 4023.000 FPS
```

---

### Post by gazzie on 2005-05-13
No ideas?  :?

---

### Post by StacyWebb on 2005-05-13
So basically  this is a windows based app running though wine? 

If so that may be where your problem is. As for your fps that you are reporting through glxgears, they are right on par with what they shoud be. If this is a windows app you might try running it though Cedega (Point to Play) and see how that works. 

One other question was it installed before or after you fixed the 3d acceleration (fglrx)?

---

### Post by gazzie on 2005-05-13
It's the Linux version of FuhQuake... ([www.fuhquake.net](www.fuhquake.net))

There is no install, just a simple tar -zxf

---

