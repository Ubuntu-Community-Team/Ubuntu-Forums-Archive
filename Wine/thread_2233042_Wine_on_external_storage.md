---
title: "Wine on external storage?"
date: 2014-07-05
forum: Wine
---

### Post by adamwright609 on 2014-07-05
I'm running Xubuntu on an Acer C720 Chromebook.  Due to the small 16gb SSD I clearly do not have much space for windows applications.  I would like to be able to install stuff to an external usb or SD card.  I know WINE needs to install to the virtual C:/ drive it creates for Windows so is there a way to install wine on the external storage or to add a secondary virtual drive on external storage?

---

### Post by Mark Phelps on 2014-07-06
BEFORE you charge down this path, you may be able to save yourself a LOT of frustration if you go to the WineHQ page link and do searches for the MS Windows apps and versions you want to use.  Anything not listed, or rated lower than Gold, is essentially going to be a waste of your time trying to install:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by MartyBuntu on 2014-07-06
You may be able to install to custom directories if you install programs through **Play On Linux**...

---

### Post by adec2 on 2014-07-07
Use playonlinux and use a symlink to the wineprefix directory

Sorry for the blatant copy and paste but i prefer to give a full answer here instead of links to other sites that may at some point not exist (you will need to edit the /media/Games part below to your location you want to put the wineprefix folder)

[COLOR=#333333][FONT=MavenPro]To ALL The people who are trying to create a symbolic link here is a small Tutorial for Ubuntu/Mint users[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]For Example[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]I want to move the wineprefix from my /home/wolf/.PlayOnLinux to /media/GAMES/wineprefix[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]1. Create a folder on your Drive GAMES with the name wineprefix[/FONT][/COLOR]
[COLOR=#333333][FONT=MavenPro]2. Open the Terminal and run[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]sudo ln -s /media/GAMES/wineprefix /home/wolf/.PlayOnLinux[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]That command above means that it will create a wineprefix symbolic link to the folder PlayOnLinux which the software will use to install your games.[/FONT][/COLOR]
[COLOR=#333333][FONT=MavenPro]This is a CASE SENSITIVE command be sure to check caps and typos otherwise it will NOT work[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]now if you go to folder /home/wolf/.PlayOnLinux you will see an arrow with the symbolic link created called (have to enable show hidden files)[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]wineprefix[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]Symbolic link ,means that the software playonlinux is using the folder wineprefix to install the games and it must be the same name with the symbolic link.[/FONT][/COLOR]

[COLOR=#333333][FONT=MavenPro]You cannot create a a symbolic link called MYWindowsGames

Respect to wolfyrion on the playonlinux forums[/FONT][/COLOR]

---

### Post by adamwright609 on 2014-07-07
Thanks, that looks like exactly what I needed.  I'll try it out later.

---

