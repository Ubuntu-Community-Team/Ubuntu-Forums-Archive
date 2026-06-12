---
title: "Open With Photoshop CS5 not working"
date: 2014-04-21
forum: Wine
---

### Post by DidierDrigbi on 2014-04-21
Hi there.
I am on the newest Ubuntu, **14.04 Thrusty Tahr.**
I installed **Photoshop CS5** using wine. I would like to launch some of the jpgs in Photoshop using the "open with" context menu. But, there comes problem.

I created desktop entry (in /usr/share/applications). Okay, Photoshop shows in app drawer but when i right-click on some image and tell it to open with photoshop, the program launches but says that it can't find the photo i want to open. Desktop entry looks like this:
**exec=wine "c:\\Programy\\W32\\P\\Adobe\\Adobe Photoshop CS5\\Photoshop.exe" %f**

How to make it work?

---

### Post by Mark Phelps on 2014-04-21
Adobe Photoshop C5 has only a Bronze rating in the WineHQ application compatibility database:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158")

This means it is all but useless because, if it installs and does nothing else, it can have a Bronze rating.  Anything less than a Gold rating, for something you use regularly and depend on, is a waste of your time trying to use in Wine.

---

### Post by DidierDrigbi on 2014-04-22
Well, actually it works great, and I can open photos using the program. The only problem occurrs, when I try to open it with PS from context menu. I think, that it is something wrong with desktop entry line I gave you in the first post. I tried also with **%u** at the end instead of **%f** but no go.

---

### Post by lorcastrand on 2014-04-25
I have the exact same problem!
But mine works, until I click anywhere on the screen, then it freezes.

---

### Post by DidierDrigbi on 2014-04-28
Okay, I solved this problem. Dekstop entry Exec line should look like this:

> Exec=wine "C:\\Program Files\\Adobe\\Adobe Photoshop CS5\\Photoshop.exe" **Z:%f [COLOR=Blue]%f[/COLOR]**

---

