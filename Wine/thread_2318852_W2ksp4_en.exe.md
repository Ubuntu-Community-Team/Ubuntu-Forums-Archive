---
title: "W2ksp4_en.exe"
date: 2016-03-29
forum: Wine
---

### Post by MJae on 2016-03-29
I've been trying to add wininet and winhttp but I've only been getting this error:

> sha1sum mismatch! Rename /home/mjae/.cache/winetricks/win2ksp4/W2KSP4_EN.EXE and try again.

I've done what it asks me to do and tried several times but I still get the error. Help me, please.

Thanks!

---

### Post by The_Woodpecker on 2016-04-11
Hey, if I'm not mistaken that file name sounds much like the Windows 2000 service pack 4 update. May I ask why you are trying to install this on Ubuntu?

---

### Post by MJae on 2016-04-30
I'm trying to install a game that doesn't have a Linux version. I looked around and said I should be installing those two items for the game to work. But, as I've mentioned, I only get that error.

---

### Post by diogovmm on 2016-07-29
I've got exacly the same problem for the same reasons.
I want to play heroes of the storm with wine/playonlinux but can't get past here. anyone know a solution?
I run Xubunto.

---

### Post by diogovmm on 2016-07-29
I've been trying to fix this for about 5 days now, I am about to explode...
my latest breakthrough was by finding out - [https://github.com/Winetricks/winetricks/issues/600](https://github.com/Winetricks/winetricks/issues/600) 
I've downloaded the executable, put it on /home/USER/.cache/winetricks/win2ksp4 and ran it, But here is what happens:
first, it asks to execute at Z:\home\USER\.cache\winetricks\win2ksp4 -->shouldn't be C : (I've tried both ways and get the same error anyway)
second, I after it extracts I get---- Service pack 4 Setup Error
                                                Setup cannot update your Windows files because the language installed on your system is different from the update language.

Now I can't find help on this from other posts, and don't understand what is the error to try fix it on my own...

ps-is it normal to have a lock icon on the executable when browsing the directory?

Please give me some feedback! Thank you.

---

