---
title: "World of Warcraft and Mangler"
date: 2011-11-11
forum: Wine
---

### Post by Digi984 on 2011-11-11
So after reading through the seemingly thousands of posts on WoW with wine, I am still left with no working answers..so I am hoping someone has some new information.

I am trying to install WoW with wine.  I have been using the client download from battle.net.  I can get it to install but whenever the launcher loads to download the new patch information(or to try to start the game) it crashes.  I am running Ubuntu 11.10 it use to work okay on 10.10 and 11.04 so I guess my first question is, should I revert to an earlier version of Ubuntu?  If not, what ways are there to solve the issue?

The other program I am having issue with is Mangler which is frustrating as it is linux native.  It installs fine but no matter the settings(I've tried em all) people can't hear me and I can't hear them.

Any suggestions on how to solve these issues would be greatly appreciated. 

Thanks.

---

### Post by Soulcage on 2011-11-12
For mangler you might need to check your mic levels by running alsamixer in a terminal.

For wow you might want to try running wow.exe instead of the launcher.exe, the launcher has had problems all along. (afaik)

---

### Post by Tweak42 on 2011-11-14
> **Digi984 said:**
> 
I am trying to install WoW with wine.  I have been using the client download from battle.net.  I can get it to install but whenever the launcher loads to download the new patch information(or to try to start the game) it crashes.  I am running Ubuntu 11.10 it use to work okay on 10.10 and 11.04 so I guess my first question is, should I revert to an earlier version of Ubuntu?  If not, what ways are there to solve the issue?


I had problems with the launcher crashing randomly while downloading the latest pre-patch.  After crash I just kept doing 'wineserver -k' and restarting the launcher till it eventually finished.  I have no evidence to substantiate but I suspect the wow news feed integration in the launcher and wines effort to render it don't get along thus causing random hangs/crashes.  The launcher is (often) broken launching the wow.exe so best to launch wow.exe directly with wine.

> **Digi984 said:**
>    
The other program I am having issue with is Mangler which is frustrating as it is linux native.  It installs fine but no matter the settings(I've tried em all) people can't hear me and I can't hear them.

Any suggestions on how to solve these issues would be greatly appreciated. 

Thanks.

Few things you can try:
Verify your mic is working using Sound Recorder.
Try different vent servers.  It's possible the one you are having trouble with is incompatible, old 2.x or using unsupported codec.
If you are using a analog headset, try a USB one or vice versa.

---

