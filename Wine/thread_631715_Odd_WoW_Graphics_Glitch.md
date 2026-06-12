---
title: "Odd WoW Graphics Glitch"
date: 2007-12-04
forum: Wine
---

### Post by Fotonurth on 2007-12-04
I've been playing WoW on 7.10 and Everything runs fine spare for 3 things. And I think they're related.

1. Low framerate
2. The panels on the top of the screen cuts in and so do other windows on the desktop
3. This Screenshot. (See Attachment)



I followed the step by step installation guide. I've searched Wine HQ. I even looked at the trouble shooting site. 

I'm running it on a laptop
with 1 gig of RAM
2 GHZ Centrino Duo
intel 945 M Express On-Board Graphics (Using the i810 Driver )

And the latest version of Wine. What else can I give you that may be helpful?

---

### Post by gazj on 2007-12-04
Try this

[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

It's a gentoo how too, but anything from step 6 down pretty much applies no matter what version of linux you use, the registry edit makes pretty much doubles the frame rate on my machine.

other things maybe to note, try turning off compiz window effects, make sure you card is set up for opengl (run glxgears from a terminal, make sure you get a decent fps)

other than that i'm not sure, i have nvidia card so maybe it's card specific problem, lets hope not :)

---

### Post by Fotonurth on 2007-12-04
Thanks for the link. And the answer.

I've done the Registry hack.
The
> SET gxApi "opengl"
 tweak, Improved the white stuff and FPS but the character models are painfully distorted.

So it may be a hardware issue. I reeeallly hope not.

---

### Post by gazj on 2007-12-04
glad to help, what fps do you get by the way, because mine is still bad, but my specs are behind yours

AMD athlon xp 2400
1gb Ram
Nvidia Geforce Fx 5200 with 128mb ram - ouch

---

### Post by Fotonurth on 2007-12-04
Well it's not fixed but It's tolerable. I'm getting a mere 15 fps. x.x

---

### Post by gazj on 2007-12-04
Thats around why i get, although i don't know how it compares to windows, have never ever played it in windows, lol, it is just bearable, until you have pvp with someone i find.

I may have to install a windows partition if you do get a significantly better frame rate in windows

---

### Post by Fotonurth on 2007-12-04
In Windows I get near 60 FPS on max graphics.... In ubuntu I get 15 fps with everything at a minimum.

---

### Post by gazj on 2007-12-04
hmm, sounds like i will have to get a win2000 partition then, what a shame.  Well i have been playing wow for over a year, and never got any better than about 15fps so please let me know if you find away of increasing it. :)  Sorry i can't help you anymore. :(

---

### Post by hikaricore on 2007-12-04
The problem is with the intel drivers and the lack of hardware/driver opengl support on intel integrated chipsets.  Intel has contributed just the minimum to developing their drivers for their lackluster hardware.  Some users have luck with d3d mode, but not all.  Sorry to hear of your troubles.

---

