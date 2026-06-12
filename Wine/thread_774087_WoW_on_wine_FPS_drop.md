---
title: "WoW on wine FPS drop"
date: 2008-04-29
forum: Wine
---

### Post by sedition on 2008-04-29
Hello all,

Let me start by saying that I've been an Ubuntu user for some time now (since about 4.10) and have been playing WoW on Ubuntu for over a year, so far every issue that I've come up with has been covered and handled by this community and I have never seen such a responsive helpful group; so thanks.
Since Hardy dropped, I decided to do a fresh install of it and switch up to the 64 bit version, but keep my /home partition, so I would have to reinstall/update/patch WoW. I install the restricted drivers for my nVidia card (spec in sig), update xorg.conf (didn't add the correct driver for some reason), ran an apt-get for nvidia-settings and wine, rebooted and checked glx gears. I averaged about 13700 fps in glxgears. Yesterday, I ran WoW and standing by the mailbox in Stormwind I got about 10 fps. As you might assume, I previously got much higher than that. After logging out WoW, I reran glxgears and it had dropped to 5500 fps. Tried again same result. Logged out of Ubuntu, logged back in and reran glxgears. Back up to 13700 fps. Ran Wow, 10 fps, reran glxgears: 5500 fps.
So, I guess to sum up, has anyone ever ran in to this or a similar issue? You get an expected result from glxgears, run software that uses OpenGL, and then your performance drops? I'm more than willing to admit I may have missed something in configuration of my box, any idea of what it could be?

Thanks in advance,
-sed

---

### Post by situz on 2008-04-29
Never had that problem, you didn't say anything about what you did to your config.wtf file, and wine settings.. 

maybe you can find your solution here:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

tho you probably know about all this :P

good luck anyway

---

### Post by sedition on 2008-04-30
Fixed. 
This post is just yet another example of me working my *** off, giving up and then sorting stuff later on by accident. :)

Config.wtf:
Set pixelshaders "0"

Even though you do the edit, run the game and this setting is gone, still runs better than before. Still only getting about ~22fps by a busy mailbox in a major city, but it's tolerable. I would think that my setup would get a much better frame rate, and a bit curious as to what others are getting...

---

### Post by thisismalhotra on 2008-04-30
> **sedition said:**
> Fixed. 
This post is just yet another example of me working my *** off, giving up and then sorting stuff later on by accident. :)

Config.wtf:
Set pixelshaders "0"

Even though you do the edit, run the game and this setting is gone, still runs better than before. Still only getting about ~22fps by a busy mailbox in a major city, but it's tolerable. I would think that my setup would get a much better frame rate, and a bit curious as to what others are getting...

IDK anything about ur setup but I have nvidia 8800 GT with 512 VideoRAM and I get 60 FPS consistently which drops to 43 in major cities like ogrimmar.

---

