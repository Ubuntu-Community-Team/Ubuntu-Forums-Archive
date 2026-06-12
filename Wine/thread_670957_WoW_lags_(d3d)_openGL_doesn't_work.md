---
title: "WoW lags (d3d)/ openGL doesn't work"
date: 2008-01-18
forum: Wine
---

### Post by mumixam on 2008-01-18
Hey, I have just installed wow on my laptop and I can't get it to work properly. At first I had problems starting WoW, it just came up either with a black screen or just as a resolution problem, where I could hear the sound but still couldn't see the game. I solved the problem by simply reinstalling ubuntu, getting all the updates in Synaptic, getting me new copy of WoW folder and getting wine again. 
 I can now run the game in -d3d but I can hardly log to my account due to HUGE lag. In -opengl the game doesn't even start.
 I have heared that the new wine 0.9.46 version does not go well with opengl or does not support opengl at all, but i don't know how much of it is true and if they have fixed the bug. I also heared that ubuntu is missing X3100 card drivers and that it might be the case and that 1Gb ram might be to little for x3100 type of cards since they use ram but right now I'm confused and asking for your help =) 

here is some usefull info. if anything more is needed i'l post it:
(Amilo pi 2515)
graphic card: x3100 
dual core 1,8 x 2 intel
wine 0.9.46
1gb ram

glxinfo | grep rendering 
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

however BEFORE updating everything in Synaptic (just after the ubuntu reinstall), the answer to <glxinfo | grep rendering> was Yes.

ps: i don't thing hardware could be the problem since i saw wow work on similar type of laptops on windows machines, but i REFUSE to install windows and want to get it to work on ubuntu =)

---

### Post by Black_Heart on 2008-01-20
well i think the only problem would be the video card drivers... and if you look at this link 

[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100)

it looks like there is a linux driver out for that video card. just make sure you ctrl + alt + f2 out before installing the drivers cuz they wont install while your logged into the desktop :)

---

### Post by mumixam on 2008-01-22
I think I'm little too unexperianced with linux to understand scriptc like that. Last time I played with xorg.conf i could not load my graphic intarface again and had to reinstall OS over again. There must be a way to fix this... I will try to install game "inside" wine's virtual partition C:, maybe that will fix some problemms with opengl at least...

---

### Post by norsk on 2008-03-09
I have yet to find a decent write up explaning how to install drivers for the X3100 GPU, but it seems like it will be figured out soon

---

### Post by buried on 2008-03-10
so I guess you Graphic card is ATi, try going to restricted drivers and installing ATI, if that doesn't work try Synaptic Package Manager and search for ATI.
Hope this helps you.

---

### Post by whaevr on 2008-03-10
You could try [Envy](http://albertomilone.com/nvidia_scripts1.html)
It automatically downloads the correct driver from the product site (Nvidia or ATi)
So if what buried said is true, and you have an ATi card Envy should work fine for you. I used it to update the driver for my Nvidia card, the driver I downloaded from restricted device manager was a bit outdated, it was like 100.4 and the one Envy installed is 169.12 :o

---

### Post by jacob01 on 2008-03-10
he is running an intel igp  not an nvidia or ati  

I have the x3000 and i haven't had much luck with game other than like assault cube and open arena but your card may be a different story although i believe they both use the same driver.


but im getting a new card soon so im hoping to fix my problems:)

i hope you find a solution to your problem!!!

---

