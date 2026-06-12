---
title: "Help with Warcraft III and opengl"
date: 2008-03-02
forum: Wine
---

### Post by jprebechi on 2008-03-02
Hi ubuntu community :)

I was wondering if there was some kind of way to create a shortcut to warcraft opening with -opengl, since right now i have to open it from the terminal and it takes some time..

is it possible to get a shortcut which automatically opens in -opengl mode? so i can get it on my desktop and have easy access :)

I'm using wine to emulate windows, and i need to open the archive w3l.exe on opengl mode.

Thanks in advance :D

jprebechi.-

---

### Post by FrozenFox on 2008-03-02
Sure. There are several ways to do so. 

1st way) Right click on the desktop, create link to application. Under the command section, put in the same one you do for wine.

2nd way) The more useful way for, if in the future you want to run multiple commands by double clicking 1 shortcut or typing in 1 shortcut,

Open your favorite text editor, and type:

#!/bin/bash
wine /the/path/to/your/wc3/folder/wc3.exe -opengl (the command you normally run)

save it to the desktop, right click it, go to properties, and under one of the tabs is "make executable" or something of the sort. then just click it, youre good to go.

This makes a script that will run commands in the bash shell. in this case, only 1 command.

---

### Post by jprebechi on 2008-03-02
Thx so much!

Actually, i had to make a little change, since that command gave me an error (couldn't launch loader or something like that).

but then i wrote in the file
"cd /directory_with_warcraft
wine w3l.exe -opengl"

and finally worked :D

Thanks, once again ^^.

now i'd like to know if i could minimize warcraft, since i can't when emulating w/ wine... anyway, it's a minor problem.

jprebechi.-

---

### Post by FrozenFox on 2008-03-03
You can do something similar to what you want with xlaunch.

[http://ubuntuforums.org/showthread.php?t=690305&highlight=xlaunch](http://ubuntuforums.org/showthread.php?t=690305&highlight=xlaunch)

Please see my reply to this guy's thread for info.

---

### Post by jprebechi on 2008-03-03
i just followed that guide, and when i try to open, the screen turns black and then this happens in my terminal (and w3 isn't open in any X server)

juan@juan-desktop:~/Escritorio$ xlaunch /usr/bin/w3
Starting /usr/bin/w3 on DISPLAY 1
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 

juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 

juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 
juan@juan-desktop:~/Escritorio$ 

same thing happens with xlaunch w3, however, xlaunch gedit for example, opens without any difficulty text editor in another X server.

Anyway, yesterday i was trying some solutions to play in another X server, and i got some error.. maybe i screwed up =(.

i'll post later if i get the solution/found the problems

Thx a lot anyway

jprebechi.-

---

### Post by FrozenFox on 2008-03-03
Hrmmm. Apologies, I suppose I should have reinstalled wc3 and tested it out before I told you to go try something. I just assumed it would work, because every other program/game i've ever tried on it works just fine with xlaunch. Very strange indeed, I just tried it and it didn't work for wc3 (but still works for every other game i have, granted they are all native linux ones). Post if you figure something out, as will I.

.. I just tested this on several other programs in wine and it works just fine. How very strange.. what in the world is so special about wc3 that it's the only thing i've ever seen that doesnt work? lol. Must be the orcs.

---

