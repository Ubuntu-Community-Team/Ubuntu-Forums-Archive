---
title: "Does Wine Not Work in Ubuntu 18.04? How can I install Windows Software?"
date: 2019-03-12
forum: Wine
---

### Post by jjm00ey on 2019-03-12
So I've installed wine using the ubuntu software application, but it doesn't do anything if I click "launch" If I open up my "show applications" tab and type wine, nothing shows up.  Also, when trying to us playonlinux, it often says wine has crashed.  Is there any way around this, or a way to fix it?

---

### Post by ajgreeny on 2019-03-12
*Thread moved to **Wine**.* which is more appropriate and a better fit.

Unfortunately I have not used wine for many years so will have to leave you in the hands of others who have more knowledge than me.

---

### Post by jjm00ey on 2019-03-12
Thank you, I apologize for picking the wrong thread.  Hopefully someone can help soon.

---

### Post by monkeybrain20122 on 2019-03-13
There are two issues here. 1) wine .desktop files not showing up. 2) playonlinux not work
For 1) see my post #2  [https://ubuntuforums.org/showthread.php?t=2391933](https://ubuntuforums.org/showthread.php?t=2391933) mc4man's post #4 was the preferred solution but unfortunately that ppa doesn't exist any more.

For 2) Apparently there is no fix [https://ubuntuforums.org/showthread.php?t=2398938](https://ubuntuforums.org/showthread.php?t=2398938) . playonlinux is completely broken in Ubuntu 18.04. Works in 16.04 though. It happens in many newer distros too, you can check out [https://www.playonlinux.com/en/forum-72-PlayOnLinux.html](https://www.playonlinux.com/en/forum-72-PlayOnLinux.html) If you find a solution there, let us know. :)

---

### Post by kc1di on 2019-03-13
if you installed wine-stable from the repositories then you need to move wine.desktop file or make a link to it by entering the following in a terminal.
```
sudo ln -s /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/
``` then wine program loader will be available on the right click menu (you may have to go to open with another program, but it should be there)

you can also exicute and exe file with wine in the terminal by navigating to it and then entering the command like this ```
wine xxxx.exe
``` Where xxxx is the name of the program you want to install or run.  Good luck.

---

