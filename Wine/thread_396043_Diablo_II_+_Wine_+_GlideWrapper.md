---
title: "Diablo II + Wine + GlideWrapper"
date: 2007-03-29
forum: Wine
---

### Post by MadMonkey234 on 2007-03-29
Hey,

I can play Diablo II + LOD with wine just fine but the perspective option is disabled in the video settings. To gain access to it, I tried using a Glide wrapper (GLIDE3-to-OpenGL-Wrapper Version 1.4 (c) 2006 by Sven Labusch). However, when I launch the game, I get the following error: "No useful pixelformat found! Please check your graphics card drivers". I know my video card is correctly configured since Warcraft III plays fine with the -opengl command line switch. I can also run the test in the glide-init.exe application provided with no errors. Any ideas? I use ATI's fglrx driver but it works fine in everything else.

Thanks for your help

---

### Post by babaum on 2008-07-21
Hi buddy, 

I'm with the same problem and I use the same driver (ATI x300)
Had any luck so far?
I didn't :\

---

### Post by babaum on 2008-07-21
Amazing. Right after I was ready to quit this, I found a glide wrapper that works PERFECTLY!
[http://www.zeckensack.de/glide/](http://www.zeckensack.de/glide/)
You can use its installer right from wine itself. Works as a charm.
Please try a few setups (there is a config tool) and let me know if you need any help.
:guitar:

---

### Post by celtoid on 2008-08-22
I hope you can help me with my Diablo II issue.

When I run Diablo II in wine with just using direct2d my frame rate is very low, but when I use the zeckensack glide wrapper the frame rate is much higher but I get flickering about once a second, I tried using the glide3-to-opengl-wrapper but that would crash my game. I've tried fiddling with the ati control panel settings and the zeckensack glide wrapper settings but neither fix the problem.

I'm running a radeon xpress 1100 chipset and my monitor has a refresh of 60hz. I'm also running the most current version of wine with 64-bit ubuntu 8.04.

Thank you for any help you can give me.

---

