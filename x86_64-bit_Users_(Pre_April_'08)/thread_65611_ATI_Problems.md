---
title: "ATI Problems"
date: 2005-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubelducky on 2005-09-14
Has anyone got the ATI drivers to work *well* with a 64bit kernel? I tried following a few different instructions, but most were for i386 and none actually worked *well* . I can run X with these problems, but there is no 3d acceleration. I either end up with a libGL.so.1.2 missing or X.org complaining about the fglrx driver. Is it just my video card or is everyone with an ATI card suffering?

3ghz P4 EM64T
ATI X300SE
Hoary 5.04 running amd64-generic kernel

Forgot to mention its a PCI-Express card

---

### Post by mlomker on 2005-09-14
I wrote a [HOW-TO](http://www.ubuntuforums.org/showthread.php?p=348911) on this just the other day.  Give it a shot and let me know if you have any problems.

You can see below what I'm running.   :razz:

---

### Post by ubelducky on 2005-09-15
Ok was finally able to get X to load using fglrx without errors. When I load fglrxinfo however it shows this. I could not use the latest drivers for got knows what reason, so i reverted to 8.14.3

OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)

Im quite sure that I downloaded the drivers for Xorg, not Xfree 4.3. glxgears works, but only gives about 800fps. fgl_glxgears gives about 120fps. anyone got any ideas?

---

### Post by mlomker on 2005-09-16
Post the output of this:

```

fglrxinfo
dmesg | grep fglrx
cat /etc/X11/xorg.conf | grep Driver

```

You can also look through the /var/log/xorg.0.log for errors.

800fps is the limit of the stock ATI driver with mesa 3d, so I'm always suspicious when I hear that number.

---

### Post by ubelducky on 2005-09-16
fglrxinfo says
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300 Generic
OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)

```
dmesg fglrx shows nothing, but my systems been up for a while and im logged on through ssh. heres cat /var/log/messages | grep fglrx though.

```

Sep 15 17:46:58 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 424 MBytes.
Sep 15 17:46:58 localhost kernel: [fglrx] module loaded - fglrx 8.14.13 [Jun  8 2005] on minor 0
Sep 15 17:48:35 localhost kernel: [fglrx] free  PCIe = 54804480
Sep 15 17:48:35 localhost kernel: [fglrx] max   PCIe = 54804480
Sep 15 17:48:35 localhost kernel: [fglrx] free  LFB = 116322304
Sep 15 17:48:35 localhost kernel: [fglrx] max   LFB = 116322304
Sep 15 17:48:35 localhost kernel: [fglrx] free  Inv = 0
Sep 15 17:48:35 localhost kernel: [fglrx] max   Inv = 0
Sep 15 17:48:35 localhost kernel: [fglrx] total Inv = 0
Sep 15 17:48:35 localhost kernel: [fglrx] total TIM = 0
Sep 15 17:48:35 localhost kernel: [fglrx] total FB  = 0
Sep 15 17:48:35 localhost kernel: [fglrx] total PCIe = 16384

```
is that last line saying that its 16X or that it has 16 megs of ram? Its a 128mb card.

heres cat /etc/X11/xorg.conf | grep driver
```

@evillx:/home/ubelducky # cat /etc/X11/xorg.conf | grep Driver
     Driver "kbd"
     Driver "mouse"
     Driver "fglrx"

```

anyone have suggestions?

---

### Post by mlomker on 2005-09-16
Boy, it sure looks like it is installed and running.  I'd recommend jumping on the [ATI forums](http://www.rage3d.com/board) and looking around.  The driver developers actually visit there...

You sound linux-savvy.  It is quite possible that you'll want to compile your own kernel optimized to use the driver...you should be able to find out what options to use by visiting that board.

---

### Post by ubelducky on 2005-09-17
I probably will do that anyway since im running a generic kernel, but I dont really want to go through the trouble since thats the only real problem im having. I do kinda wanna play nexiuz though.  O:) 
Ill post again if I make any progress.

---

