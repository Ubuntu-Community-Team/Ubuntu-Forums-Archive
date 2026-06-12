---
title: "Can wine run mugen???"
date: 2007-09-08
forum: Wine
---

### Post by trinireddman on 2007-09-08
Hi everyone is there a way to run mugen/winmugen on wine?Anytime i try it says it can't find mugen.config but when I check its there.

Noob onboard trying to leave microsoft for LINUX...so please cater your responce accordingly.

---

### Post by luisromangz on 2007-09-08
How do you start the program?

Maybe you should try to start it with a terminal from the folder were the exe is sitting.

---

### Post by MaximB on 2007-09-08
I do remember that Mugen has a Native Linux client , maybe under different name.
google for it, I remember that I've found it once.

---

### Post by CarpKing on 2007-09-08
They have the Linux version here: [http://randomselect.i-xcell.com/](http://randomselect.i-xcell.com/)

---

### Post by trinireddman on 2007-09-09
Thanks CarpKing the linux version worked.I tried it a couple days ago and it didn't,now on your recommendition it does...I love this forum.By the way do you know how to add a launcher to the menu?When I add the launcher it doesn't run. 

Anyway thanks people...I'll add more questions tomorrow.

---

### Post by MonkeyBoy on 2007-09-09
> **trinireddman said:**
> Thanks CarpKing the linux version worked.I tried it a couple days ago and it didn't,now on your recommendition it does...I love this forum.By the way do you know how to add a launcher to the menu?When I add the launcher it doesn't run. 

Anyway thanks people...I'll add more questions tomorrow.

To make a launcher go to the mupen directory and create a document.  Name the document "launcher.sh" then open it with text editor and put in the following:
```
#! /bin/bash
cd downloads/mugen
./mugen
```
Change that second line depending on where you put your mugen directory.
Save this and then right click on it and go to properties then permissions.  Mark the "Execute" box and you're done.  Back at your desktop right click and choose "Create Launcher".  Make sure you point this at the launcher.sh you just made.  Download a nice icon if you want it to look pretty.  For a menu entry open a terminal window, type "alacarte", then do much the same as above but in the menu editor that apppears.

---

### Post by elalzu on 2009-08-10
Yes it can. I'm currently running high res mugen on "Wine", works perfectly. So far no probs. Just run winmugen.exe (open with wine windows program loader). It doesnt install so you have to do this everytime you open winmugen. Hope this helps!:)

---

### Post by argor on 2009-08-13
> **elalzu said:**
> Yes it can. I'm currently running high res mugen on "Wine", works perfectly. So far no probs. Just run winmugen.exe (open with wine windows program loader). It doesnt install so you have to do this everytime you open winmugen. Hope this helps!:)

just run Mupen64Plus [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

---

### Post by frodon on 2009-08-13
2 years old thread necromancing !

Thread closed

---

