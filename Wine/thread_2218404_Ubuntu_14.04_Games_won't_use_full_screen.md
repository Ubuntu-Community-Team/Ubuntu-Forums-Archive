---
title: "Ubuntu 14.04: Games won't use full screen"
date: 2014-04-20
forum: Wine
---

### Post by martijntje on 2014-04-20
After upgrading my system to 14.04 this morning, WINE games won't run properly anymore. It flashes fullscreen for a millisecond, then gets redirected in what appears to be a window. The window start some pixels away from the top and left bar.If I move the mouse to the right or bottom corner the whole screen will move (like a virtual desktop that is bigger than the screen resolution).I do not have wine configured to use a virtual desktop. I have already tried to uncheck the option to let the window manager decorate WINE windows without avail. What can I do to resolve the issue?My system uses a nVidia card, I have tried both available proprietary versions.

---

### Post by adec2 on 2014-04-20
I used to have this problem too in Ubuntu but dont anymore using Kubuntu.
Some games were helped by setting the screen resolution using nvidia settings to your preferred resolution then using the same drop down box and selecting auto.
Some games required you to uncheck the "Allow the window manager to control the windows" option under the graphics tab in the wine configuration.
Also checking the legacy programs option in compiz config helped some
In the end it didnt solve all my problems, many games still did this and after pulling my hair out for ages over this problem it was all sorted out accidently by using Kubuntu
Maybe its something to do with the windows manager as Kubuntu uses a different one to Ubuntu

---

### Post by martijntje on 2014-04-21
Hmm, I tried using gnome, but the problem stays exactly the same. It wasn't a problem with Unity in earlier versions either. I have also tried the legacy fullscreen option without avail. What else could it be?

---

### Post by Sandgoose on 2014-04-25
is it with a specific game or all games? have you gone into the setup and told it to run in maximum resolution your monitor will take? I had an odd problem with a game not running fullscreen after some updates, the game config screen said it was set to run in 1920x1080 but it clearly was not. I ran winecfg told it to launch in a 800x600 virtual desktop and for some reason that made the game start in the window and then jump into fullscreen mode, got to love quirks of gaming in wine.

---

### Post by Mad-Halfling on 2014-05-15
I've also just started getting this problem, I think it was after an update, but I don't recall it being a WINE update.  Sometimes it works ok, but sometimes it doesn't. I've tried turning off and on "Allow the window manager to control the windows" but it doesn't make any difference.  This hits me on both ESO and WoW but winecfg always loads ok - it only seems to hit programs that actually run fullscreen

---

