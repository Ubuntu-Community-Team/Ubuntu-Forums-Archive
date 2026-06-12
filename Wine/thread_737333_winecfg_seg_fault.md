---
title: "winecfg seg fault"
date: 2008-03-27
forum: Wine
---

### Post by Nythain on 2008-03-27
so this is a first... i cant install wine... i mean, i can install it, just cant config it...

first, im running 64bit gutsy (wich i've installed wine on before)
second, dont tell me to wine /path/to/whatever.exe because well, i cant very well run a program that i cant install because i dont have a flippin wine directory
third, wine version is 9.58 or whatever gotten from the wine repo for gutsy

now for the problem... im all to familiar with installing and setting up wine, i've done it a billion times, but for some reason, when i type winecfg in the terminal this is what i get
```

wine: creating configuration directory '/home/rune/.wine'...
Could not load Mozilla. HTML rendering will be disabled.
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/rune/.wine'.

```

i've googled the "Could not load Mozilla." problem, and everyone says put a certain .cab file into my windows installation in the wine folder... well guess what...

there is no wine folder or windows installation, because it wont make it, aparently because of this problem :P

any help would be great
thanks a lot

---

### Post by Nythain on 2008-03-27
Ok, so after a day of googling, i finally found my problem, it wasnt teh mozilla issue, it was a driver issue... for anyone else having a wine segfault issue, try re-installing your video drivers...

chances are you are running a nvidia card and chances are you installed more current drivers manually... and chances are this will solve your problem

---

### Post by mc4man on 2008-03-28
the mozilla thing is somewhat irrelevant - it goes away when you install gecko - simply  installing steam takes care of that vs. windows .cab thing

---

### Post by Nythain on 2008-03-28
yeah, i initially didnt know that due to the nature of the output of the segfault and the totall lack of info, i originally thought it was having issues because of the mozilla deal...

turned out to be a lack of 32bit libraries, specifically dealing with the manually installed nvidia drivers, wich re-installing fixed :)

---

