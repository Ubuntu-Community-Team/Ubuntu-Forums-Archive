---
title: "Automatic Installer and making ANY program portable"
date: 2008-09-23
forum: Wine
---

### Post by david_kt on 2008-09-23
I have made a script to install windows program automatically, including downloading the program, downloading required dll and the needed wine tweak. For this case, the installer I make is to install e-Sword.

I think installer is very good for beginners that just wanted to have their program running and do not want to learn wine.

So, may be you guys could help those people by making installer for whatever programs of games you are good at, and other people just need to run your installer if they want to install your program in wine.

I have even make a script to make e-Sword portable. Theoretically, you could make any windows program running in wine portable using the concept on those script.

So, if you want to install e-Sword, make portable e-Sword, or you want to make installer for other program/games, you could examine my script and adjust it to your need.

Please see below:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

And if you find a better way of doing it, please let me know so that I could improve those scripts.

DK

---

### Post by Thelasko on 2008-09-24
> **david_kt said:**
> I have made a script to install windows program automatically, including downloading the program, downloading required dll and the needed wine tweak. For this case, the installer I make is to install e-Sword.

[Wine-Doors]("http://en.wikipedia.org/wiki/Wine-Doors") does something similar.  You should get involved.

---

### Post by binbash on 2008-09-25
> **Thelasko said:**
> [Wine-Doors]("http://en.wikipedia.org/wiki/Wine-Doors") does something similar.  You should get involved.

Isn't wine-doors broken?

---

### Post by david_kt on 2008-09-25
> **binbash said:**
> Isn't wine-doors broken?

To join wine-doors is too difficult for me, I just checked the source code of wine-doors and it is too complicated. I am no programmer.

I have made installer for e-Sword after reading winetricks codes. In my opinion, collection of installer is easier to manage, understand and maintain as compared to one installer for everything (which is wine-doors trying to do).

What I suggest is a simple installer like winetricks, easy to understand. If people reading my installer codes slowly, I believe they could do the same i.e. to convert their manual instruction to installer.

DK

---

