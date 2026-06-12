---
title: "Missing Wine Config after upgrade to Wine 1.8"
date: 2015-12-21
forum: Wine
---

### Post by yoshii on 2015-12-21
OK, I followed the instructions on WineHQ.com for how to upgrade to Wine 1.8 for Ubuntu.  Unfortunately, further information about this install is in the WineHQ forums but not on that instruction page.  
It turns out that the new install goes into the "/opt/wine-devel/bin/" folder and furthermore, in the process of the install, the Wine Config menu shortcut is deleted.  Wine Configuration program is called "winecfg".  

You can create a desktop launcher with these contents to launch Wine Config:

> 
[Desktop Entry]
Version=1.0
Type=Application
Name=Wine Configuration
Comment=Wine Configuration
Exec=/opt/wine-devel/bin/winecfg
Icon=7765_winebrowser.0
Path=
Terminal=false
StartupNotify=true


Create an empty document and name it WineConfig.desktop and edit it with gedit or leafpad or geany or whatever plain text editor you have.  Paste the quoted text above into and save it.  Then after you quit, select the file and enable it for execution (running as a program).  You can choose a different icon if you like.  Sorry if this isn't entirely clear.  I learn this stuff as I go along.  Ask more questions if you need help and we will try and get you up and running.  Peace and happy holidays.

P.S. - Another place to get a Wine icon is from here:  /usr/share/app-install/icons/wine.svg

---

