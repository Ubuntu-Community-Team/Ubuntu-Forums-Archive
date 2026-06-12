---
title: "Play WarCraft 3 in ubuntu?"
date: 2008-09-13
forum: Wine
---

### Post by justinram22 on 2008-09-13
Hello, im 13 and kinda new to linux, and well.. i've been using ubuntu for about 8 months now, and know about half of the termainal commands... my question is, ever sense i switched from windows XP, i've been having the itch to play warcraft 3 again, i've tried using wine, but when i launch wc3 it flickers a couple of times, then it goes to a black screen, when i move to a different side of my cube with compiz all the icons are huge, and i just end up restarting ubuntu.... any help would be greatly appriciated, baby step instrutions would be the best, thanks!

---

### Post by Zzl1xndd on 2008-09-13
I have never tried Warcraft 3, but according to Cedega's site it runs perfectly. Cedega is a gaming specific version of Wine sold by transgaming.

[http://www.cedega.com/gamesdb/games/view.mhtml?game_id=2793](http://www.cedega.com/gamesdb/games/view.mhtml?game_id=2793)

---

### Post by justinram22 on 2008-09-13
Is there a free option? i wouldn't mind using wine, other than it don't work lol

---

### Post by Patrick793 on 2008-09-13
Try turning Compiz off and seeing how it runs.

---

### Post by Whiffle on 2008-09-13
Should work fine under wine, if you follow these instructions:
[http://frankscorner.org/index.php?p=warcraft3](http://frankscorner.org/index.php?p=warcraft3)

---

### Post by Oldsoldier2003 on 2008-09-13
Moved to the Wine subforum. Have you looked at the wineappdb to see if there are any specific tweaks or caveats? [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by Zzl1xndd on 2008-09-13
I have the installer files and update version 6.0.5, if you want I would be more then happy to give them to you. It is still open source software I might as well help someone else out.

---

### Post by PandaGoat on 2008-09-13
You got it to run fine.  The problem with the black screen does with the movies in warcraft III. Delete or rename the folder Warcraft III/Movies. Then restart Warcraft.

If you get low framerate run warcraft with -opengl at the very end.

Also if you host or use compiz, you really should get a wine patched for these since the newest version of wine implements something that screws with hosting and tab switching(with compiz running). Luckily though, my brother patches wine specifically for this and uploads it to his PPA repository; you can get information here: [http://ubuntuforums.org/showthread.php?t=803988](http://ubuntuforums.org/showthread.php?t=803988)

Moreover, once you update Warcraft, you will no longer need the CD to run it.  So don't do what Frank's Corner tells you to do, since you can obviously initially run it anyway, and Frank's Corner is outdated.

---

### Post by justinram22 on 2008-09-13
ok thanks to you all, i renamed my movies file to movies2 and it loads just fine, i had to use the "-opengl" command to get it not so laggy, but one question, is there a way to get it so it doesn't flash back to my desktop every half a second and than back to the game?

---

### Post by tklinge on 2008-09-15
To get it not to flash you have to turn off the extra desktop visual effects.

---

