---
title: "Opengl Wow fps low"
date: 2007-05-27
forum: Wine
---

### Post by Elvish Legion on 2007-05-27
When I try to start wow from wine in opengl mode even the opening menu has REALLY low FPS (1-2).

System specs:

ATI Radeon Mobility 1100 
AMDTurion x2 1.6 proc
1.5 gigs ram (128 go to the graphics card)

The game loads up so much smoother with d3d than opengl which everyone says should not be the case.

Any thoughts?

---

### Post by Nehvrook on 2007-05-27
Wich howto did you follow to install WoW? Did you apply the opengl registry tweak? And did you make sure it's spelled properly (Copy and pasting stuff is the best way)

If you did all that then I'm not sure, but ATI cards have a bad reputation with Wine from what I've read.

---

### Post by Elvish Legion on 2007-05-27
[http://ubuntuforums.org/showthread.php?t=312482&highlight=world+of+warcraft](http://ubuntuforums.org/showthread.php?t=312482&highlight=world+of+warcraft)

That howto, I'm pretty sure I applied the registary change, will check when I Get home tonight.

Will that change help the sluggish login scren?

---

### Post by ShadowFlar3 on 2007-05-28
You should start with checking if your ATI drivers are working properly in the first place.

glxinfo | grep rendering

You should see Direct rendering: Yes.

After this you should move on to tweaking your config.wtf. I suggest using same resolution, color depth and refresh rate as your desktop to max out performance / stability.

---

### Post by hikaricore on 2007-05-28
Useful info for the OP, but...

Anyone who's ever played WoW know that colour depth set in config.wtf is ignored and reset upon starting the game.  :P

---

### Post by ShadowFlar3 on 2007-05-28
If you have SET hwdetect "0" in config like you should NOTHING is ignored or reset.

---

### Post by nenitza on 2007-05-28
> **Elvish Legion said:**
> When I try to start wow from wine in opengl mode even the opening menu has REALLY low FPS (1-2).

System specs:

ATI Radeon Mobility 1100 
AMDTurion x2 1.6 proc
1.5 gigs ram (128 go to the graphics card)

The game loads up so much smoother with d3d than opengl which everyone says should not be the case.

Any thoughts?

[http://forums.wow-europe.com/thread.html?topicId=286873872&sid=1](http://forums.wow-europe.com/thread.html?topicId=286873872&sid=1) So blizz issue.
This happens for me too on both my machines. Some windows users have 5-10fps.

---

### Post by ShadowFlar3 on 2007-05-28
Ok here's why this is not the same issue as what's discussed in that thread because:

1) All windows users run the game in d3d, and Elvish Legion said he has problems with specifically opengl. On wine and cedega, wow runs much better in opengl than d3d so there's definetly something wrong here.
2) This is not a problem caused by the latest patch, at least no one has posted anything that indicates so.

So I'm still waiting for the OP's response to my advice.

---

### Post by Elvish Legion on 2007-06-01
> **ShadowFlar3 said:**
> Ok here's why this is not the same issue as what's discussed in that thread because:

1) All windows users run the game in d3d, and Elvish Legion said he has problems with specifically opengl. On wine and cedega, wow runs much better in opengl than d3d so there's definetly something wrong here.
2) This is not a problem caused by the latest patch, at least no one has posted anything that indicates so.

So I'm still waiting for the OP's response to my advice.

Well making the wtf changes you suggested helped slightly, I'm not sure if this is a hardware issue or not....I think it may just be my card.  I'm building a desktop here in a month or two so I guessI can deal with dual boot for a little longer

---

### Post by Elvish Legion on 2007-06-03
I just thought of something, may these issues be due to the fact I'm trying to run the game in fullscreen? Would windowed be better?

---

### Post by Nehvrook on 2007-06-03
In my experience of WoW running windowed ran slower than running full screen. But saying that anything is worth a try right?

Just about that registry entry, make sure it's spelled right and you remember that it's all case sensetive. When I first installed the game I spelled it wrong and my framerate never went over 10. When I fixed it I got 50+ framerate all the time.

If you're building a new PC, get an NVidia card :P

---

### Post by Ferrat on 2007-06-03
The FPS drops seems to be randomly affecting people from what I gather after reading the wow-forum thread, some people got it, others didn't so prolly a small glitch somewhere in the patch that is haunting you and your FPS. 

I assume you have the latest version of wine 0.9.38 and the latest grafic drivers from ATi (8.37.6)?

---

### Post by Elvish Legion on 2007-06-03
Also I just noticed something

Running glxgears I used to run at 1500fps, I downloaded easyubuntu (because I'm lazy) and installed the ati driver thinking it would upgrade it, now I've dropped to 900fps (this is all while watching the gears) 2500 while the gears are minimized

I'm going to try installing the driver from the ati site to see if that helps

---

### Post by Elvish Legion on 2007-06-03
jduvall@aspire:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

jduvall@aspire:~$ glxinfo | grep renderingdirect rendering: Yes

jduvall@aspire:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:

I've tried to edit my config.wtf and noticed the changes are sticking, it keeps reverting to 800x600 not 1200x800

---

### Post by Ferrat on 2007-06-04
1200x800??

you don't mean 1280x720 or 1280x1024 ??

---

### Post by Ripfox on 2008-01-02
My laptop is 1200x800

---

