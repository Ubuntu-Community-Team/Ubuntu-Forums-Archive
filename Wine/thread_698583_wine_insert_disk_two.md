---
title: "wine insert disk two"
date: 2008-02-16
forum: Wine
---

### Post by strang3r on 2008-02-16
im trying to instal a game on wine, however it requires a second disk and it won't eject the disk. Here is what i have tried:
*ejecting via terminal (says its busy)
*dragging all files to desktop (no dice)
*asking nicely (negotiations have no effect :p)
*all on one disk (same story says its busy)

---

### Post by strang3r on 2008-02-16
help!

---

### Post by happyhamster on 2008-02-16
- Make sure you're not "on" the disc when trying to install: close all filebrowser windows looking at it for example. Also, don't run the setup.exe from within the disc's mount point, run:

wine /media/cdrom0/setup.exe

- from somewhere else (your home dir or such). (I'm just assuming /media/cdrom0 is the drive's mount point. You can check with the "mount" command.)
- When ejecting, use one of the the commands:

wine eject
wine eject d:
wine eject -a

- Another try is running:

winecfg

- and checking the Drives tab, to see if the drives are mapped correctly. 

- If it still doesn't work, could you give the wine version you're using, and the application you're trying to install?

> **strang3r said:**
> 
*asking nicely (negotiations have no effect :p)
:lolflag:


[edit: dang! you beat me to it :) So, what did you do to get it working?]

---

### Post by strang3r on 2008-02-16
no i didnt i ll try your idea

---

### Post by julian67 on 2008-02-16
cd tray is locked by default when in use. To change the default to always unlocked: ```
sudo echo "dev.cdrom.lock=0" >> /etc/sysctl.conf
``` and restart the computer.

When you finish making the wine install you might want to comment out the change again in /etc/sysctl.conf to return to the default of a locked CD tray when in use....so you don't inadvertently ruin a burn by ejecting.

---

### Post by strang3r on 2008-02-16
YEAH BABY! IT WORKED!!!!! 
now i gotta know how to make a thank you post.

---

### Post by FrozenFox on 2008-02-16
> **strang3r said:**
> YEAH BABY! IT WORKED!!!!! 
now i gotta know how to make a thank you post.

There's a little star symbol with a ribbon that's like a medal next to the quote button at the bottom of each post if you're logged in, if that's what you mean.

---

