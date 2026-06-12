---
title: "How to get Sunday Times Scrabble CD-ROM to work / wine ??"
date: 2008-03-03
forum: Wine
---

### Post by Malefiz on 2008-03-03
Hi all!
Yesterday's Sunday Times included a free Scrabble CD-ROM, which I'm hoping to run using wine.
As I'm posting this here, you probably guessed: It doesn't work.
And I don't know why :-(

I managed to install it in c:\program files..... yet trying to run the Scrabble.exe only results in a Ubisoft Starter Screen showing for about 5 seconds, until it disappears. 

On re-running the installation as a repair, I finally got two Desktop icons, but trying those doesn't do anything.

Trying to run it via Terminal seems fruitless, as the path to the .exe file in wine includes special characters ( (R) -sign), which I can't manage to either get into the terminal or to avoid, when /cd-ing into the appropriate directory. Is it possible to change the name of the path in wine to avoid the problem?

Does anyone have any tips? And did anyone actually manage to get the game to run?

Thanks,
Malefiz

NB: I know there are some Linux Scrabbles around, and I use ISC anyway, but I really want to use the free CD-ROM, for reasons of stubbornness :-)

---

### Post by jonny on 2008-03-04
Strange - it Just Works for me on Gutsy.

---

### Post by jonny on 2008-03-04
If it helps, I run it from adesktop icon that has this as the launcher command:

env WINEPREFIX="/home/jonny/.wine" wine "C:\Program Files\Ubisoft\SCRABBLE® 2005 EDITION\Scrabble2005.exe"

---

