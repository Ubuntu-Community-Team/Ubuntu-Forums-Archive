---
title: "Starcraft resolution issues"
date: 2008-03-01
forum: Wine
---

### Post by BallsMcGregor on 2008-03-01
Hi, I'm running Starcraft: Broodwar under wine 0.9.55 (Ubuntu 7.10) on a laptop with a 1280x800 display and I'm having a problem.  Basically Starcraft can only run in 640x480, so when I play it in full screen mode it stays with the 4:3 ratio and the bottom portion of the game is cut off the screen.  Is there anyway I can fix this?  In windows the game just stretches to fit the screen, this is a fine solution.  I'd really appreciate any help, thanks!

---

### Post by uberlube on 2008-03-01
You should be able to set the screen resolution from winecfg

---

### Post by BallsMcGregor on 2008-03-01
Update: I'm now using Cedega, since I wish to play on battle.net, and SC on wine has plenty of issues on battle.net.  On Cedega battle.net works 100% perfectly, but I still have the same resolution issues.  It works perfectly in a window, by the way, but I wish to play it fullscreen.

---

### Post by yabbadabbadont on 2008-03-01
Well, since you have paid for Cedega, you can open a support request with them while you wait to see if anyone in the forums can help.  That *is* one of the advantages of Cedega over wine.  (well, that and copy protection support)

---

### Post by chewearn on 2008-03-01
I have the same problem with a 1280x800 as well.  In my case, I highly suspect the problem lies with the nvidia driver.

Starcraft is hardcoded to 640x480.  When set to full screen, The scaling to the screen resolution is done by the graphics driver.  Every possible options I have tried to set to the nvidia-settings have not solved this problem.  Furthermore, to remove the starcraft and wine from the equation, I tried setting my desktop resolution to 640x480.  The result is the exact same problem.

---

### Post by BallsMcGregor on 2008-03-01
> **yabbadabbadont said:**
> Well, since you have paid for Cedega, you can open a support request with them while you wait to see if anyone in the forums can help.  That *is* one of the advantages of Cedega over wine.  (well, that and copy protection support)
From what I can tell, Cedega support is abysmal at best.  

> **AstalaVista said:**
> I have the same problem with a 1280x800 as well.  In my case, I highly suspect the problem lies with the nvidia driver.

Hmm, I have a nvidia card as well, so that is very likely.  I'll be sure to let you know if I find a solution.

---

### Post by yabbadabbadont on 2008-03-02
Since Starcraft doesn't need 3d acceleration, you might try using the open source, nv driver, just to see if it works any better.

---

### Post by Compactman on 2008-03-07
I can confirm this issue as well.  Starcraft seems ot default to 640 x 480

I'm running dual monitors in nividia twinmode.

---

### Post by komsas on 2008-03-24
I have same problem, my resolution 1280x800 too. Someone know how to solve it?

---

### Post by nonmi9 on 2008-06-03
I own an HP dv6425us, nVidia go 6150 1280x800 and same problem.

---

### Post by medic2000 on 2008-06-03
> **AstalaVista said:**
> I have the same problem with a 1280x800 as well.  In my case, I highly suspect the problem lies with the nvidia driver.

Starcraft is hardcoded to 640x480.  When set to full screen, The scaling to the screen resolution is done by the graphics driver.  Every possible options I have tried to set to the nvidia-settings have not solved this problem.  Furthermore, to remove the starcraft and wine from the equation, I tried setting my desktop resolution to 640x480.  The result is the exact same problem.

Yes it is the nvidia driver. Before installing the driver i tried the SC without no resolution problem. After nvidia-glx-new bye bye proper resolution :( 

I wish we find a way soon.

---

### Post by nonmi9 on 2008-06-04
Any News on how do fix this?

---

### Post by medic2000 on 2008-06-05
Bump!

---

### Post by luke16 on 2008-06-15
It would be cool if there was a way to have wine to force stretch apps to whatever resolutions you wanted, along with an option to capture the mouse to the window. It would make games such as starcraft actually playable in a window so that you can play the game without leaving the desktop.

Also, for the record, SC switches to the correct res, stretching rather than cutting off anything, so it looks like this problem is confined to just 1280x800 monitors.

---

