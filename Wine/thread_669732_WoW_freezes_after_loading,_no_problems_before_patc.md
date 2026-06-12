---
title: "WoW freezes after loading, no problems before patch"
date: 2008-01-16
forum: Wine
---

### Post by person_99 on 2008-01-16
I searched around the forums, and I can't find anything useful.
In december, I was happily playing WoW through Wine 0.49 , no problems.
I lost my WoW subscription, and had to wait until now to renew it.
Now, WoW runs fine, lets me select my character, and it loads. The second the loading screen is closed, and the 3d world is rendering, WoW crashes, showing everything normal but a few short glowing green lines on the screen. Looks sort of like a magic trail coming from a shaman or something.

It doesn't matter what world I am on, what character I play, still pulls it.
System specs before and after crashes:
As shown in my profile, Kubuntu 6.10 Edgy Eft.
Geforce 6200 256mb DDR2, SM 3.0.
1gb RAM DDR.
AMD Athlon 2800+ x64

Things that changed before crashes:
Nvidia drivers
Wine version
Motherboard, nothing with it.
WoW login screen FPS (Can't go by anything else yet)
WoW version

Before:
Nvidia Linux x86, 100.14.19
Wine 0.49
Motherboard, ASRock KGB (or KBG, not sure) Upgrade 768 (Or something)
WoW got around 15-19FPS at the loading screen.
WoW version (Old, December 1-Jan-1 at least)
After:
Nvidia Linux x86, 169.07
Wine 0.52
Nforce-4 Socket 752 Motherboard.
WoW gets around 30fps at the loading screen.
WoW version (New Patch) 

Can anyone help me fix this problem?

Edit: Before, I was running my video card through an AGP slot on my old motherboard, now it is running through an AGR.
The only performance changes have been good.

Edit: Problem solved! 
Switched renderer to Open GL, also fixed framerate issues, player aura issues, and more.
How (Also shown in the link posted by Foolsh) :
Go to your World of Warcraft directory. Something like (home/youruser/World of Warcraft). go to the WTF folder, and open Config.WTF with a text editor.
Add the line ```
SET gxApi "opengl"
``` and save.

---

### Post by foolsh on 2008-01-16
is WOW  using open-GL rendering or did you not set that option. 
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)
should be able to help sort out the problems

---

### Post by person_99 on 2008-01-16
I did not, I just installed and played (Did not change any game files, I installed it in December, and  still have the same install.).

---

### Post by person_99 on 2008-01-16
Hey, switching the renderer to OpenGL not just fixed the problem, but also fixed all of my framerate issues and everything! Thanks!

---

