---
title: "Backing up Wine Programs for Fresh Wine Install?"
date: 2008-11-22
forum: Wine
---

### Post by iheartubuntu on 2008-11-22
Im having a problem right now installing Photoshop CS2 on this computer, but didnt have such problems on my home computers. I would like to somehow backup all of my other WINE programs and copy them back into WINE after I uninstall and then reinstall WINE. Is this possible? Then, try installing PS-CS2 on a fresh version of WINE. Would be easy to do, but I have a bunch of other WINE software :/

---

### Post by iheartubuntu on 2008-11-22
bumpity bump bump!

Thanks!

---

### Post by iheartubuntu on 2008-11-24
Is it possible? thx

---

### Post by karth on 2008-11-24
According to my experience, it is possible.

I succesfully moved entire wine trees over my filesystem and used them right away (provided they were not corrupted themselves in any way in the first time)

Just back up the .wine/ directory (or whatever wine tree you are using for CS2) to some place, do what you have to do with the wine packages, and paste the backed up directory back in place. Or put it somewhere else and set WINEPREFIX accordingly.

---

