---
title: "Lubuntu - add new shortcut to main menu"
date: 2014-11-29
forum: Wine
---

### Post by marchello_lippi2 on 2014-11-29
Hi all, 

I'd like to add new shortcut to Start -> Wine -> Programs. 
Actually I created .desktop already, placed it in my home directory and it works fine. How do I add it to menu now?

How do I perform it? 

Lubuntu 14.04.1 LTS
Wine 1.7.31

---

### Post by ajgreeny on 2014-11-29
I am sure there is a package available for Lubuntu to enable you to edit the menu, though it may need a ppa repository.  I used it in the past and it was called lxmed.
[http://sourceforge.net/projects/lxmed/](http://sourceforge.net/projects/lxmed/)
See thread at [http://ubuntuforums.org/showthread.php?t=1857030](http://ubuntuforums.org/showthread.php?t=1857030)

---

### Post by vasa1 on 2014-11-29
> **ajgreeny said:**
> I am sure there is a package available for Lubuntu to enable you to edit the menu, though it may need a ppa repository.  I used it in the past and it was called lxmed.
[http://sourceforge.net/projects/lxmed/](http://sourceforge.net/projects/lxmed/)
See thread at [http://ubuntuforums.org/showthread.php?t=1857030](http://ubuntuforums.org/showthread.php?t=1857030)IIRC, lxmed needs java which is why I never tried it. What about MenuLibre? Of course, Wine comes with its own wrinkles. Again, I don't use Wine.

---

### Post by marchello_lippi2 on 2014-11-30
Ok, I installed MenuLibre, now how do I create new menu item properly? 

I created item, command is "/home/user1/.wine/drive_c/Program Files/program1/program1.exe"
working directory is "/home/user1/.wine/drive_c/Program Files/program1/"

But when I run it via Start -> Wine -> Programs -> Program1 then it doesn't work. 
How to do it properly? 
Thanks ahead.

---

### Post by Dennis N on 2014-11-30
> Actually I created .desktop already, placed it in my home directory and it works fine. How do I add it to menu now?

Copy this working .desktop file from your Desktop to **~/.local/share/applications**
It should then appear in the main Lubuntu menu.

---

### Post by marchello_lippi2 on 2014-11-30
This way does work for me via MenuLibre: 

/usr/bin/wine /home/ymarkiv/.wine/drive_c/Program\ Files/program1/program1.exe

Thanks to all.

---

