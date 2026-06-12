---
title: "using program 'launchers' in wine"
date: 2008-05-01
forum: Wine
---

### Post by gawdin on 2008-05-01
I have some games that in windows you would execute a "launcher" rather than the main executable (for example Flyff or Conquer Online) however I usually get an error along the lines of it not being able to find the main executable or that the main executable could not be accessed. neither exec file is "locked" so it may just be whether or not the launcher knows how to find the main exec. any help with this? also the program doesn't work in my virtualization (it launches the main exec but only to a black screen, video driver problems I assume)

---

### Post by cogadh on 2008-05-01
Technically, all you should need to do is change directories to the game's install directory before you run the launcher with Wine and it should detect the correct executables:
```
cd ~/.wine/drive_c/Program\ Files/game_directory
wine launcher.exe
```
However, that being said, at least one of the games you mention (Flyff) does not work with Wine at all:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3253](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3253)
And the other game (Conquer Online) has a spotty performance history, plus some specific configuration/installation steps that are required before it will work:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4055](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4055)

---

### Post by gawdin on 2008-05-01
thank you very much, it worked with some of my other games right away, I will post if I get Conquer working too.

---

