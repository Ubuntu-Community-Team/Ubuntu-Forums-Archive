---
title: "No steam directory in wine?"
date: 2008-08-29
forum: Wine
---

### Post by IOA on 2008-08-29
Well, I ended up screwing up Crossover so I switched back to Wine. I started up HL2DM on Steam and I went to go to edit my autoexec so that I could save stuff like a jumpduck script or whatever, and I found that there IS no directory for steam. I looked under /home/ioa/.wine, /home/ioa/.wine.0806221923/, and I did a system search for all other wine directories and I found none that had the Valve or Steam folder. After a few days of having this issue I started wondering how the hell Steam was able to start or how I could find out where it was located, but even after doing "Open c_drive" or whatever on wine nothing came up, and when I tried to find out where Steam was it wouldn't show anything. Does anyone know how I could find it other than searching things like hl2 and that stuff on my PC? Because no matter what I seem to do, I just can't find it. 

I'm on Ubuntu 7.10, any tips?

Thanks in advance.

-IOA

---

### Post by aoanla on 2008-08-30
Odd.

Why do you have two .wine directories? That sometimes suggests Wine is being odd about things.

In my Wine install, Steam is where you would expect:

~/.wine/drive_c/Program\ Files/Steam

---

### Post by IOA on 2008-08-30
Well, here's the directories of both wine folders:

[http://img184.imageshack.us/img184/8158/wine1yx0.png](http://img184.imageshack.us/img184/8158/wine1yx0.png) <-- /home/ioa/.wine

[http://img528.imageshack.us/img528/5504/wine2hf7.png](http://img528.imageshack.us/img528/5504/wine2hf7.png) <-- /home/ioa/.wine.0806221923/drive_c/Program Files

Yes, I looked in Dosdevices and those folders. Most of them brought me right back to that folder which caused all the directories to get weird...

---

### Post by IOA on 2008-08-31
I'll try reinstalling wine and I'll post back.

---

### Post by IOA on 2008-09-07
Well reinstalling didn't work...no one else is getting this problem?

---

### Post by Bios Element on 2008-09-08
Assuming you have a launch icon go to it, edit it and look for the launch command. It'll probably have an environment (env) prefix and that'll be the patch to your steam folder.

---

