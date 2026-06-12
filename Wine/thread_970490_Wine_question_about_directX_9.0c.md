---
title: "Wine question about directX 9.0c"
date: 2008-11-04
forum: Wine
---

### Post by Faith912 on 2008-11-04
I was watching on the internet for wine and suddenly i saw this :lolflag:
[http://www.linux-gamers.net/modules/news/article.php?storyid=2334](http://www.linux-gamers.net/modules/news/article.php?storyid=2334)

wine doesnt have directx installed for default? because i can run the game without problem... 

after that i installed directx runtime with winedoors but i-m not sure of what i've done :lolflag:

plz tell me if i must install directx for running game on wine or not...

thx to all of you and sry for my english :p

I'm using ubuntu intrepid 8.10 and wine 1.1.5 (because 1.1.6 and 7 sux)

---

### Post by Magnes on 2008-11-04
Aside from DirectX 9.0c there are some additional small DirectX libraries (they have numbers in their names) that may be needed for some games to work on WINE. But WINE provides most of them (not the newer ones I suppose).

And you don't have to install the whole DirectX because WINE can't use it anyway.

WINE has it's own implementation of DirectX (using OpenGL) which "emulates" DirectX9.0c.

---

### Post by cogadh on 2008-11-04
The only thing you gain by installing DX as described in that article is a working version of DXDiag (which is fairly useless in Wine). As Magnes mentioned, you can get any needed functionality by simply copying the d3dx9_##.dll and d3dx10_##.dll files from an existing Windows installation into your .wine directory.

---

### Post by Ameneon on 2008-11-04
That brings me up another question that might be answered elsewhere but anyway; is there any performance benefit to copying over said dll's or is it merely in order to get a certain application to work at all?

---

### Post by cogadh on 2008-11-04
It really depends on the game. Some may need those files just to run properly, others may be able to work without them, but will work better if you do have them.

---

### Post by Faith912 on 2008-11-05
i had to copy d3dx9_27.dll for running oblivion, tha'ts why i tought that directX it's usefull to install but thx for your help.

Ehm someone know how does DirectX 10 work on wine 1.1.7??

---

### Post by oedipuss on 2008-11-05
There's no working dx10 yet, I think, but it's being developped. 

As for installing directx9, there were some guides on how to do so, with mixed results. Some games seemed to work better with a partially native (windows) directx installation. 

In any case, it's not as simple as running the default directX installer, which in fact may even damage your wine installation. 
Use winetricks, or follow a guide on how to install dx9 in wine, and do it in a different prefix ( =the fake windows environment wine uses, usually at /home/XXXX/.wine) It's not too complicated, just google 'wineprefixcreate' and 'wineprefix' for some info. Basically, you can then choose from which 'wine' you wish to run something by adding 
'WINEPREFIX=/home/XXXX/.mywinewithdx9' (where .mywinewithdx9 would be your new prefix) 
before any wine or winecfg command.

---

