---
title: "[SOLVED] The Elder Scrolls III: Morrowind GOTY edition; won't start; fullscreen error"
date: 2008-03-21
forum: Wine
---

### Post by Majin Zero on 2008-03-21
exact error is:

Render Creation Error: "Creation failed: could not match desired fullscreen mode"

anyway to start Morrowind in windowed mode?

I have two monitors at different resolutions running in "one screen mode" 

Or do I need to set my monitors differently?

BTW; I'm running it in the latest version of WINE from the repos, but I don't think that has any effect at this point.

---

### Post by DarkSim on 2008-03-21
Worth a shot to try FPS Optimizer to set your resolution. Make sure you set the refresh rate or whatever its called as well. Default is 0 Hz for some reason. I had a heck of time wondering what was going on when the game would stay at a black screen.

[http://planetelderscrolls.gamespy.com/View.php?view=Utilities.Detail&id=22](http://planetelderscrolls.gamespy.com/View.php?view=Utilities.Detail&id=22)

Thats the only part of FPS Optimizer that works on Linux. So after setting the resolution try MW again through the launcher you already have not FPS Optimizer.

---

### Post by Majin Zero on 2008-03-21
> **DarkSim said:**
> Worth a shot to try FPS Optimizer to set your resolution. Make sure you set the refresh rate or whatever its called as well. Default is 0 Hz for some reason. I had a heck of time wondering what was going on when the game would stay at a black screen.

[http://planetelderscrolls.gamespy.com/View.php?view=Utilities.Detail&id=22](http://planetelderscrolls.gamespy.com/View.php?view=Utilities.Detail&id=22)

Thats the only part of FPS Optimizer that works on Linux. So after setting the resolution try MW again through the launcher you already have not FPS Optimizer.

Ok, I set it to super low rez, 640XI forget the other number

and it loaded fine.

Now, how can I get it so I can move the window around; and resize it?

Should I set wine to allow my window manger to manage those windows?

---

### Post by Majin Zero on 2008-03-21
> **Majin Zero said:**
> Ok, I set it to super low rez, 640XI forget the other number

and it loaded fine.

Now, how can I get it so I can move the window around; and resize it?

Should I set wine to allow my window manger to manage those windows?

I did that and I was able to move the window to my larger monitor

Now, do I need to use the FPS optimizer to set the rez?

---

### Post by Majin Zero on 2008-03-21
I can no longer start the FPS optimizer

it keeps saying that it's already running, even if I log out then back in

I tried deleting the folders with the program in it, and re-extracting it and running it; same thing

---

### Post by Majin Zero on 2008-03-21
looks like it runs at start up

I killed the process, and now I can open it again

---

### Post by Majin Zero on 2008-03-21
I did that, changed the rez to my larger monitor's rez, but the title bar gets in the way, and I can't move the actual game window so it's filling the screen.

I just want it to be maximized on the one monitor I have

which is 1360 X 768

---

### Post by Majin Zero on 2008-03-21
cool, I turn off WINE letting my window manager control windows; and now it's centered perfectly on my good monitor while at my max rez

^_^

the optimizer program is kinda...in the way though, it won't go behind other windows, and it won't minimize properly, it just covers up a bit of my lower left screen.

---

### Post by DarkSim on 2008-03-21
You shouldn't need to use the optimizer program each time you want to play. Set it and forget it. :D

Although if you mess with the options in the Morrowind Windows splash screen you'll have to use the optimizer program again. It gets reset by that.

---

