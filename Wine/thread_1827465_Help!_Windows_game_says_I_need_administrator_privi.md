---
title: "Help! Windows game says I need administrator privileges to play"
date: 2011-08-18
forum: Wine
---

### Post by sixela295 on 2011-08-18
I'm running 64bit Natty. I downloaded a copy of Beyond Good & Evil (from Gamer's Gate, if that means anything), and installed it using WINE emulator with compatibility layer. However, once I launched it I received an error message saying that I needed to install TAGES drivers, and that this requires an account with administrative privileges. My user account has full elevated privileges & is an administrator. Is this an ubuntu error, meaning I need to install a copy on the GUI for root, or is this something to do with virtual windows (must I tweak something within WINE or etc)? 
Thanks for any help, as this is my first attempt at playing a windows native game on ubuntu :)

---

### Post by davdo2004 on 2011-08-18
The main exe is infected with Tages DRM. Always check with wineHQ before trying tto install windows native games.  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22107)

---

### Post by Elfy on 2011-08-18
Thread moved to Wine.

---

### Post by Matt__ on 2011-08-18
> **davdo2004 said:**
> The main exe is _[COLOR=Lime]infected with Tages DRM[/COLOR]_. 
It's not correct to describe it as "infected" because as much as you may dislike it, this is a valid copy protect system put in place to prevent piracy, so you are just expressing a personal opinion in your statement (even if it's not yours :P ).

To the OP, on any system other than win7 you will get that admin required warning.
It's pretty unlikely you will be able to get the game to run, but here is the Tages website if you want to try...
[http://www.tagesprotection.com/main.htm](http://www.tagesprotection.com/main.htm)
like davdo said, you should really check on winehq before purchasing games to run on it.

there is an interesting article about how the tages process works...
[http://www.myce.com/article/Another-Tages-blunder-212/](http://www.myce.com/article/Another-Tages-blunder-212/)

you may also have some success if you can find and remove atjsgt.sys and linsgt.sys from within wine as these are the tages drivers.

---

