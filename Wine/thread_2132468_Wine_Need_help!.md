---
title: "Wine? Need help!"
date: 2013-04-04
forum: Wine
---

### Post by acidydragon on 2013-04-04
I read the all of the information I could find on wine, and it wasn't very much (having issues with the search feature of the forum).

I understand that the idea behind it is to make it so that you can install windows programs, and have them run on ubuntu. The wine website, says just to double click the .exe file, and it will take  over, and install normally.
That didn't work, it just opened the .exe. So, I right clicked, and hit Open with Wine Windows Program Loader, but nothing happens...
How do you get wine to work?

---

### Post by mamamia88 on 2013-04-04
What program?  Check the database on winehq to see how well its supported first

---

### Post by QIII on 2013-04-04
*Moved to **Wine***

---

### Post by acidydragon on 2013-04-04
League Of Legends, Star Wars the Old Republic... A few games.

---

### Post by mamamia88 on 2013-04-04
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true) and yes looks like you are doing it right.  Just right click the exe installer file and run with wine.  or from a terminal wine /path/to/exefile.

---

### Post by acidydragon on 2013-04-04
I tried the right click and run, and got nothing.

I typed "wine/home/kyle/to/LeagueofLegends.exe" in terminal, and got No such file or directory.

---

### Post by breezypt on 2013-04-05
First off, to run from the terminal, you need a space between the 'wine' and the 'path to the file'. In other words type ' wine /home/kyle/to/LeagueofLegends.exe' remember to put a space after you type the word wine. And of coarse leave out the quotes, I just put them in there as an old force of habit dealing with unix commands. I wish you luck with your wine install.....

Second of all, I have had no success from wine with anything. I don't mean to insult the programmers who worked tirelessly to get this to work. But I had many major issues with it, and deleted the whole damn thing!

---

### Post by breezypt on 2013-04-05
[**[COLOR=#000000]acidydragon[/COLOR]**]("http://ubuntuforums.org/member.php?u=1807402"), Kyle they also said to never sudo a wine command, so if it says you don't have permissions. Right click the installer, go down to properties,permissions and make sure the box is checked to make the file executable. Hope this helps a little.

John

---

