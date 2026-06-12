---
title: "[SOLVED] Halo"
date: 2007-12-21
forum: Wine
---

### Post by famous3warriors on 2007-12-21
I am new to Ubuntu and i am loving the experience.   I have halo that I was playing on my wont mention the word and now I would like to play it on Ubuntu? I have Ubuntu 7.10 i386  what software would I need to play the game and how to download it?  Thanks I really do appreciate your help in this matter.:lolflag:

---

### Post by TheIdiotThatIsMe on 2007-12-22
Howdy! For using any Windows programs in Ubuntu (or linux in general) you should familiarize yourself with Wine. Wine is an Windows compatible API that runs on top of Linux, to assist in running Windows programs inside Linux. However, it should be warned that Wine is *not* 100% compatible or a complete replacement.

For information on games or applications in Wine, always visit the [_Wine Application Database_]("http://appdb.winehq.org/")

Halo seems to have a Gold rating, so you might want to check [_there_]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1986") for ways to get Halo to work on Linux.

Hope this helps :)

---

### Post by famous3warriors on 2007-12-22
Thanks yeah  I was taking a look at you're post and I have to get wine 9.43 and for 7.10 the lowest it goes is 9.47 can I go further down to 9.43 on gutsy?  9.43 version of wine is for feisty i386.

---

### Post by famous3warriors on 2007-12-22
thanks I could not get it to work properly Thanks I really do appreciate your help.  i will try some other time.

---

### Post by pissedoffdude on 2007-12-22
> **famous3warriors said:**
> I am new to Ubuntu and i am loving the experience.   I have halo that I was playing on my wont mention the word and now I would like to play it on Ubuntu? I have Ubuntu 7.10 i386  what software would I need to play the game and how to download it?  Thanks I really do appreciate your help in this matter.:lolflag:

You'll have to use an old version of wine since the new ones have trouble with halo.  Get this deb and install it ```
http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.41~winehq0~ubuntu~7.04-1_i386.deb
```
Open up a terminal and type "winecfg" (no quotes) and make sure you have the alsa driver selected under audio.  Then head over to the graphics tab and emulate a virtual desktop size of 800x600
When installing halo it will report some errors, just ignore them.  After it's done installing do not click play now.  You must right click the halo icon on your desktop and under launcher>command add -novideo.  Halo should be up and running now.

---

