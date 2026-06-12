---
title: "Xfire"
date: 2008-05-21
forum: Wine
---

### Post by Vrekk on 2008-05-21
Hey i am a big gamer and normally do it on windows. well i wanted to try it on Ubuntu so i dont have to restart and boot into windows so much.  Well i got the majority of the games working and well no i want to install xfire if at all possible.  Xfire is an INGAME instant messaging program and ALL of my friends have an accound on.     but i cant install, i am not at home and cant remeber the error but  i can post it in about 3-4 hours.

---

### Post by justin whitaker on 2008-05-21
> **Vrekk said:**
> Hey i am a big gamer and normally do it on windows. well i wanted to try it on Ubuntu so i dont have to restart and boot into windows so much.  Well i got the majority of the games working and well no i want to install xfire if at all possible.  Xfire is an INGAME instant messaging program and ALL of my friends have an accound on.     but i cant install, i am not at home and cant remeber the error but  i can post it in about 3-4 hours.

There is a pluging for GAIM (now Pidgin) that allowed you to use Xfire. I do not know if it still works.

---

### Post by U83RMENSCH on 2008-05-21
Pidgin doesnt alow you to use xfire. I've tried xfire under wine, it seem to work ok. not great, but i dont know if hte in game rendering worked, I dont remember trying that.

---

### Post by Vrekk on 2008-05-21
> **U83RMENSCH said:**
> Pidgin doesnt alow you to use xfire. I've tried xfire under wine, it seem to work ok. not great, but i dont know if hte in game rendering worked, I dont remember trying that.

ok so update. i was able to reinstall xfire and i can login now, but i cant see my friends username, i just looks like [][][][][][][][][] and i havent had a change to test in game yet, that sould come in about 15-30mintues

---

### Post by Sleaka J on 2008-05-21
There's a plugin for Pidgin called Gfire that logs into the Xfire IM system. I can confirm it works.

However, I don't believe it detects games (doesn't display friends playing or detect you playing).

Edit: (3 days later) It does display which games friends are playing and if you mouse over the friend it also shows the IP of the server they are playing on (if it's a multiplayer game). I still don't believe the Gfire plugin is able to detect you playing games though, but at least it allows you to chat with your friends from Xfire.

---

### Post by Poyntz on 2009-06-08
> **Vrekk said:**
> ok so update. i was able to reinstall xfire and i can login now, but i cant see my friends username, i just looks like [][][][][][][][][] and i havent had a change to test in game yet, that sould come in about 15-30mintues

Install allfonts using winetricks
```
cd <winetricks path>; sh winetricks allfonts
```

Hopefully this works. If it doesn't upgrade to the latest xfire on [http://www.xfire.com](http://www.xfire.com)

You'll be downloading a .msi file which you just need to run through wine and it should install.

Execute these commands through winetricks before running it:
sh winetricks comctl32
sh winetricks comctl32.ocx

If you're having trouble with the client crashing, try my tutorial here:
[http://ubuntuforums.org/showthread.php?t=1181645&highlight=xfire](http://ubuntuforums.org/showthread.php?t=1181645&highlight=xfire)
to bypass the crashes

---

