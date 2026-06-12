---
title: "Multidisc install problems"
date: 2008-03-31
forum: Wine
---

### Post by coolkid5 on 2008-03-31
I'm having a problem installing Escape From Monkey Island, it is my first wine install so perhaps I am doing something incorrectly.

I pop in the disc 1 (there are 2) and navigate to it in the terminal, and then do "wine Monkey.exe".  This starts the installer and I do all the normal accepting license agreements and such, and select standard install.  It begins fine and it gets to 53% and the installer says, "Please insert disc 2 and hit 'ok' to continue or 'cancel' to exit installation".  I open a new terminal and use "wine eject" and then close the terminal and insert my new disc.  When Ubuntu recognizes the new disc (iit shows up on the desktop and I can see the files on it) I hit ok on the install window... the problem is that when I hit ok the box goes away and then comes back.  Nothing happens, I don't know what would cause this because Ubuntu has recognized the disc.

I have the latest version of wine ( 0.9.58 ) and AppDB says that Monkey Island works.  Any help would be very appreciated!

---

### Post by happyhamster on 2008-03-31
- Try running the installer from somewhere else then the cd itself. In other words, assuming your cd is mounted at /media/cdrom0, run:

wine /media/cdrom0/Monkey.exe

- from your home dir, instead of

wine Monkey.exe

- from the cd's mount point. Also make sure there are no other things looking at the disc (other terminals or filebrowsers etc.).

---

### Post by coolkid5 on 2008-03-31
Thank you!  That was my problem, I just needed to use "wine /media/cdrom0/Monkey.exe".  I knew it had to be something simple like that :)

---

### Post by happyhamster on 2008-03-31
You're welcome :)

BTW, running installers that way  is the exception to the rule: normally you *do* have to run wine from within a game's folder (because windows programs expect to be run that way).

A lot more info on running wine can be found in cogadh's thread:
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

---

