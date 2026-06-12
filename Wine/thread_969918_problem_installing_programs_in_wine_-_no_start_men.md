---
title: "problem installing programs in wine - no start menu entry"
date: 2008-11-03
forum: Wine
---

### Post by themusicalduck on 2008-11-03
I've tried to install a couple of programs in wine but for some reason after installing, there isn't any Program Files listing on the wine menu. When I install WoW, I also get an error about not being able to enter wow into add/remove programs. If I try to uninstall a program using the wine uninstaller, it says there is no registry key yet, and the list of programs to uninstall is empty.

I've recently done a fresh install, but keeping my original home folder. I also used crossover for a while for programs instead of wine, but decided to continue using wine instead, and completely uninstalled crossover.

Another odd thing is that .exe files don't seem to be associated with wine anymore, when I click on an exe file it comes up with the archive manager.. only way to run the programs is through right click menu or the terminal.

Anyone have any ideas about it?

---

### Post by SerenityKill3r on 2008-11-03
Hmm, what version of wine are you using?

---

### Post by themusicalduck on 2008-11-04
1.0.1

---

### Post by cogadh on 2008-11-04
Try this to fix the Applications Menu problem:
[http://ubuntuforums.org/showpost.php?p=4025416&postcount=4](http://ubuntuforums.org/showpost.php?p=4025416&postcount=4)

As for the file associations and other issues, you might try purging Wine completely and then reinstalling to see if it fixes the issue:
```
sudo apt-get remove --purge wine
sudo apt-get install wine
```

---

### Post by themusicalduck on 2008-11-06
Following that post seems to have helped to bring back my old wine menus. But it still doesn't want to show any of the new programs I install.

Doing a remove --purge and reinstall doesn't seem to have helped the file associations either, it tries to open exe files as an archive.

---

### Post by themusicalduck on 2008-11-07
bump

---

### Post by hondaftw on 2008-11-23
hello. i have a solution for the file association of the exe file for wine, i just found it on google myself lol.

right click on the exe file and select Properties. click over to the Open With tab, and select the Wine radio button (the archive radio button is selected by default). hit OK and problem solved!!


I am also in for a solution to wine adding program shortcuts to the start menu. i have no luck with that :(

---

### Post by themusicalduck on 2008-11-23
Thanks! that worked!

As for the wine menus.. I managed to fix it, but I'm not entirely sure what it is I actually did..

I'm pretty sure I deleted a large block of text under 'wine' tags in /home/<user name>/.config/menus/applications.menu in the hope that it would reset things, but I don't know if that is what actually fixed it or not. It might be worth backing that file up and experimenting a bit though.

---

### Post by 3rods on 2009-02-10
I had pretty much the same issue and I created a new user, then copied over their /home/<user>/.config folder and the wine menu showed up again. 

I got a menu item stuck hanging off the wine menu too so I ended up deleting (i forget exactly) some files that made everything under App > Wine >Programs disappear. Then I tried editing the main menu, removed/purged wine - no luck. Only replacing the ~/.config folder did the trick and set it back to it's defaults.

---

