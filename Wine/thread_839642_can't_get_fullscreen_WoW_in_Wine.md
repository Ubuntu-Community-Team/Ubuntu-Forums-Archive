---
title: "can't get fullscreen WoW in Wine"
date: 2008-06-24
forum: Wine
---

### Post by alexnublet85 on 2008-06-24
Hi all,

To try and cut this as short as possible:

I'm trying to run WoW in Wine.

I have installed Wine and WoW according to the guide in community docs. I have also done the extra stuff in the config.wtf file

I can get into the world now after some tweaks and using a virtual desktop with it running fine essentially, but as soon as I even touch the window/try to resize/go fullscreen the graphics stop and it all falls apart. I ran it from the Terminal but nothing comes up when it gets stuck at this point. I have saved the text up to that point if it would help for people to see it, just let me know.

I have tried changing the screen size in winecfg which is fine, but as soon as I change it in config.wtf, it does the same lock at start up.

The specs:

Wine 1.0
Default Settings for Applications, using Windows XP
Graphics Card: Nvidia GeForce 4200i using the restricted driver through Ubuntu
```
glxinfo | grep rendering
direct rendering: Yes
```
Using Hardy Heron

I don't have any other applications to try in Wine, I don't know if it is a problem with a Wine itself or some graphics settings but I can't find any other threads on this. Let me know if I'm not looking hard enough!

Thanks :)

(by the way, I'm pretty new to Linux so any help will prob need to be explained quite obviously!)

---

