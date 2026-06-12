---
title: "TF2 Black Menu/Screen"
date: 2011-12-01
forum: Wine
---

### Post by kaosvarkas on 2011-12-01
Hey guys,

I am very new to linux based operating systems and I have attempted to install Team Fortress 2 using Wine on my system. I have gotten Steam setup working flawlessly on an emulated desktop. However, when I try to run Team Fortress 2, the opening menu screen is all black background and only the buttons are viewable. Also, I can get into a game but the screen is completely blacked out at that point. All sounds and everything else is perfect.

I am using Ubuntu 11.10 64 bit with a nvidia 9800gtx graphics card. I have the latest nvidia drivers installed. I have gone through tons of google searches and forum posts to try to find a solution to this and have come up empty. Does anyone know the solution to this problem? I've tried a lot of different launch options and nothing has changed it.

Thanks guys I appreciate it. :)

---

### Post by ergo-proxy on 2011-12-02
Check here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901)

---

### Post by dmwit on 2011-12-02
Since that website will likely change, but this forum post will probably come up near the top in Google for a long time, the solution suggested at winehq is to add

-nod3d9ex

to TF2's launch options. It works for me.

---

### Post by kaosvarkas on 2011-12-02
Thanks very much for the help guys. This has fixed my issue. Now all I need to do is figure out how to maximize performance so I get a better framerate. :P Appreciate it!

---

