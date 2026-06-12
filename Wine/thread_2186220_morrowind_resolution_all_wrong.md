---
title: "morrowind resolution all wrong"
date: 2013-11-06
forum: Wine
---

### Post by cramshaw227 on 2013-11-06
[ATTACH=CONFIG]247614[/ATTACH]

I installed morrowind via wine1.6, it seems to big for the the screen maybe a resolution problem. Any ideas?

---

### Post by King Dude on 2013-11-06
Not one clue... but I think this might strike your fancy. 

[https://openmw.org/en/](https://openmw.org/en/)

---

### Post by howefield on 2013-11-06
Thread moved to the "*Wine*" forum.

---

### Post by cramshaw227 on 2013-11-06
> **King Dude said:**
> Not one clue... but I think this might strike your fancy. 

[https://openmw.org/en/](https://openmw.org/en/)

nice thx but imagine what this is like...

[http://www.nonfictiongaming.com/wp-content/uploads/2013/08/Grazlands-3.jpg](http://www.nonfictiongaming.com/wp-content/uploads/2013/08/Grazlands-3.jpg)

---

### Post by cramshaw227 on 2013-11-06
I figured how to get it working for me, this is what i did for future reference:

**sudo add-apt-repository ppa:ubuntu-wine/ppa** 

 **sudo apt-get update** 
 **sudo apt-get install wine1.6** 

 [B]sudo apt-get install winetricks

open up winetricks and [/B][B]*select the default wineprefix,* press *OK* and then [I]Install a Windows DLL or component -
[/I][/B]
[B]- everything beginning with “d3dx” 
 - quartz 
 - vcrun2005, vcrun2008, and vcrun2010 
 - wininet 
 - xact, xact_jun2010, and xinput 


[/B]
then i clicked the morrowindlauncher.exe changed to windowed mode via options and the game just ran.

(I HAVE NOT FULLY TESTED IT YET)

[http://i.imgur.com/0O1uwfG.png](http://i.imgur.com/0O1uwfG.png)

---

