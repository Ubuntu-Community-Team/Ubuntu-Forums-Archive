---
title: "World of Warcraft glitches"
date: 2012-11-23
forum: Wine
---

### Post by djxvillain on 2012-11-23
Hey guys, this is my first post, but I absolutely can't figure this out.

I'm running Ubuntu 12.10 and I use Wine to play World of Warcraft.  But I have a few issues that I can't seem to resolve.  The top half of my character and mounts are cut off in the character info screen (see attachment), my map doesn't show my arrow, or rarely shows it (see attachment), and my graphics card doesn't run at full specs, which it would on Windows (see attachment).

Another issue is I can't multi-task.  WoW will freeze if I click anywhere in my second monitor.  I then have to completely shut down Wine, and relaunch.

I have the NVIDIA GeForce 460 SE.  I've looked at other solutions that have worked for other people such as adding SET gxApi "OpenGL" to the config.wtf file, and trying different drivers.  I think I've tried every NVIDIA driver.

I'm not one to quickly complain, I've done my research, but this is really bothering me.  It makes things very frustrating, especially the map and character problem.  I'm still pretty new to Linux, but I'm learning.  I would really appreciate the help on this one.  Thanks everyone.

---

### Post by holastickboy on 2012-11-25
What you are experiencing is a set of well known issues. The problem with the disappearing character with inspections, no characters on maps is a problem with the WoW OpenGL renderer.  Note that this is not a Linux issue, it happens if you use OpenGL on Windows too!

The only way to fix those issues is by using Direct X mode, which is not very quick if you are using vanilla Wine to run it.  I have a GTX 460, and run WoW using Crossover games, with Direct X support, and usually get well over 100 fps.  There are addons that make life a little easier while questing, particularly Carbonite, as it adds its own map system that shows the character (and adds a location arrow).  Check out the crossover games demo, see how that works for you, and I recommend purchasing it if you can afford it.

Edit: Forgot to mention... To allow multitasking with WINE and second monitor, I found that enabling virtual desktop in the Wine settings helped and just set the resolution I wanted. I also enabled window mode in the WoW settings, but not the Windowed (Fullscreen) version, which seems to have the same issue.

---

### Post by djxvillain on 2012-11-25
> **holastickboy said:**
> What you are experiencing is a set of well known issues. The problem with the disappearing character with inspections, no characters on maps is a problem with the WoW OpenGL renderer.  Note that this is not a Linux issue, it happens if you use OpenGL on Windows too!

The only way to fix those issues is by using Direct X mode, which is not very quick if you are using vanilla Wine to run it.  I have a GTX 460, and run WoW using Crossover games, with Direct X support, and usually get well over 100 fps.  There are addons that make life a little easier while questing, particularly Carbonite, as it adds its own map system that shows the character (and adds a location arrow).  Check out the crossover games demo, see how that works for you, and I recommend purchasing it if you can afford it.

Edit: Forgot to mention... To allow multitasking with WINE and second monitor, I found that enabling virtual desktop in the Wine settings helped and just set the resolution I wanted. I also enabled window mode in the WoW settings, but not the Windowed (Fullscreen) version, which seems to have the same issue.

Wow...  Everything seems to be running perfectly now.  Thank you so much for your help.  This is why I love the Linux community ^_^

EDIT:  All of the problems addressed initially are now solved!  Unfortunately, if I run the game at full specs (which was fine on Windows), the game  can't seem to handle it, and has pretty bad lag issues.  I know my graphics card can run this.  It seems like this is the very very very last problem until my WoW is perfect.  Right now I have to run the game at about "fair" performance in order for it to be playable.  Thanks so much for everything.  If you have any tips on this new issue, I would greatly appreciate it :]

---

### Post by Dlambert on 2012-11-28
Update to the latest (310) Nvidia drivers and use the Threaded optimization on Multi core systems:
 
> 
Nvidia users with driver version 310 or newer can use the new **threaded optimization **(Renderer thread is offloaded to a seperate core) on multicore boxes with

# cd PATH_TO_YOUR_WOW

# __GL_THREADED_OPTIMIZATIONS=1 WINEDEBUG=-all wine wow-64
Disabling debugging is neccessary, otherwise you will get less than 10 fps. Mileage may vary, but a increase of more than 50%  of the fps seems common. This works both in opengl and in direct3d mode. 



---

### Post by holastickboy on 2012-11-28
yeah, there definitely is a performance hit. But it's getting better, and still very playable!

---

