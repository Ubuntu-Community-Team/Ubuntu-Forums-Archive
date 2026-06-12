---
title: "configuring wine"
date: 2012-08-03
forum: Wine
---

### Post by opfeld on 2012-08-03
I recently installed wine so I could install and play total war.  The problem is that I only have 15gb for my / and /home folders, I have a separate partition for everything else.  As a result there is not enough room for the game on my drive c:, according to wine.  I can't seem to find the option to install the game elsewhere, it only wants to allow me to do it to c:  can anyone tell me how to set it up so it downloads it elsewhere?

---

### Post by Dylan1473 on 2012-08-03
I've never tried this outside of a home directory so I'm not 100% certain it will work, but you can change the wineprefix (the folder Wine works from) with
```

export WINEPREFIX=~/.wine-new wine winecfg 
```Just replace ~/.wine-new with the directory you want (that one points to a hidden folder called .wine-new in your home directory). That's directly from _[Wine's FAQ here]("http://wiki.winehq.org/FAQ/#head-667c697ca3174cbbbfc9b5213e40885761d6a596")_ if you want some more info.

I'm not sure whether this would work outside your home directory or what consequences it might have. If you're just using a generic partition for storage or something I expect it'd work. One thing though: do *not* point Wine toward a Windows partition. Wine may or may not work this way, but Windows most definitely won't afterwards.

EDIT: Further reading of the FAQ indicates that it should in fact be possible to run Wine from a separate partition so long as it is a UNIX partition. You might examine the "My installer tells me I don't have enough free disk space" section.

---

### Post by 3Miro on 2012-08-03
You will have to use the terminal and write:
```
WINEPREFIX="/some/folder/" wine ....
```
This will tell wine to use another folder as opposed to the default /home/your_name/.wine.

---

### Post by oldos2er on 2012-08-03
Moved to Wine.

---

### Post by cwwilson721 on 2012-08-04
Well...

If the above doesn't work, you can always add a "D:" drive in winecfg, pointing to a folder wherever you want (for example: winegames on the other drive), then install whatever to it, if the game install lets you install to other drives than C:

I do that for a "common" WoW install, so I have just one install for all users. I just have to make sure the permissions are set. But if it's just one user, you won't have those issues.

This also has the benefit (for me) of keeping all my wine folders in my home directory. It is the '.wine' folders that have all the registries, etc.

---

