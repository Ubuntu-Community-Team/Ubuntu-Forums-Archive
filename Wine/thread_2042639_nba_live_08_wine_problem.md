---
title: "nba live 08 wine problem"
date: 2012-08-15
forum: Wine
---

### Post by viksanbg on 2012-08-15
Hello,

I`m trying to run NBA live 08 under my Ubuntu 10.04 and wine 1.4 version.

I install the game and after that everything works great.
[IMG]http://img201.imageshack.us/img201/4290/nba1t.png[/IMG]

But when I started to play a match a receive this error

[IMG]http://img716.imageshack.us/img716/6192/nba2g.png[/IMG]

I hope anyone can help me to solve this.

Regards

---

### Post by mastablasta on 2012-08-15
did you check the application database as advised in the error report??

---

### Post by viksanbg on 2012-08-15
According to this page
[http://appdb.winehq.org/objectManage...ation&iId=6779](http://appdb.winehq.org/objectManage...ation&iId=6779)

I can`t see this type of error. The only thing  is that they tested this game in a diffrent wine version. But I think this is not the problem.

---

### Post by anewguy on 2012-08-15
If you look at the terminal behind the message box, you'll see a unhandled page fault.  If this EXACT same game (I mean EXACT - same release, same patches, etc.) runs fine in Windows, it would indicate it has a problem running in Wine.  This may be a difference in dll's, etc..

---

### Post by oldos2er on 2012-08-15
Moved to Wine.

---

### Post by mastablasta on 2012-08-15
404 on appdb page. so i went there and checked arround a bit. it seems game had gold rating in older version of wine. 

no extra explanaiton...

have you tried play on linux? maybe they have some settings for the game. do you have winetricks installed?

---

### Post by anewguy on 2012-08-16
Another odd idea, but what the heck at this point:

when you installed wine, did you run wine config to set it up for the type of Windows, etc.?  Maybe there's an incompatibility between the Windows wine is set for (perhaps vista when it needs xp, etc.).  Just something to check.

---

