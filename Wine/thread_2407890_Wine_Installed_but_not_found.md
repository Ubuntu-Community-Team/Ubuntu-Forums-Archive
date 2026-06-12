---
title: "Wine Installed but not found"
date: 2018-12-10
forum: Wine
---

### Post by stew1411 on 2018-12-10
[ATTACH=CONFIG]281914[/ATTACH]

Hello,

I have installed Wine but my system says that it's not installed when I try to launch it. In the screenshot posted, you can see that I've tried installing and running Wine from the terminal, it's added to the software repositories, and it's not appearing in my Applications menu. Any ideas on my next step? TIA.

---

### Post by Dennis N on 2018-12-10
wine doesn't have a GUI, - it works in the background to install and then run Windows programs. 
You can install a Windows program with wine by right clicking on its .exe installer, and select **Open with > "Wine Windows Program Loader"** to start the installer for the Windows program.
After installing, there should be a menu entry for the Windows program just installed, possibly in your Applications menu. Depends on the desktop environment. My Xubuntu shows a separate menu category for Wine. After being installed, Windows programs by default get installed to **~/.wine/drive_c/Program Files/** Start them like any other program in your menu.

You can also install and run them from a terminal - here is an example of a terminal command that runs an installed program:

wine "/home/dmn/.wine/drive_c/Program Files/Litsoft/Across Lite/ACROSSL.EXE"

basically, **wine** followed by path to the installed executable.

More Information Here:
UbuntuCommunity Help:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Also there is a program called **playonlinux** that makes things easier (its in the Ubuntu repository). Too much to explain here. There is a web site for Play on Linux:
[https://www.playonlinux.com/en/](https://www.playonlinux.com/en/)

---

### Post by freemedia2018 on 2018-12-10
> **Dennis N said:**
> wine doesn't have a GUI,

It has a GUI config panel for setting up applications, which typically opens the first time you use it. At least in Debian. I used Wine with Puppy Linux over a decade ago, I don't know if I ever used it in Ubuntu.

From the term you can probably find it just by typing wine[click tab key a couple times] and it's probably winecfg or wine-config or something like that.

---

### Post by deadflowr on 2018-12-10
In order to get the wine program loader to show you need to follow monkeybrain20122's post here:
[https://ubuntuforums.org/showthread.php?t=2382617&p=13766904#post13766904]("https://ubuntuforums.org/showthread.php?t=2382617&p=13766904#post13766904")
It relates to this bug here:
[https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326]("https://bugs.launchpad.net/ubuntu/+source/wine-development/+bug/1576326")

---

