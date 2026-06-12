---
title: "copy pasting WoW"
date: 2011-07-13
forum: Wine
---

### Post by patabet on 2011-07-13
hey 
I was wondering if i could juste copy paste wow from my windows PC to my linux and juste launch it using wine?
(i ususaly transfer wow from a pc to an other directly by copy pasting it; it works on windows)
(lost my wow CDs)
(new to ubuntu, and linux in general)
thanks

---

### Post by cwwilson721 on 2011-07-13
That, as a matter of fact, is the EASIEST way to get WoW running.

I have a [guide on here about installing Cataclysm]("http://ubuntuforums.org/showthread.php?t=1773985"). Follow it, EXCEPT for the "install" part. Just copy/paste your ENTIRE "World of Warcraft" folder into /home/<USERNAME>/.wine/drive_c/Program Files folder, then create a launcher with ```
/home/<USERNAME>/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```as the command.
NOTE: Assumes you use the default '.wine' folder. If not, change to appropriate name. And change <USERNAME> to YOUR username on your computer.
(Also, make sure to use the opengl switch, and run Wow.exe. Launcher.exe has issues right now)

If you follow the guide, install the correct drivers and don't use a Intel chip or older ATi/AMD (needs REAL 3d opengl support, so opensource ones don't do well), you'll be up/running in about 30 min (most of the time is spent copying the now HUGE (16-17GB) WoW folder.

Good luck!

---

