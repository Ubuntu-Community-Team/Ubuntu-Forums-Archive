---
title: "WINE updates"
date: 2007-08-15
forum: Wine
---

### Post by Jordan777 on 2007-08-15
Hi I have been running on Ubuntu and periodically WINE updates to the next version.  I was wondering if I should keep updating it.  I notice some things go gold or platinum on a previous version but I need to know if updating might cause the game or program to not work because the new version might mess something up.  Any help is appreciated.  I won't be home for several hours so I'll come back to this later.

---

### Post by onestep on 2007-08-15
I run 2 "must have" windows programs with Wine on Feisty. Last Friday I added the WineHQ APT Repository to my source list and upgraded to the latest version. One of my 2 windows programs stopped running properly!

I removed the WineHQ repository and installed the older version from Ubuntu. Still the program would not run! I started to panic!! 

Long story short, I ended up completely removing Wine and my 2 windows programs. Then I did a clean reinstall.  Everything now works fine!

YMMV

---

### Post by cogadh on 2007-08-15
Wine updates usually only include fixes and improvements, however, occasionally those updates can either introduce new problems or bring back old ones (regressions). By consistently updating you are guaranteeing that you will have the most complete Windows app support possible, but you also run the small risk of getting a buggy update occasionally. Generally speaking, if a game or app used to work with an old version of Wine, then it will likely work as good, if not better, with the newer version. If you do get a buggy update, it is very easy to uninstall it and reinstall a previous version.

---

### Post by Jordan777 on 2007-08-15
Oh ok then.  I understand.  Thanks for your replies.

---

### Post by Sammi on 2007-08-16
If a new version gives you troubles, then you can always find the old version here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

And remember that the Wine releases are not tested for bugs - at all!

They are simply snapshots taken every two weeks of the current alpha development build, that are packaged for easy installation. Wine is simply not ready for a "stable" release yet, that's why it's done this way. But it still works fine for many things.

---

