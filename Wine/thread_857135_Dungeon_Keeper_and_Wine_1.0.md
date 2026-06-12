---
title: "Dungeon Keeper and Wine 1.0"
date: 2008-07-12
forum: Wine
---

### Post by F for Fragging on 2008-07-12
This game was awesome and I'd really like to play it again with Wine. Unfortunately I can't get it to work. I searched with Google thoroughly, but I found no instructions on how to get it working.

The Wine AppDB has [reports]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1978") that it doesn't work. Elsewhere it is claimed that it does work, and the AppDB entry also has a screenshot which shows it running. Besides that, I found no useful information with Google or on this forum.

I got [this version]("http://www.the-underdogs.info/game.php?id=5103") of Dungeon Keeper, because I lost the original CD. This is Dungeon Keeper Gold with the latest updates and a Direct3D version as well. I'm on Intrepid, I downloaded Wine 1.0 from the repositories and the latest Wine-doors from the Wine-doors website.

I copy the DK directory to Wine's C drive directory inside the /.wine/ directory. I don't do any configuration with Wine-doors, except for setting DK's executable files to use Windows 95. Then I browse with Nautilus to the Wine's C drive directory, right click the executable and choose "Open with "Wine Windows Program Loader"". My monitor then shows the splash screen of DK, but before the intro movie can play the game crashes. I tried both the Direct3D and the Windows 95 executables. I also tried starting it with the method described [here]("http://ubuntuforums.org/showthread.php?p=5357789") to no avail.

I'd really appreciate some help, Dungeon Keeper is one of the first games I've ever played and I still remember it as one of the best games ever. Hopefully those who apparantly do have it working could post instructions to get it working here.

---

### Post by happyhamster on 2008-07-12
You'll probably have a better chance of getting it to run by using dosbox instead of wine. Odds are good, see this page for example:
[http://www.dosbox.com/comp_list.php?showID=758&letter=D](http://www.dosbox.com/comp_list.php?showID=758&letter=D)
(Hardy has dosbox 0.72)

I once installed Dungeonkeeper in Virtualbox (winxp) and it ran fine, but it was unplayable nevertheless because it would only run in a tiny 800x600 (or perhaps even 640x480) window. Fullscreen it just crashed IIRC.

For more info on dosbox, see:
[https://help.ubuntu.com/community/DOSBox](https://help.ubuntu.com/community/DOSBox)
[http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html](http://blog.mypapit.net/2007/05/dosbox-how-to-play-dos-games-in-ubuntu-linux.html)

---

### Post by F for Fragging on 2008-07-15
Thanks for your reply, but unfortunately the Direct3D version can´t work under DOS AFAIK, so now I'm playing it on Windows XP. I hope Wine will work someday.

---

