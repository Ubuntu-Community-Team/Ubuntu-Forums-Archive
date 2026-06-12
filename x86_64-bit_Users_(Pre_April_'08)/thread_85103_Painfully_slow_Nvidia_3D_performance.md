---
title: "Painfully slow Nvidia 3D performance"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ribs on 2005-11-01
Hi,

I've been trying for the past hour to get my 3D card working, with little sucess. Everything appears to be set up correctly, but the performance of the beast is awfull;
ribs@aphrodite:~$ glxgears -printfps
1911 frames in 5.0 seconds = 382.138 FPS
1937 frames in 5.0 seconds = 387.382 FPS
1892 frames in 5.0 seconds = 378.153 FPS

This is on a GeForce FX 5950 Ultra, so it should be a LOT higher than that! I've tried the k8 ubuntu kernel + restricted modules, the generic ones, and even used the offical nvidia drivers, nothing helps.

GLCore and dri are removed in the xorg.conf file, the dri section at the end has been commented out. I have the load glx part in my .conf file, and of course, I am loading the nvidia driver, not the nv one... Direct rendering is working;
ribs@aphrodite:~$ glxinfo | grep direct
direct rendering: Yes

The only thing I can think which could be wrong is that there is no agpgart module loaded, or any agp module at all;
ribs@aphrodite:~$ lsmod | grep agp
ribs@aphrodite:~$
Loading agpgart produces an error:
ribs@aphrodite:~$ sudo modprobe apggart
FATAL: Module apggart not found.

Is this the source of my frustrations? Can anyone help me? I'm desperate to play Quake4 over here! :(

---

### Post by tseliot on 2005-11-01
Try  asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

There are the developers of the drivers in that forum

---

### Post by joris.brus on 2005-11-02
I used easy ubuntu to install my nvidia drivers
[http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta](http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta)

Make sure you copy your sources.list back to the original after you're done.
Deselect everything but the 3d drivers button

---

### Post by Ribs on 2005-11-02
Okay, I fixed it. But the soultion was not what I was expecting...

Basically, I let glxgears -printfps run for a while, then looked at my top output. I run the 'folding@home' client (like seti@home, but this one cures diseases, hopefully). The top command showed the client for this using all the avalible cpu power. When I killed that client, things improved (4th line down onwards);
ribs@aphrodite:~$ glxgears -printfps
1939 frames in 5.0 seconds = 387.654 FPS
1798 frames in 5.0 seconds = 359.367 FPS
1887 frames in 5.0 seconds = 377.231 FPS
11391 frames in 5.0 seconds = 2278.169 FPS
46459 frames in 5.0 seconds = 9291.608 FPS
47059 frames in 5.0 seconds = 9411.641 FPS
46600 frames in 5.0 seconds = 9319.918 FPS

Dunno why this happened, as folding@home should run at lowest priority. But hey, it's fix now, so I'm happy. :smile:

---

### Post by RAOF on 2005-11-02
This is the reason for the 
```

glxgears --iacknoledgethisisnotabenchmark

```
command line switch ;)

---

### Post by andreas_mauser on 2006-01-09
Hi teams,

as I have the same problem now, and found no solution :confused: , I would ask for help here also. My glxgears shows up with an apple and an egg and this is far to less.

I get 200.000fps, where in xandros or any other debian I get  15Mio  !! :KS 

I really would appreciate any hint.

Thank you and kind regards,
Andreas

---

### Post by Worm_in_a_Box on 2006-01-12
magui@darkmoon:~$ glxgears -printfps
1531 frames in 5.0 seconds = 304.453 FPS
1715 frames in 5.0 seconds = 342.989 FPS
1719 frames in 5.0 seconds = 343.559 FPS

Same problem here ._.! I know that I don't have a top graphic card, but it was supposed to have at least 800-1200 fps. Anyone know how I can fix that?

---

