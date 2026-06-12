---
title: "[SOLVED] Mathematica 6.0.3 freezes after start"
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by Buzzdee on 2008-06-19
Hi, 

I installed the freshly released Mathematica 6.0.3 under Gutsy x86 64-bit. MathKernel runs fine, but the GUI doesn't seem to work... Mathematica opens and then freezes completely (goes grey, needs to be forced to quit). I tried starting it with the -defaultvisual and -noSplashScreen options - without success. I have Compiz enabled, but it didn't work when I switched it off either. 

It might be of interest to say, that I had a problem during installation. The output of the installation error report reads: 
```
find: WARNING: Hard link count is wrong for 
/home/brandb/ides/Mathematica_6.x_Stud_Unix_EN/mathematica_6.0.3/Files: 
this may be a bug in your filesystem driver.  
Automatically turning on find's -noleaf option.  
Earlier results may have failed to include directories that should have been searched.
```
I suppose this has to do with the fact that the ~/ides folder is a network folder from my university mounted on my laptop... However, I installed the previous 6.xx(?) version by downloading the installation files to my local disc and installing it from here and got no problems during installation but had the same GUI problem (and a few extra windows opened, but that's gone in 6.0.3). 
Console gives no output when mathematica freezes. 

Can any of you help me? I had to go to a Windows computer all the time for mathematica :(

Thanks a lot in advance, 
Bastian

---

### Post by Extr3me on 2008-07-03
I have been using 8.04 with Mathematica 6.0.2 for some time now and I have not had any problems with the gui as such. I have had problems in the past with the gui being a bit unstable as it used to use LessTif, but recently it has been great.  I think now it is using Motif which apparently is much more widely supported.

Are you using an ATI or NVidia graphics card and do you have the official drivers for your card installed?

Ewan

---

### Post by Buzzdee on 2008-07-03
I've had some advances with the Wolfram support staff, although it got quiet now... 
We found out that the problem is, that the GUI can't connect to the Kernel (which runs fine). Probably firewall issues... I don't know. 
wxMaxima can't connect to Maxima, too, exactly the same situation. 

I did install firestarter, but it's switched off (it completely blocks the entire network if enabled). I'm not sure if there might be any other connectivity problems and have no ideas at all - and Wolfram staff, too, I think. I haven't heard from them quite some time now. 

Sorry, I'm a little confused by work at the moment, way too much coffee. I'll try and edit this post when I find time to clean up the info...

Bastian

---

### Post by Buzzdee on 2008-08-13
The problem was, that the loopback device (lo) was missing in my configuration files. To check if you have the same problem as I do, try "ping localhost" and see if you can ping yourself. Otherwise configure a loopback device (several threads in this forum).

---

