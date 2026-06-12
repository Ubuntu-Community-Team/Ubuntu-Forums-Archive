---
title: "30 plus icons on desktop"
date: 2012-07-03
forum: Wine
---

### Post by benjie1 on 2012-07-03
I have Ubuntu v 12.04 and gnome desktop. Installed wine 1.5.7 no problem and then an old windows solitaire game called Hardwood Solitaire 3 .It's an .exe file and installed well and runs great. Problem is during the install (hwsoliii.exe) it put about 30 icons on the desktop. The game runs perfectly in spite of this. I removed the icons and then the icon that runs the game disappeared too. Re-installed, the game runs great but got the 30 icons again. Somehow in removing one or more of these icons it also removes the one needed to run the game. Hate to have to go one by one til I find the culprit. Newbie here. Thanks.  Bob   BTW, the exact same thing happens in openSuse v 12.1, and wine 1.5.7.

---

### Post by cbanakis on 2012-07-03
The installer could be a simple self-extracting zip file.

Was the installer on your desktop when you ran it?

If so, try moving the installer to another folder before you run it.

---

### Post by llamabr on 2012-07-03
> **cbanakis said:**
> ...try moving the installer to another folder before you run it.

Or, try removing Wine, and installing a native solitaire.  Wine is very rarely the correct solution.  It doesn't work very well.  It's not made to work very well, and there's usually a better solution.

```
brock@vader:~$ apt-cache search solitaire
ace-of-penguins - graphical solitaire-games with penguin-look
junior-games-card - Debian Jr. Card Games
freecell-solver-bin - Library for solving Freecell games
libfreecell-solver-dev - Library for solving Freecell games (Development files)
libfreecell-solver0 - Library for solving Freecell games
gnome-games - games for the GNOME desktop
jester - board game similar to Othello
kmahjongg - mahjongg solitaire game
kpat - solitaire card games
kshisen - Shisen-Sho solitaire game
mah-jong - The original Mah-Jong game
peg-e - peg elimination solitaire game
pegsolitaire - An education game similar to Hi-Q
sgt-puzzles - Simon Tatham's Portable Puzzle Collection - 1-player puzzle games
vdr-plugin-solitaire - Plugin to vdr that implements the card game "Solitaire"
vgacardgames - Four SVGAlib card games
xmahjongg - tile-based solitaire game
xsol - X Solitaire
brock@vader:~$ 

```

---

### Post by benjie1 on 2012-07-04
Hi again. Moved the installer to another folder as you said. Works great and only one icon on the desktop other than the one to run it. It is a .lnk icon. Haven't removed it and not sure if I can do that or should I put it in a particular folder?

As to native solitaire. I've had this one for many years and am used to it but will try native ones. In the lines of code listed in a reply here, do I run them all at once in a terminal? Thanks.

---

### Post by SirWhy on 2012-07-04
Perhaps I'm wrong in interpreting what you mean, but the only thing you need to do in terminal is 

```
~$ apt-cache search solitaire
```

Read the output, choose a package and use

```
~$ sudo apt-get install <package name>
```

Then again I probably misinterpreted you. But you don't need to run them all, just those two if I understood you.

---

### Post by benjie1 on 2012-07-04
you understood me correctly. Thanks.  Do you or anyone know about that .lnk icon on the desktop from installing the Hardwood Solitaire game? Don't want to remove it and have to re-install. Can I put it in another folder? Which one? Now to check native solitaire games. Thanks.           Bob

---

### Post by SirWhy on 2012-07-04
It might be this, I'm 95% sure (could be something different but I doubt it)

A .lnk file points to the .exe file for the Hardwood Solitaire game. It's a shortcut to the game. If the other icon is a .exe file, you can remove it no problem I'd say. You can launch the game from the other file right?

---

### Post by benjie1 on 2012-07-04
Will try removing the .lnk and hope the .exe launches the program as it does now. Will let you know.  Thanks.                Bob

---

### Post by benjie1 on 2012-07-04
:D  Removing the .lnk was not a problem and I installed a few of the ones listed in #3 or #2. Now to play them. Anyone interested in Hardwood Solitaire, it works great. Just the music doesn't. It has 100 games in alphabetical order.  [http://www.silvercrk.com](http://www.silvercrk.com)  The present version is 4 and you have to buy tokens to get a few games. Gets to be expensive. Version 3 that I have is buried somewhere on their web site. I don't know just where. If it is not free, you get 100 games for a single fee. Or if legal, I have the install file.     Bob

---

### Post by SirWhy on 2012-07-04
> **benjie1 said:**
> :D  Removing the .lnk was not a problem and I installed a few of the ones listed in #3 or #2. Now to play them. Anyone interested in Hardwood Solitaire, it works great. Just the music doesn't. It has 100 games in alphabetical order.  [http://www.silvercrk.com](http://www.silvercrk.com)  The present version is 4 and you have to buy tokens to get a few games. Gets to be expensive. Version 3 that I have is buried somewhere on their web site. I don't know just where. If it is not free, you get 100 games for a single fee. Or if legal, I have the install file.     Bob
Glad it worked for you mate. Enjoy your solitaire

---

