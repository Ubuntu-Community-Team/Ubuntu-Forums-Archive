---
title: "Extremely poor OpenGL performance"
date: 2005-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by banshee on 2005-04-12
Okay, I've looked everywhere for an answer for this one, but so far I've found none. So I hope that you guys can help, 'cause I'm just out of options.

I've just installed Ubuntu the other day (with this kernel: 2.6.10-5-amd64-generic). 

I've installed nVidia-drivers for my GeForce 5600 XT and everything works as it should... except for OpenGL performance. I get around 9 FPS in ANY OpenGL application. Anything from TuxRacer to Unreal Tournament 2004. Same FPS. I tried using the 'stat fps' command in UT2004, and it said 9 FPS, most of the time, but somethimes it jumps to 170-180 (which is used to be, in Windows XP, with all settings set to low or extremely low). 

Now, could anyone tell me, what is wrong here?

Thanks :)

PS: Linux-newbie.. sorry for any wrong expressions, terms ect. ect...
PPS: English-skills not perfect either...

---

### Post by banshee on 2005-04-12
Just found out that there is a program called 'glxgears'. It reports between 9.800 and 10.000 fps constant...

---

### Post by Manfire on 2005-04-12
[QUOTE=banshee]Just found out that there is a program called 'glxgears'. It reports between 9.800 and 10.000 fps constant...[/QUOTE]

Damn glxgears only get me 2500 fps or so, and tux racer and other games are all running fine so far. Weird problem you got.

Maybe something you can find running nvidia-settings ?

---

### Post by banshee on 2005-04-12
Okay, seems like it was a logical reason for this behavior... Nano had somehow crashed and was swallowing up every system resource it could (100% cpu and over 300 MB RAM, for NANO!). And I changed to NvAGP instead of AGPGART. 

Now glxgears says 1700 fps, which is FAR better than the 10 I got before ;)

---

### Post by michealm on 2005-04-13
[QUOTE=banshee]Okay, seems like it was a logical reason for this behavior... Nano had somehow crashed and was swallowing up every system resource it could (100% cpu and over 300 MB RAM, for NANO!). And I changed to NvAGP instead of AGPGART. 

Now glxgears says 1700 fps, which is FAR better than the 10 I got before ;)[/QUOTE]
 how do i change to NvAGP

---

### Post by banshee on 2005-04-13
sudo gedit /etc/X11/xorg.conf

Under the section called "Device" add a line that says:

Option "NvAGP" "1"

and while you're at it add the following lines as well

#Disables the nVidia logo at GDM start
Option "NoLogo" "True"

---

### Post by graabein on 2005-04-13
I'm having problems as well... glxinfo just gives me errors...

```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault
```
I just upgraded to Hoary from Warty. Previously I had installed NVIDIA drivers and it worked as it should. After the upgrade I followed the steps in the unofficial starter's guide.

BTW: I do NOT have AMD64. Missed the forum name, sorry.

---

### Post by banshee on 2005-04-13
I have no idea if this will fix it, but it's worth a shot

sudo apt-get install nvidia-glx

---

### Post by graabein on 2005-04-13
[QUOTE=banshee]I have no idea if this will fix it, but it's worth a shot

sudo apt-get install nvidia-glx[/QUOTE]
 nvidia-glx is already the newest version.


Now I've reinstalled NVIDIA-Linux driver (7174) and I just get a segmentation fault when I try glxinfo... Jeez...

---

