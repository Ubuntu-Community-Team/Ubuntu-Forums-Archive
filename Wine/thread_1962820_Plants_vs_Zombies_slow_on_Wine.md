---
title: "Plants vs Zombies slow on Wine"
date: 2012-04-21
forum: Wine
---

### Post by mungstro on 2012-04-21
Here's the thing, I'm running Plants Vs Zombies on wine; it installs ok, it runs almost fine

However, there are two things about gameplay, and i think they're related:

1.- Game start menu runs very slow, same as plant selecting menu

2.(more important)- In normal gameplay, speed is normal, but when the screen is full of zombies (ex. endless survival in late flags), the game is REALLY slow

Is there any way to work around this??

---

### Post by Mark Phelps on 2012-04-21
> **mungstro said:**
> Is there any way to work around this??

If the game is running slow because you're using open-source graphics drivers, meaning you're getting little or no hardware acceleration, then unfortunately, the answer would depend on if you could install restricted drivers.

If you're already running restricted drivers, the answer is likely to be NO.

---

### Post by mungstro on 2012-04-21
I believe i'm running on open source drivers...

I'm kind of new at this, so... how could I install these restricted ones?... or even know if i can?

Thanks in advance

---

### Post by uRock on 2012-04-21
Moved to the Wine sub-forum.

---

### Post by strafe_sawdoffe on 2012-04-21
I once had a very similar problem with PvZ, and I actually fixed it from within the game itself. From the main menu, go to options and turn off Hardware Acceleration. You may also have luck experimenting with running the game in a window (as supposed to fullscreen, which I believe is the default). That is also under the options menu, plus you can do it through Wine itself.

About the proprietary drivers: Ubuntu will usually notify you if there are optional drivers to install, but regardless... in Gnome 2.x, you can get to it through System -> Administration -> Hardware drivers; in Unity it's System Settings -> Additional drivers.

Not sure where it is in Gnome 3, KDE or XFCE off the top of my head...

Finally, PvZ (and actually all of PopCap's stuff) runs more or less perfectly on Wine, so the Wine Forums probably have tips published for the most common performance issues with PopCap stuff.

Hope this helps.

---

### Post by mungstro on 2012-04-21
Hi, thanks, the hardware acceleration is already off, but i'm gonna try on window mode, thanks... :)

and thanks also about the drivers... ;)

---

