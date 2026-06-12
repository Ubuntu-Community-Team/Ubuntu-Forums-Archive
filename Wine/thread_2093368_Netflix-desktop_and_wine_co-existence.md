---
title: "Netflix-desktop and wine co-existence?"
date: 2012-12-10
forum: Wine
---

### Post by schwim on 2012-12-10
Hi there everyone!

I installed 12.04 32 bit to test Steam and would like to move the other things I use this computer for to this OS, so I don't have to dual-boot too much.  One item is Netflix and the other is WoW.

I installed Netflix-desktop and realize it's a "specialized" wine install, but don't understand if I'm ok to install standard wine for WoW without messing Netflix up or whether I should try to install WoW in the Netflix app's version of Wine?

Searching wine in unity doesn't bring up a result, so I thought I'd ask before messing something up.

Thanks for your time!

---

### Post by schwim on 2012-12-10
It seems they will coexist without issue. Thanks for all your help!

---

### Post by regor210 on 2012-12-11
I picked up netflix-desktop from this PPA

[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

Installing netflix-desktop places a new copy of wine called wine-compholio in your root opt file so the wine you use for everything else is not modified.

Its important to note “You can exit out of the app completely by pressing ALT+F4. You can also press F11 to exit out of full screen mode. “

If it stops working after an update just restart your computer then restart netflix-desktop and it should work.

Another thread.
[http://ubuntuforums.org/showthread.php?t=2086331](http://ubuntuforums.org/showthread.php?t=2086331)

---

