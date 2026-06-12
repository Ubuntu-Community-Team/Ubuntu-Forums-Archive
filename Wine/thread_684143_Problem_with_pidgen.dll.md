---
title: "Problem with pidgen.dll"
date: 2008-01-31
forum: Wine
---

### Post by mamasita on 2008-01-31
I am running wine 9.54 and am trying to install age of mythology.  I keep getting this error cannot load pidgen.dll.  What do I have to do to get this working correctly.  Thanks for you help.  I am really new to wine this is my very first app trying to learn something new.

---

### Post by happyhamster on 2008-01-31
You'll need to get a native windows file: mfc42.dll. Get it from a windows xp computer, or download it from somewhere (there are several sites available around the net).

Then you have to put that file into wine's system32 folder. To get there: open your home folder (Places-->Home Folder), then press ctrl-h to be able to see all hidden files and folders. There should be a .wine folder. Open it and search until you find the system32 folder. Put mfc42.dll into that folder.

Try to run the installer again. Good luck.

---

### Post by mamasita on 2008-01-31
Thanks I did that.  It loaded both disks.  When I tried to start the game it stays stuck in the begining.  Dosent go anyfurther.

---

### Post by happyhamster on 2008-01-31
Hmm, the installation went fine? At the end (I believe) of the installation procedure, MSXML4 Parser is installed also (required to run the game). You can check if it's installed, by running:

wine uninstaller

It will list all programs currently installed under wine. If you don't see MSXML4 Parser, then it could be because of this bug: [http://bugs.winehq.org/show_bug.cgi?id=11174](http://bugs.winehq.org/show_bug.cgi?id=11174)

Basically, wine 0.9.54 or wine 0.9.53 won't allow you to install some programs (perhaps the parser is one of them). Solution would be to use wine 0.9.52 (or older) instead.

You can find the older deb files here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

To get rid of the previous wine install:

sudo apt-get remove --purge wine

And manually delete or move the hidden .wine folder in your home dir.

Next, install wine 0.9.52 by double-clicking the deb file. Configure wine using the command:

winecfg

And redo the mfc42.dll thing, etc, etc. Good luck, and let us know how things went.

---

### Post by mamasita on 2008-02-12
Ok I moved down to wine 0.9.47 and now I get this. Unload the debugger and try again.

---

### Post by mamasita on 2008-02-12
This is what I get in the debugger.

---

### Post by happyhamster on 2008-02-12
> **mamasita said:**
> Ok I moved down to wine 0.9.47 and now I get this. Unload the debugger and try again.
That usually means you need to use a nocd crack.

---

### Post by mamasita on 2008-02-12
how do you do that?

---

