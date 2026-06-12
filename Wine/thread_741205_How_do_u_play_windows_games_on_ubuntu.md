---
title: "How do u play windows games on ubuntu?"
date: 2008-03-31
forum: Wine
---

### Post by hollyn on 2008-03-31
How do u play windows games on Ubuntu??????????:confused:

---

### Post by edm1 on 2008-03-31
Unfortunately many game manufacturers dont see linux as a large enough market to produce games for. Wine may work for some games but they will not run as well as if they were native to linux.

---

### Post by gavintlgold on 2008-03-31
Come on Tim0miT, don't insult new users...

If you like Valve's Steam games like half-life 2, portal, team fortress, etc, you're in luck. They work perfectly in directx 8.1 mode.

Most of the games that work are listed in the "AppDB" on the wine website ^ up there.

Once you've gotten the latest wine installed, run something like:
> wine setup.exe
in a terminal changed to the directory of the .exe and try installing it. You might have to do a lot of tweaking to get it to work... look on the AppDB about that.

To change the basic wine settings, run
 > winecfg
Have fun, and good luck!

---

### Post by kaivalagi on 2008-03-31
I use Cedega rather than Wine, it's solely made for gaming, I run BF2142 in it okay(ish). I haven't tried using Wine for a bit, it's support for gaming has probably improved since I last installed it.

Also note a couple of windows games have installers for linux too, the following can be installed natively (hopefully the list will grow [-o< )

[LIST]
[*]UT2004
[*]Quake 2/3/4
[*]Enemy Territory : Quake Wars
[*]Wolfenstein
[/LIST]

Anyone know of any other games for windows that also have linux installers for them? Any non FPS type ones?

---

### Post by punkkid219 on 2008-03-31
Cadega works best for me with games

---

### Post by aomlives on 2008-04-03
I thought the new CrossOver was much better than Cedega?

---

### Post by kaivalagi on 2008-04-03
Has anyone tried using Crossover? Is it better than Cedega for games?

Both are based on Wine as far as I can tell, if so, are they really the same in performance or do they have special features that they benefit from?

I have read that Cedega is best for games and Cross is best for office for example, is this strictly true?

---

### Post by YokoZar on 2008-04-04
> **kaivalagi said:**
> Has anyone tried using Crossover? Is it better than Cedega for games?

Both are based on Wine as far as I can tell, if so, are they really the same in performance or do they have special features that they benefit from?The new Crossover Games has much more compatibility.  Crossover is based on the newer, free version of Wine, while Cedega is based on a 4 year old fork.

> I have read that Cedega is best for games and Cross is best for office for example, is this strictly true?No.  That's just the way Cedega tries to sell themselves.  In truth Wine often runs games better than Cedega, as well as every other application, all for free.  If you want a supported version that's been tested against a list of specific games, you can get Crossover Games.

---

### Post by kaivalagi on 2008-04-04
Thanks for the heads up YokoZar, I'll be checking out crossover soon :)

---

### Post by linuxisfree on 2008-04-07
> **Tim0miT said:**
> to gavintlgold

i wasn't that mean, just encouraging him to read about a bit first, thats all

cool?

actually it WAS kinda mean, and you didn't have to call the person a dumb ***.

---

### Post by Rathan on 2011-06-26
how can i play GTA Vice City Multiplayer in ubuntu. 

when i use WINE it worrks but when i coonect to server this shows from wine.



                              Program error
 
the program GTA VC.EXE  has encounterd a serious problem and needs to close we are sorry for incovenience .

this can be caused by a problem or a deficency in wineYou may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been reported yet you can repost it at [http://bugs.winehq.org](http://bugs.winehq.org).







    now waht sholud i do to work this application in Ubuntu 10.04

---

### Post by rickyLOLZ on 2011-06-27
Install Wine, then on any game .exe file,  (if right handed) right click on your mouse, then properties, then click permissions, then click on the little checkbox then OK and your done! Have fun! ;)

---

### Post by 10snoopy1 on 2011-06-27
> **Rathan said:**
> how can i play GTA Vice City Multiplayer in ubuntu. 

when i use WINE it worrks but when i coonect to server this shows from wine.



                              Program error
 
the program GTA VC.EXE  has encounterd a serious problem and needs to close we are sorry for incovenience .

this can be caused by a problem or a deficency in wineYou may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.

If this problem is not present under Windows and has not been reported yet you can repost it at [http://bugs.winehq.org](http://bugs.winehq.org).







    now waht sholud i do to work this application in Ubuntu 10.04


Which version of Wine are you using?

You may want to take a look at [this]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1369"):
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1369](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1369)

---

