---
title: "[SOLVED] Deus Ex on a dual-core system"
date: 2008-03-29
forum: Wine
---

### Post by noerrorsfound on 2008-03-29
I've read the other Deus Ex threads and searched Google, but I haven't found a solution that works for me.

Wine version: 0.9.58

First issue: The game runs way too fast under OpenGL (I'm currently using [Deus Ex Enhanced OpenGL Render v1.8]("http://cwdohnal.home.mindspring.com/utglr/")). On Windows, many old games had the same problem, but AMD's Dual Core Optimizer fixed it. That program isn't available for Linux. I edited the DeusEx.ini file and set FrameRateLimit to a lower value, but it didn't do anything so I changed it to 10 (insanely low) and discovered the game seems to ignore that part of the ini file. I can run it at a normal speed in DirectX mode but it doesn't look as good as the OpenGL version, and has a few graphical glitches. I heard something about CPU frequency scaling and read to disable it in the BIOS but I couldn't find it. I did find "Cool N' Quiet" but that didn't completely fix the speed issue, and I want that on since it saves power and makes the CPU quieter when it's not needed as much. I would like a way to fix this at a software level.

Second issue: I can't use any resolution other than 640x480 or 800x600. I want to use 1024x768. I'm still talking about Deus Ex, just in case you thought I meant my desktop. I also can't make the game go in fullscreen. Using OpenGL, I'm able to maximize the window so it fits perfectly between the top and bottom Gnome panels, but on DirectX there are no window borders.

---

### Post by happyhamster on 2008-03-30
- CPU frequency scaling is taken care of by the powernow daemon. You can disable it from: System-->Admininstration-->Services-->CPU Frequency Manager

- Or from a terminal:

sudo /etc/init.d/powernowd stop

sudo /etc/init.d/powernowd start

---

### Post by noerrorsfound on 2008-04-02
Just in case anyone thinks this is completely solved, I still want to find out how to run in 1024x768.;)

---

### Post by UV-Ray on 2008-04-26
I had same problem on windows.
Games like that should run only on one processor core instead of two.
Look [http://www.thief-thecircle.com/guides/hyperthreading/](http://www.thief-thecircle.com/guides/hyperthreading/) for windows solution.
I think will work on linux too.
PS. Thanks for renderer.

---

### Post by noerrorsfound on 2008-04-26
Thanks for the attempt UV-Ray, but that solution is only for Windows systems. Besides, that problem has already been solved for Ubuntu in a previous post in the thread. ;) Although, the Windows solution seems better since it only affects the specific game (using the solution of disabling powernowd is system-wide and must be manually enabled again afterwards).

---

### Post by luke16 on 2008-06-23
> **noerrorsfound said:**
> Just in case anyone thinks this is completely solved, I still want to find out how to run in 1024x768.;)

If that res doesn't come up by default in the display settings, you can set it manually:
[http://www.widescreengamingforum.com/wiki/index.php/Deus_Ex](http://www.widescreengamingforum.com/wiki/index.php/Deus_Ex)

I still have problems with speed even if I disable powernowd.

---

### Post by colewudgm on 2011-01-12
> **noerrorsfound said:**
> I've read the other Deus Ex threads and searched Google, but I haven't found a solution that works for me.Wine version: 0.9.58First issue: The game runs way too fast under OpenGL (I'm currently using [Deus Ex Enhanced OpenGL Render v1.8](http://cwdohnal.home.mindspring.com/utglr/)). On Windows, many old games had the same problem, but AMD's Dual Core Optimizer fixed it. That program isn't available for Linux. I edited the DeusEx.ini file and set FrameRateLimit to a lower value, but it didn't do anything so I changed it to 10 (insanely low) and discovered the game seems to ignore that part of the ini file. I can run it at a normal speed in DirectX mode but it doesn't look as good as the OpenGL version, and has a few graphical glitches. I [[COLOR=#000000]heard[/COLOR]](http://www.tanapple.net/no/research/prescribed-drugs-a-forbidden-truth-revealed.html) something about CPU frequency scaling and read to disable it in the BIOS but I couldn't find it. I did find "Cool N' Quiet" but that didn't completely fix the speed issue, and I want that on since it saves power and makes the CPU quieter when it's not needed as much. I would like a way to fix this at a software level.Second issue: I can't use any resolution other than 640x480 or 800x600. I want to use 1024x768. I'm still talking about Deus Ex, just in case you thought I meant my desktop. I also can't make the game go in fullscreen. Using OpenGL, I'm able to maximize the window so it fits perfectly between the top and bottom Gnome panels, but on DirectX there are no window borders.Thanks for your instruction! It's very valuable, Now I got it.

---

