---
title: "X-Server problems with GeForce 6200 SE"
date: 2006-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by mdh on 2006-02-26
Hi all,

I have been having problems with x-server (crashes often when running opengl applications) after nvidia driver installation. I am not sure if I have the right drivers installed, is it possible to know if I have the correct driver by looking at my xorg.conf file ??. 

Here is a part of my xorg.conf file which I guess deals with the graphics driver. My graphics card is nvidia GeForce 6200 SE with Turbo cache.

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6200?]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV40 [GeForce 6200?]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
........... file continues .......

 What does the question mark at the end of the *Identifier* line mean ?, My guess is that my graphics card is not recognized and I am having a generic driver, am I right ?

Any help would be greatly appreciated. I really want to get this problem sorted out quickly. Because of this x-server crash, I am forced to work in windows whenever I need to use OpenGL apps :(

---

### Post by RAOF on 2006-02-26
The "identifier" is just that - it is just a label for that particular configuration (because you can use multiple monitors/graphics cards for X).  That configuration seems correct - you appear to be using the nvidia driver, which is what you want.  It could just be a driver bug - your card is pretty new, isn't it?

For further info, you can check out /var/log/Xorg.0.log - that's the logfile for X.  Check it particularly for lines with (EE) in them - that's the error tag.

You could also run "glxinfo" from a terminal - that should return a bunch of info about your GL setup.

Maybe you should try the newer nVidia drivers - you can get them from nvidia.com, and the "nvidia drivers" link in my sig has a howto to get them installed.

---

