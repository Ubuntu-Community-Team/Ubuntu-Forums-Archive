---
title: "[SOLVED] distorted fullscreen opengl with ati restricted driver (Ibex 64)"
date: 2008-11-11
forum: x86 64-bit Users
---

### Post by lavinog on 2008-11-11
I just installed Ubuntu 8.10 64 bit from scratch using the live cd.
I have been using Hardy with every proprietary ati driver as they are released.
This time I used the restricted driver in the repositories (The reason why I didn't upgrade from hardy)
Everything works fine except fullscreen 3d.
Windowed 3d works, but fullscreen I get a garbled mess. The software responds fine and if i exit the program, the video returns to normal.

Tried with compiz on and off (seems odd to me that compiz doesnt experience this behavior)

Anyone else experience this?

I am using an onboard radeon 3200.
4 gig of memory, 256 shared.

Here is the xorg.conf after install of the restricted driver:
```


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

---

### Post by judasg0at on 2008-11-11
Hi there,

I have a thread going for this same issue in the gaming area:
[http://ubuntuforums.org/showthread.php?t=958400&page=2]("http://ubuntuforums.org/showthread.php?t=958400&page=2")

Anyways, I was able to get "some" games to work by executing them with sudo prefixed. So... sudo ./crx to start Alien Arena and such. 

I also have an ATI HD3200 and as far as I can tell It must be some sort of permissions issue to do with the ATI drivers, or more likely, one of thier dependencies. I just don't know how to find out where that file is.

---

### Post by thatsPipe on 2008-11-11
Wanted to add in that you aren't alone; I've also been getting the whole garbled mess with fullscreen OpenGL apps. I've been trying all sorts of various xorg options but to no avail. 

Checking out some other forums, I'm going to see if running apps with 'sudo' helps and also giving 'echo LIBGL_ALWAYS_INDIRECT=true' a try.

---

### Post by lavinog on 2008-11-11
Thank you judasg0at for the information, I was having a tough time searching for the issue.
It worked with sudo...very weird...I suspect you are right, but how do we find out where the permission issue is.
Has anyone figured out if this is isolated to 64bit ubuntu, or has anyone reported it in 32bit?
I suspect we should be seeing the non-beta version of the fglrx driver soon.
When it is released, it might be easier to troubleshoot it then if it isn't fixed.
I will try the LIBGL_ALWAYS_INDIRECT thing when i get home.

---

### Post by lavinog on 2008-11-11
```
export LIBGL_ALWAYS_INDIRECT=true
```
worked also.
There is a huge performance hit though using it, so it is still not a good solution.
glxgears reports about 1500 fps with direct rendering. <300 with indirect rendering.

---

### Post by segalion on 2008-11-12
Hi, 
I suspect I have the same problem. Reported time ago in

[http://ubuntuforums.org/showthread.php?t=874743](http://ubuntuforums.org/showthread.php?t=874743)

My config was 32 bits and Ati IGP X200M, and the problem appear at since Catalist 8.6 til 8.9 (8.10 not tested, but supose the same).

I was begining to supose that was the only one with this problem...

This night I will try a help from spikethehobbitmage at [http://www.phoronix.com/forums/showthread.php?t=13167](http://www.phoronix.com/forums/showthread.php?t=13167)

---

### Post by lavinog on 2008-11-12
I think this issue is different. This has more to do with the new xorg included with intrepid and the fglrx beta drivers.
If running your programs as root doesn't fix your issue, then it is a different issue.

---

### Post by segalion on 2008-11-12
> **lavinog said:**
> I think this issue is different. This has more to do with the new xorg included with intrepid and the fglrx beta drivers.
If running your programs as root doesn't fix your issue, then it is a different issue.

I have tested sudo stellarium in fullscreen and work fine. So I supose this is the same issue. So its not related to ibex or 64bits. I have hardy 32 bits with fglrx 8.9.

---

### Post by lavinog on 2008-11-14
The official 8-11 is out and it fixed the distortion.

---

