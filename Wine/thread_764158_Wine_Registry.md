---
title: "Wine Registry"
date: 2008-04-23
forum: Wine
---

### Post by swordphsh on 2008-04-23
I have a certain program that i run in wine that removes the serial number from the registry file and deems itself "unregistered trial version." 

I created its own wine prefix directory called .wine2 in my home directory and installed the program to the wineprefix .wine2.

Here is where the problem comes in: If I set the 3 registry files in my .wine2 directory to read-only (chmod 444), the program stays registered because it cannot delete the registry key with the serial, but Wine seems to change the permissions of the files back to 744, rw,r,r, thus the program unregisters itself.

My question: Is there any way to make these three files read-only without Wine changing the permissions back to writable?

     Also, if I chown the files by root, Wine immediately changes them back to my user as the owner and chmod 744.

---

### Post by cogadh on 2008-04-23
Wine changes them back to read/write because Wine won't work if it can't write to the registry when it needs to. The Wine registry is treated just like the Windows registry; it cannot be read only.

---

### Post by swordphsh on 2008-04-24
I guess that makes sense...Does anyone have any other ideas though?

I know in the Windows registry certain keys can have restricted permissions such as allowing only the system account write-permissions, but I couldn't find anything relating to this in Wine's.

---

### Post by cogadh on 2008-04-24
What's the program? Maybe someone has already encountered this and put a solution up on Wine's Application Database:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by swordphsh on 2008-04-28
It's GetRight 6. It's not problem with Wine in particular, more of a problem with the program itself, in Windows and Wine.

---

