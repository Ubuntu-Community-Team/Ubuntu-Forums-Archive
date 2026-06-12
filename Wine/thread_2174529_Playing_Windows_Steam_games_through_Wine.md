---
title: "Playing Windows Steam games through Wine"
date: 2013-09-15
forum: Wine
---

### Post by stretch2 on 2013-09-15
Hello,

I am currently trying to get my Steam games (That I purchased through the Windows version) to work on Linux.

I installed Steam.exe using Wine, and everything works well, allows me to download my games and everything ... 

My problems started when trying to load the games.

GTA IV wont load at all, not giving any errors ...

GTA San Andreas changes the resoluton to 800x600 and then does nothing else, non splash screen or anything

Ragnarok online 2 loads the client, and then when I click 'Play' it comes with an empty error box, only allowing me to click 'OK

Is there anything I can do to get these to work?

Many thanks,
Chris :D

---

### Post by DarkAmbient on 2013-09-15
How did you install Steam, what else did you install?

You can use winetricks to install other components in your wine-environment. Such as directX9 etc...

```
winetricks
```

---

### Post by grentthevampire on 2013-09-15
Certain games doesnt just outright work after installing wine you should consider heading out to their forums and check for what they do for those certain scenarios 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780) heres a link to the GTA:San Andreas WINE thread

---

### Post by mJayk on 2013-09-17
I would really recommend using playonlinux for this.

---

