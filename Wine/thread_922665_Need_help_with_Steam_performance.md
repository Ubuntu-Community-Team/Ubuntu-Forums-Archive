---
title: "Need help with Steam performance"
date: 2008-09-17
forum: Wine
---

### Post by snusnu on 2008-09-17
actually, i need help with steam games performance.  what i have in vista is roughly ~150fps, right now my estimation is <5fps running in Wine (with day of defeat source).

ive followed the guide located [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4571) to install everything.

i am currently using wine-1.1.4, and i have tested it with wine 1.0 but received about the same performance.  when you get in game, when you click "server", you get a the list of servers that are invisible but you can select them.  the tahoma.ttf file is already in the windows/fonts folder, so that should not be an issue.  when you get in the server, you're missing the flags icons at the top left hand, the reload icon at your bottom lefthand, crosshair is missing, and any interactive hotkeys do not bring up their associated bind (map, score, voice command lists, etc).

i installed my drivers with envyng, and i am using xorg-x11 7.3.  compiz-fusion using glxgear produces ~ 12000fps.

a friend of mine said i might need to use opengl, and right now its using my hardware to render stuff.  is this the case ?  under the options it says its using a version of directx9.0, but since its not windows... is there anyway to force it to use opengl ?  does wine do this itself ?  im kind of a linux novice, so please bear with me.

my hardware stats are:
q6600 b3 stepping
8GB ddr2 800 ram
2x 8800gts 640 vid cards in sli

thanks !

---

### Post by Brynster on 2008-09-17
Firstly i would recommend the following

set the launch option of -dxlevel 81 do this by right clicking the game in steam and the clicking on properties launch options

The reason for this is that directx emulation n wine is good upto directx 8.1. Directx 9 is improving but not upto the standard of 8.1 yet.

I would also recommend only using a resolution on 1024 x 768 as in certain circumstances and configs where a resolution greater than this has caused significant slow down.



if i can help further please don't hesitate to ask/post/pm me.

---

### Post by snusnu on 2008-09-17
ive tried adding -dxlevel 81 to the launcher line, but i havent seen much if any performance gains.  im currently using 1680x1050 resolution... would having a larger resolution really kill performance by that much ?  im thinking there might be something wrong, since the crosshairs and all these icons are missing/not displaying properly.

ive done a data integrity check from steam and it says everything is a-okay, but im not quite sure.

---

### Post by Bios Element on 2008-09-17
A high res. can easily slice half your FPS off. It sounds weird but i spent hours tuning it for performance and it does make a difference. Also try disabling compiz while gaming. It'll help with your FPS some.

---

### Post by snusnu on 2008-09-17
even with my hardware ?  it seems a little too incredulous to believe that the resolution at a 16:10 aspect widescreen level is enough to cripple the game.  im not talking a little decrease in performance, its going from 100% performance to less than .5%

when i get home ill try it out though.. but even if that is the reason, why would that make my icons/crosshair/lists disappear ?  a low fps would not hide those

---

### Post by snusnu on 2008-09-18
okay, just tried it with a lower resolution.  did not fix it.  i also tried with -dxlevel 81 just now, also did not work.

---

### Post by snusnu on 2008-09-18
okay, so my xorg is also using 35-40% of my cpu at idle... would this be a root issue that would also cause this ?  i ran "top" and it looked like dod:s was using 90% of my cpu as well.

---

### Post by hikaricore on 2008-09-18
Have you any way to test if SLI is actually working properly?

If you're using two cards and for some reason SLI isn't working, this could adversly affect your video performance.
Be sure to have the latest binary driver from nvidia installed for best results using the 8xxx series.

---

### Post by snusnu on 2008-09-18
turns out sli isnt even enabled, i didnt even build nvidia-xconfig with it.  i tried it on, day of defeat source refused to even enter a server... stalled and crashed as you try to join a game.  i think im stuck with rebooting into vista just so i can play games :(

on a side note, i fixed xorg's cpu usage by updating my libgnome.  does anyone know if i need to update anything for wine ?  ive been getting a few weird errors here and there and i'm feeling i might be missing something

also, should i try running an older version of wine ?

---

### Post by snusnu on 2008-09-23
installed wine-1.1.5, still same issues.  any ideas guys ?

---

### Post by snusnu on 2008-09-30
> **Brynster said:**
> Firstly i would recommend the following

set the launch option of -dxlevel 81 do this by right clicking the game in steam and the clicking on properties launch options

The reason for this is that directx emulation n wine is good upto directx 8.1. Directx 9 is improving but not upto the standard of 8.1 yet.

I would also recommend only using a resolution on 1024 x 768 as in certain circumstances and configs where a resolution greater than this has caused significant slow down.



if i can help further please don't hesitate to ask/post/pm me.

okay, i must be retarded.  didnt see that in the advanced properties, and when i changed it, it boosted the fps to ~28-35FPS on average.  this is much better than what it was, but i was wondering if there was anything else i could do to bump up my FPS ?  if i can get it to around 70-90FPS, ill just deal with it.

edit:  reducing my resolution changed nothing, so i just left it at 1680x1050 (was same fps at 1024x1080).

also, heres some more information 
glxgears produces:
65468 frames in 5.0 seconds = 13093.461 FPS
65315 frames in 5.0 seconds = 13062.997 FPS
62175 frames in 5.0 seconds = 12434.882 FPS

glxinfo:
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8800 GTS/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.12
direct rendering: Yes

---

### Post by killguta on 2008-10-01
PM me if you manage to find out the problem :) . I really want to stop using Windows FOR EVER!!!

---

