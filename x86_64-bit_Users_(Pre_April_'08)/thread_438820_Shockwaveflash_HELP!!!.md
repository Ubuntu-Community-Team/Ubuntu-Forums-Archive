---
title: "Shockwave/flash HELP!!!"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by gr1Mo on 2007-05-10
asdas

---

### Post by Kobalt on 2007-05-10
For your resolution : 
Open up the Terminal and enter ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the spacebar then validate with Enter. Finally, press Ctrl+Alt+Backspace to restart X, and here you go.

For your flash problem : 
there is currently no flash plugin made by adobe for x86_64 architectures on Linux. But there is a way of having this working though : [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

For your codec problem : 
I advise you to set up the Medibuntu repositories in order to have this all, see the Medibuntu section of this guide : [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

PS: I also recommend not using Automatix, with the Medibuntu repos and since Universe & Multiverse repos are now default enabled as of Feisty, Automatix is simply useless, you can get all it does from the Add/Remove menu.

---

### Post by kuja on 2007-05-10
Flash isn't a problem, flash is pretty easy to take care of. Shockwave on the other hand isn't available for Linux at all. I've heard you may be able to get it to work by running the windows version of a browser + shockwave in wine, but I'm not sure how well that works.

---

### Post by gr1Mo on 2007-05-11
Alright, Thanks guys great help. Much appreciated.

---

### Post by gr1Mo on 2007-05-28
adsad

---

### Post by morghi76 on 2007-05-28
the "sudo" word stands for SuperUserDO... therefore the system asks you for the SU passwords, which happens to be your same password, as you are the SU...
Hope it helps

---

### Post by gr1Mo on 2007-05-30
Is it sudo dpkg-reconfigure -phigh xserver-xorg for the 32 bit x86 version of fiesty aswell? I paste it in the terminal and it asks for the pass and i hit enter, because i cant type in there when it asks for the pass. Nothing happens.

---

### Post by kuja on 2007-05-30
gr1Mo, like pretty much all password inputs in the console in linux, as you type it nothing will appear, it's supposed to be some sort of security feature but misleads a lot of new users. You'll just have to trust that you're typing the password correctly and then press enter.

---

### Post by boogachamp on 2007-05-30
it really is asking for the passowrd, you just can't see what you type.  Type it in carefully and press enter.

---

