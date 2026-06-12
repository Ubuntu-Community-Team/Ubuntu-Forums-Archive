---
title: "Feltstars, Lock (Merge) Poker Download.  HELP"
date: 2012-05-12
forum: Wine
---

### Post by Trevkidd on 2012-05-12
I am new to Ubuntu 12.04 and am having trouble playing online poker. 

I downloaded Feltstars and Lock Poker (windows version) using Wine.  When i open the icon it stars to load the program then stops.  No error or anything, just stops.  Also the main Picture is upside down.

Please help.  I don't want to go back to windows.

Thank you

Trever.

---

### Post by LemursDontExist on 2012-05-12
Unfortunately, I think Lock poker isn't going to run under wine.  Check out the [carbon poker entry]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6536") on the wine appdb.  It's a different skin, but all the skins on Merge use essentially identical software as far as I know.

I would recommend creating a virtual machine to run the poker client under.  Virtualbox, which is in the repos, is quite user friendly - you can find tons of tutorials for using it to setup a virtual windows machine you can use to play poker inside Ubuntu.

---

### Post by Trevkidd on 2012-05-14
Thank you for the Virtualbox idea.  I am using it for now.  I was hoping to get rid of windows.  Oh well will wait for the rest of the world to catch up.

---

### Post by thatguruguy on 2012-05-14
You may want to try pokerth available in the Ubuntu Software Center.  I play it from time to time, and it seems to have a pretty active community of players.

---

### Post by Trevkidd on 2012-05-14
I have it but it doesn't use real money, so it's just for fun.

---

### Post by thatguruguy on 2012-05-14
That's cool. Send me a thousand dollars, and we'll play heads up.

---

### Post by Trevkidd on 2012-05-18
> **thatguruguy said:**
> That's cool. Send me a thousand dollars, and we'll play heads up.
 
 
If i could play online poker through Ubuntu i would send you a grand. But I still can't play. :mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by LemursDontExist on 2012-05-18
The problem is that most poker clients include some very invasive anti-cheating features which make use the the windows API at a very low level.  Wine just doesn't support the API quite well enough to handle that sort of thing yet.

---

