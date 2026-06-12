---
title: "i need help installing jedi knight academy"
date: 2008-01-13
forum: Wine
---

### Post by swankyfb on 2008-01-13
I have followed this tutorial and I still need help.

here it is:
Fix Cd Install Jedi Academy
by Mike James on Sunday December 30th 2007, 21:37
Fix Cd Install Jedi Academy

Ok, Here is my febile attempt to tell you how to get around this problem. First of all I use Ubuntu with the WINE installed.
I Installed Jedi Academy by copying all the files from both disks to a folder on my desktop then I exicuted the install from the desktop folder.

1.In ubuntu goto Applications-Wine-Configurewine

2.Click on the Drives Tab

3.Hit the Autodect button and see what the drive letters are for your CD-rom drive/drives.

4.Click the "Show Advanced" button then go to top of window and make sure you cd-rom drives say CD-ROM in the "Type" option. If not change it to CD-ROM then hit "apply" at the bottom.

5.Open a terminal window and type "wine eject x:" x=your cd-rom drive letter. If your CD-ROM drive ejects then you know that wine sees it as that drive letter. Remember the drive letter that ejected your CD-ROM.

6.In a terminal window type "wine regedit"

7. Click edit-Find and in the find window type "jedi" and hit enter.

8. Hit the F3 key to search next registery item and Look at every registery entry that referes to Jedi Academy and you will see where the registery had some drive letter info in some of the files. On my system it said h: drive
The reason it said h: is because according to wine my desktop is part of the h: drive and that is the location of the folder I installed it from.

9. Change all of the drive letters to that of you wine cd-rom drive that you found from direction 5. from above.

That's it.
Now the game will be able to detect your cd-rom drive with the game disk in it.


I have followed the steps in order:

[IMG]http://i88.photobucket.com/albums/k192/swankyfb/jk3.png[/IMG]
[IMG]http://i88.photobucket.com/albums/k192/swankyfb/jk3.png[/IMG]
[IMG]http://i88.photobucket.com/albums/k192/swankyfb/Screenshot-WineApplicationDB-Viewin.png[/IMG]
[IMG]http://i88.photobucket.com/albums/k192/swankyfb/Screenshot-Wineconfiguration.png[/IMG]
[IMG]http://i88.photobucket.com/albums/k192/swankyfb/Screenshot-Wineconfiguration-2.png[/IMG]
[IMG]http://i88.photobucket.com/albums/k192/swankyfb/Screenshot-robRob.png[/IMG]
[IMG]http://i88.photobucket.com/albums/k192/swankyfb/Screenshot-3.png[/IMG]

Screenshots are put in order as steps.

In step 5 E: is the CD-Rom drive and D: and C: are both hard drives.

In the last step, regedit cannot find "jedi"

what am I doing wrong?

please note that I am new to Linux and it is confusing to me right now.

---

### Post by kjander on 2008-01-14
Have you already run Jedi Academy's installer? it installs fine on my system with the current WINE build. That tutorial only seems to be for if you have a specific problem, after installing JKA

---

### Post by Einder on 2011-07-29
The game itself should install just fine. First you need to get and apply the v1.01 patch and then go to appdb.winehq.com and search jedi academy. Download the next patch you need from there and it should run just fine. I just go it installed on my system.

---

