---
title: "Wine and warcraft"
date: 2007-12-28
forum: Wine
---

### Post by Xar_Lock on 2007-12-28
I've loaded World of Warcraft and wine 0.9.51 in ubuntu 7.10. My video card is ati radeon mobility x1400. i've tried it with the default ati driver that comes with the 7.10 distro, as well as newer ones. I can't load the newest driver , due to it not compiling with the current kernel , because of paravirtulization or something, honestly above me head, as i'm fairly new to linux in general. I'm currently using the version 8.38.6 ati driver. The game loads fine and i can play, but i get graphical bugs. I can't get any of the newer drivers to load at all. i have some weird shading on the ground below my toons on the screen, as well as all my icons look very funny. Does anyone have any idea of what other tweaks i can do to my files to maybe correct these issues. i can post whatever info you may need to assist me in this . Thank you in advance.


Tweaks i have used already include adding 

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
 
to the config.wtf file in my wtf folder of the game. is there anything else that i could do for the graphics issue.

---

### Post by pay on 2007-12-28
You could try this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) to setup the latest fglrx driver. It has always worked for me. The new driver codebase should perform alot better than the old.

---

### Post by fain on 2007-12-28
[http://ubuntuforums.org/showthread.php?t=579378&highlight=warcraft]("http://ubuntuforums.org/showthread.php?t=579378&highlight=warcraft")

Theres the tutorial. Try the "Almost mandatory performance enhancing tweak".

---

### Post by Xar_Lock on 2007-12-28
i tried the install guide for the ati driver, and the driver installs and , after following the steps i reboot the machine , i am no longer able to log into my normal running session. it crashes back out to the logon each time and i must choose failsafe gnome to be able to get past the logon. is there something in that guide that i missed ?

---

### Post by pay on 2007-12-28
What does your xorg.conf look like? ```
cat /etc/X11/xorg.conf
```

---

### Post by Xar_Lock on 2007-12-28
also on another note. prior to this driver update, when i ran glxgears , i was always pulling 4600 to 4800 FPS. Also on the glxinfo | grep rendering it always resulted in direct rendering  No.  It now shows direct rendering Yes, but only has 2500 approx for the FPS.

---

### Post by Xar_Lock on 2007-12-28
Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection


Thats the device info in the xorg file.

---

### Post by Xar_Lock on 2007-12-28
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7170 Release

 glxinfo | grep rendering
direct rendering: Yes

glxgears 
12576 frames in 5.0 seconds = 2515.139 FPS
12604 frames in 5.0 seconds = 2520.776 FPS
12598 frames in 5.0 seconds = 2519.598 FPS
13290 frames in 5.0 seconds = 2657.968 FPS
16888 frames in 5.0 seconds = 3377.401 FPS


I still am not able to load up in normal interface. i have to select failsafe to get online.  I am at a loss as to what i need to do to correct this issue. The driver never gave me any errors when i installed it via the distro specific package.

Any assistance is much appreciated. As well as any further info you may need i will gladly post. I just didn't want to post my entire xorg file as most of whats in it is a waste, and a lot of reading for this paticular issue.

---

