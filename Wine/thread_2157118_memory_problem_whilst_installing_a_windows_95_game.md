---
title: "memory problem whilst installing a windows 95 game on wine"
date: 2013-06-24
forum: Wine
---

### Post by DrBlob on 2013-06-24
I'm trying to install Admiral Sea Battles on wine (version 1.4.1 on ubuntu 13.04) and it gets as far as here:
[IMG]http://farm4.staticflickr.com/3819/9126230490_fa7f9cd91f_o.jpg[/IMG]
...then I can't move forward, as it doesn't show up any disk space. The program is meant for windows 95; could there be some issue with amounts of memory and a win95 limit? If this is the problem, is there a way to set some kind of limit on wine. I've also tried to install it on a windows machine through virtual box, the install went fine, but the graphics were appalling, and i'd prefer to have it running on ubuntu anyways.
Any ideas?

---

### Post by regor210 on 2013-06-24
Configure Wine for win 95

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following command into the terminal window minus $

$ winecfg

look at the bottom of the menu and use the down arrow to select  windows 95  then press the Apply button. Retry installing.

**Note**. Remember to change back to XP before running a game or app that requires XP.

If its still not working I would see if the game has a DOS install. Dosbox does a great job of running old games.

Another option would be running Windows 98 in Virtualbox or Qemu, I say Windows 98 because most games made for win 95 will work in win 98 and win 95 was a GUI for DOS and can sometimes be tricky to get up and running.

---

### Post by DrBlob on 2013-06-26
I ran the install again with wine in win95, still the same problem :( and when trying to run the setup.exe in DOSbox it says "This program cannot be run in DOS mode." (am I doing it wrong?). I also tried virtual box, this time it installed fine (huzzah!) but the graphics were really bad and it ran really slowly  -guess that's an issue for somewhere else though

Anyways, thanks for the help  :)

---

