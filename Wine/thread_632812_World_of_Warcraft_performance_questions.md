---
title: "World of Warcraft performance questions"
date: 2007-12-05
forum: Wine
---

### Post by tabithaboof on 2007-12-05
I have spent a couple of days battling with Wine and Wow and finally managed to get everything to go in game and playable yesterday (yay)

First up are my system specs. I appreciate this isnt really a gaming Laptop but:

Intel core 2 duo / 1GB RAM / Intel Graphics Media Accelerator 950 / OpenGL version string: 1.3 Mesa 7.0.1

And I have done the regedit, open GL tweak, and done the normal edits to me config.wtf file. I think i didnt make any mistakes.

Here is were it got interesting. I managed to get in game (my start command is wine WoW.exe -OpenGL) but the character models were all broken with arms and swords floating in wierd places and the game ran at a punishingly slow sub 1 fps. I then disabled fullscreen glow in config.wtf which made no difference at all.

I tried to adjust my video setting but the game locked. In the troubleshooting guide it recomends running in d3d mode (I dont acctually understand what that means) to adjust the video settings then changing back. I started in d3d mode and to my surprise everything worked. I am running on the minumum possible settings for video, I get about 6 or 7 fps outside and about 35 fps inside. I amdit this sucks but its playable.

Does anyone have any idea whats going on? it seems like openGL doesnt work for me but d3d does and this seems the opposite to most people.

Also I thing only 1GB of ram is rairly low. I was thinking about putting in another 2GB, is this likely to improve my performance at all or is WoW much more dependant on the video card?

Sorry about the long post!

---

### Post by hikaricore on 2007-12-05
If it helps you understand the situation any:

In the beginning I went from playing with 1gb of ram and an intel chipset and getting 7fps @ 800x600 /w settings on low to 2gb of ram and an Nvidia GeForce 8600GT getting 70+fps @ 1600x1200 /w setting maxed.

Ram is definately important, but if your video hardware isn't up to par, all the ram in the world won't help you.

---

### Post by Fotonurth on 2007-12-06
I removed the opengl twek from the config.wtf

and it runs decently enough to play. (I'm playing on almost the exact machine you are) some wierd graphics bugs, like white textureless models and such, but I had the same issue, and I can't seem to find a fix. If I come up with something I'll let ya know

---

### Post by tabithaboof on 2007-12-06
Im still looking, maybe something will turn up. I ordered more RAM so I will se if that makes any difference. 

also, are you running in d3d mode?

---

