---
title: "Problems in Wine with KOTOR 1 and 2"
date: 2008-05-07
forum: Wine
---

### Post by mudpuppy630511 on 2008-05-07
I'm having porblems with loading KOTOR II on Ubuntu 8.04 through Wine. Even though I meet the minium software requirements, and I ran it just fine on my computer when I used WIndows 2000, It is not letting me past the configuaration window stating that I need open GL or the equivalent on my system to run KOTOR 2. I don't have it, and I know I can run it without it. My system is an IBM T40 Thinkpad with 512 ram, and the standard graphics card. Pentium 4 1.9, I think it might be dual core, thoughI'm not sure. It's a decent Laptop non-upgraded (yet), and I had no problem with running KOTOR 1 or 2 on my laptop. With KOTR 1, The problem is the graphics. I can run the game just fine with wine, but it is in gray scale and it shows a terminal error when attempting the Directx setup. What is there yet I need to do?

---

### Post by cogadh on 2008-05-07
What exactly is the "standard graphics card" and have you installed the restricted drivers for it yet? Without those drivers, your Linux machine does not have OpenGL or any 3D accelerated graphics support at all and the game will never run correctly. Depending on the actual graphics card, it may still not run, even with the restricted drivers, due to limitations of the Linux drivers.

---

### Post by roderick on 2008-05-07
Also, you do NOT install DirectX - ever under wine. Wine has it's own implementation of DirectX and attempting to install DirectX will most likely end up in a non functional wine setup.

Check out [http://appdb.winehq.org](http://appdb.winehq.org) and see if there is an entry for KOTR.

Make sure you have Direct Rendering. Run glxinfo from the command line (terminal) and look at the output for the line "Direct Rendering: Yes". If it doesn't say Yes, then you do not have your 3D acceleration setup, and the game will not work. You may need to update your video card driver or settings and possibly enable the restricted drivers to get a new driver. 

Please post the output of 'lspci' here so we can see what card you have.

---

### Post by cogadh on 2008-05-07
Rather than run the full glxinfo (way too much useless info) just run:
```
glxinfo | grep direct
```
That will just confirm that direct rendering is enabled.

---

