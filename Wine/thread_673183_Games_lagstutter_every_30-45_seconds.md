---
title: "Games lag/stutter every 30-45 seconds?"
date: 2008-01-20
forum: Wine
---

### Post by reverend1313 on 2008-01-20
I have what seems to be a wierd problem. ANytime I try to run a game two exanples ive test WOW and Guildwars. It runs ok kinda laggy but ok. But then stalls/lags hard for 3-4 seconds. This happens about ever 30-45 seconds. Its totally wierd because it does it in Cedega and Crossover Office. I havent been able to get Wine to work at all. Too much config for this newbie at the moment. Anyone seen anything like this before?

Oh and I installed the latest nvidia drivers with the envy tool. 

Asus Z71v laptop
2gbs of ram
GF 6600 
intel 2.2ghz
ubuntu 7.10

---

### Post by reverend1313 on 2008-01-20
I just tested WoW in windows, I have a dual boot going. and I noticed my Frames per second were around 28-40 in Windows XP but in the same area of the game in Ubunutu they were suck at 10 or lower.

---

### Post by hikaricore on 2008-01-20
Are you running WoW in opengl mode?

---

### Post by reverend1313 on 2008-01-21
When I add the comands to the config.wtf to run it in openGL the game just opens up to a black screen. So I dont think its working correctly. Even though GLXgears shows everything is ok maybe the Nvidia drivers didnt install right?

---

### Post by oedipuss on 2008-01-21
Are you running wow with desktop effects enabled? If so, it can cause significant lag and possibly other problems. 
Try disabling compiz with the command : metacity --replace , and then launching wow.
(metacity is the original gnome window manager, without any fancy effects)

If you've already done this, try following a how-to for optimizing wine. The sticky one in this forum ( "what I've learned about wine") is nice , and not too hard to follow.

PS: the command ' glxinfo | grep -i direct ' should display "Direct Rendering : YES" if your nvidia drivers are installed correctly.

---

### Post by banewman on 2008-01-21
You could type -
top
in a terminal and see if there is an application that runs at that cycle - mail checkers or something similar can hog memory and/or cpu
:)

---

### Post by reverend1313 on 2008-01-21
Thats seems to have worked. The performance is still a little slow for what it should be but at least its not a real pain in the butt now. So I can take my time with tweaking wine and not have to worry to much about it.

I had had a lot of desktop effects on, but mostly was just using the Avant bar at the bottom. Which is a prettuy cool bar. I will just have to see about making a script to turn it back on and off when I wanna play or something

---

