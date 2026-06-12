---
title: "[SOLVED] Steam games running slowly"
date: 2008-08-02
forum: Wine
---

### Post by ilikeroflcopters on 2008-08-02
I installed steam via wine and it works fine when i start it up
But when i start to  run a game, like Defcon, it takes a while for it to start up and then when it is finally open it runs at a really slow frame rate. How do i make wine/games inside of it run anyfaster or is it maybe a hardware problem from my end?

---

### Post by aoanla on 2008-08-02
It's very difficult to answer this question without you actually telling us something about your computer!

Steam *does* take a while to launch some games, but you shouldn't be having performance issues with the games themselves.

Can you tell us what your processor and graphics card are, what version of Ubuntu (and graphics drivers) you have installed, and what the result of typing

glxinfo | grep render

in a terminal is?

DEFCON, by the way, should have a linux-native client, which should perform better than a Windows version running in Wine.

---

### Post by ilikeroflcopters on 2008-08-02
> **aoanla said:**
> It's very difficult to answer this question without you actually telling us something about your computer!

Steam *does* take a while to launch some games, but you shouldn't be having performance issues with the games themselves.

Can you tell us what your processor and graphics card are, what version of Ubuntu (and graphics drivers) you have installed, and what the result of typing

glxinfo | grep render

in a terminal is?

DEFCON, by the way, should have a linux-native client, which should perform better than a Windows version running in Wine.

Oh sorry ^^;;I havent done this much, so please forgive anything i mistake

Im running Ubuntu 8.04 Hardy. I have a Mobile Intel Pentium 4 3.06 Ghz(im running this on a laptop)with 1.2GB of ram.I have a GeForce FX Go5600 graphics card with the "NVIDIA accelerated graphics driver".I dont know if the driver is correct though, i just looked in System->Administration->Hardware Drivers

When i type "glxinfo | grep render" into a terminal i get 
" direct rendering: Yes
OpenGL renderer string: GeForce FX Go5600/AGP/SSE2"

---

### Post by aoanla on 2008-08-03
Hrm. It's not an utterly horrible graphics card (although, obviously, laptop graphics are never quite as good as desktop graphics cards from the same generation), so it might be possible to improve things for you.

The first thing you should try is upgrading your version of Wine. I suspect you're still using the default Hardy release of wine, which is 0.9.60 (I think). 
You can find instructions about how to start using a repository with newer release of Wine here: [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

You might also benefit from upgrading your nVidia drivers from the default ones shipped with Hardy. This is a little trickier, though, since you need to do stuff with the desktop rendering off - if you're not that confident, don't bother and see what a Wine upgrade does.

---

### Post by aoanla on 2008-08-03
Oh, also, you can use

[http://appdb.winehq.org/](http://appdb.winehq.org/) 

to look up particular games you want to play and see how well they work with different Wine releases (and if anyone has any tips on fixing common issues with them).

---

### Post by ilikeroflcopters on 2008-08-03
> **aoanla said:**
> Hrm. It's not an utterly horrible graphics card (although, obviously, laptop graphics are never quite as good as desktop graphics cards from the same generation), so it might be possible to improve things for you.

The first thing you should try is upgrading your version of Wine. I suspect you're still using the default Hardy release of wine, which is 0.9.60 (I think). 
You can find instructions about how to start using a repository with newer release of Wine here: [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

You might also benefit from upgrading your nVidia drivers from the default ones shipped with Hardy. This is a little trickier, though, since you need to do stuff with the desktop rendering off - if you're not that confident, don't bother and see what a Wine upgrade does.

I updated my repositories with the new ones from WineHQ and installed the new one, but it didnt help. Steam opens up fine, but after starting defcon, it just goes to a white striped like screen.I sreencaptured it

And at the Appdatabase, they have no solutions posted on their website, so right now im hoping that someone on the ubuntu forums has figured out a way, or is trying to figure out a way to make it work.Thanks for the link though

And when you say upgrading my NVIDIA drivers from the default ones, what do you mean?^^;;

---

### Post by ilikeroflcopters on 2008-08-03
Im moving this thread to the gaming and leisure forum. I installed the linux version of Defcon, and it also runs with a slow frame rate. So im led to believe it is not wine and the game Defcon itself

---

### Post by unca.paka on 2008-08-23
You could always get Envy, and let it install the most up to date driver for your video card.
drop this into a terminal
```
sudo apt-get install envyng-gtk
```

---

### Post by ilikeroflcopters on 2008-08-23
Thanks unca.paka!
Right after i installed envy and let it install the new driver, Defcon worked fine for me.

---

