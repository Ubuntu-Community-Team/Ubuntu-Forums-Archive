---
title: "Installing/Working Guildwars - Thread"
date: 2008-02-19
forum: Wine
---

### Post by xtek0 on 2008-02-19
Hey guys let this be the official GW thread running through wine, Heres my problem:

Installed the old wine version from add/remove packager pre-installed in ubuntu and everything worked except the text would disappear on and off, the quality was great! Perfect and running. Now i have the newest version 0.9.54 and it is very VERY choppy and laggy, and it does not run right. Any ideas on how to fix this?

My graphics card is a radeon 9600series!

---

### Post by Toffeeapple on 2008-02-19
Try what they say [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194")....

---

### Post by xtek0 on 2008-02-19
how would i install it on the fedora wine since I got counter-strike perfectly working on this wine?

---

### Post by xtek0 on 2008-02-19
anyone know how?

---

### Post by Toffeeapple on 2008-02-19
Fedora is just a different linux..

[http://fedoraproject.org/](http://fedoraproject.org/)

The test result bit in the link I gave earlier is showing what linux distribution the results were gotten on... If you look above Fedora 8 you will see 'distribution'

To get GW to run a bit better set wine to windows 98 and turn some of the in game detail down.

---

### Post by xtek0 on 2008-02-19
Yea if i use fedora then i cant use ubuntu =[

---

### Post by xtek0 on 2008-02-19
Sorry for double post, well this PC i am running now already has been setup and been using on a daily basis. I am looking for this ubuntu to play some mmorpg especially guildwars, I have counterstrike working but without sound =[ !

Which linux OS is better for gaming?

---

### Post by xtek0 on 2008-02-19
Also just another thing I know im asking alot of questions but it is better to ask questions and help other people as well! When I have Guildwars running on my ubuntu everything is fine except in login I can use the keyboard to type my account info...One time I successfully got in the game except graphics were weird the textures looked like white clay etc.

But back to the keyboard it worked then next time instead of typing it in the box for the username it started typing on this box on the bottom, Im not sure i can pull it up again so Im sorry for the no screenshot!

---

### Post by xtek0 on 2008-02-20
**Update:** Fixed my problems for keyboard was just screwing around with the config, Alright now heres the part... This may be my graphics card i have no clue.
Ok when i first get into the game it works great and about 2 minutes in or whenever i click around on the menus or teleport the text is all messed up in menus. Also the graphics turn a off white color (trees, plants, etc.)

any ideas?

---

### Post by Ferrat on 2008-02-20
In a way it's your grafic card yes, it's ATi, somewhere around 0.9.45 I think it was Stefan Dösinger (one of the devs at WINE, the one working mostly on D3D) changed a lot of code for the better, the results are much more accurate and give better preformance, there was one problem tho, some games that had been working due to a glitch more than anything started showing grafic errors like 3d models not rendering, text looking good a few sec only to get jumbled and so on. 
I made a bug report about this and more people said they had noticed it, turns out every singel one of them had one thing in common, ATi cards :/ 
There is something in the fglrx drivers that doesn't like one of the updates and sofar it's not fixed sine the problem is on the driver side and not in wine itself :/

You can try editing regedit, it's not really a nice work around but worked for me when I played GW on my old ATi card
HKEY>>Software>>Wine>>Direct3D
DisabledExtensions = GL_ARB_draw_buffers

this should pop up models for you (case sensitive)

---

### Post by karth on 2008-02-20
As for Guild Wars, a little search wouldn't have harmed, since there is already a "Guild Wars under Wine" thread. It's a fair amount of reading, but it's quite complete and most of the problems are covered.

[http://ubuntuforums.org/showthread.php?t=283122](http://ubuntuforums.org/showthread.php?t=283122)

It may seem outdated (it's entitled "... Wine 0.9.23"), but it's not, the latest versions of wine are covered in the last pages.

---

### Post by xtek0 on 2008-02-20
Update: Fixed my problems for keyboard was just screwing around with the config, Alright now heres the part... This may be my graphics card i have no clue.
Ok when i first get into the game it works great and about 2 minutes in or whenever i click around on the menus or teleport the text is all messed up in menus. Also the graphics turn a off white color (trees, plants, etc.)

any ideas?

Running: Wine 0.9.54

---

### Post by Ferrat on 2008-02-20
> **xtek0 said:**
> Update: Fixed my problems for keyboard was just screwing around with the config, Alright now heres the part... This may be my graphics card i have no clue.
Ok when i first get into the game it works great and about 2 minutes in or whenever i click around on the menus or teleport the text is all messed up in menus. Also the graphics turn a off white color (trees, plants, etc.)

any ideas?

Running: Wine 0.9.54

If you have a ATi card you didn't read the thread ...

---

### Post by karth on 2008-02-20
> **xtek0 said:**
> My graphics card is a radeon 9600series!

> If you have a ATi card you didn't read the thread ...

Indeed... :p

---

