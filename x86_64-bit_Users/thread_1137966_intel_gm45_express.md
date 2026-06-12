---
title: "intel gm45 express"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by utnr6 on 2009-04-26
anyone have any suggestions on how to get this to function kindly with my dual boot and vista 64

i've edited my xorg.conf and things are goin pretty nice but if anyone can give some helpful suggestions it'd be nice

---

### Post by dtsat on 2009-04-26
What kinds of problems are you having? Running flawlessly on a 945 chipset here.

---

### Post by stryder144 on 2009-04-28
I have a laptop that has the gm45 chipset.  What is wrong?  I, too, dual boot with Vista 64 (wife and I share a computer, so she insists that I don't hose the Vista) and have had no problems.  Everything works on the machine (at least everything that I've tried so far...usb, SD card reader, wireless, webcam, etc.).

Cheers

---

### Post by utnr6 on 2009-04-28
you know, i think its just me trying to fix stuff that isnt broken.  i was having the screen problem where the display wasnt correct and had black bars on the sides; even after changing the display it would return but that is fixable by adding lines to my xorg.conf.  the only minor issue i still have is glitchiness when opening or closing windows or applications but its something i guess i can live with.  quality is good, the glitchiness is a bit annoying.

---

### Post by mickchilders on 2009-04-28
> **utnr6 said:**
>   the only minor issue i still have is glitchiness when opening or closing windows or applications but its something i guess i can live with.  quality is good, the glitchiness is a bit annoying.

I have a laptop with an intel GPU and I have the same quirkiness. opening up Firefox in Intrepid caused what looked like raster lines, diagonal lines that looks like when the horizontal hold goes out on an old TV. GoogleEarth didn't work either. I figured that it is with the fancy Compiz Window Manager. It is supposedly the first window manager that does 3D effects. Anyway, when I tried logging into KDE desktop it went away. Jaunty seems to have fixed the diagonal line problem but I still can't use GoogleEarth unless it is full screen mode. 
I am beginning to suspect that the Compiz window manager is your problem. You could either try another window manager in gnome or try logging into KDE desktop. 
Here is another thread that complained of Compiz problems:

[http://ubuntuforums.org/showthread.php?t=845530](http://ubuntuforums.org/showthread.php?t=845530)

I don't know about other window managers because I haven't tried them out, other than installing and trying the KDE desktop.

---

