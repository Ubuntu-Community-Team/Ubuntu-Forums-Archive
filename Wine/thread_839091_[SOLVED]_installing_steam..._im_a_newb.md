---
title: "[SOLVED] installing steam... im a newb"
date: 2008-06-24
forum: Wine
---

### Post by mcheshpants on 2008-06-24
im using wine to install steam on ubuntu and what it says to do in the instructions for installing it everywhere is "type" and then it has a box under it with some code. where do you type it? can someone explain please im a newb ](*,)

---

### Post by cbwcjw on 2008-06-24
This isn't the right board for this, there's a wine question section. Try [here]("http://ubuntuforums.org/forumdisplay.php?f=313").

---

### Post by Perfect Storm on 2008-06-24
Thread moved

---

### Post by greyfox1 on 2008-06-24
Hi mcheshpants (like the name BTW), what you are asking about is the Gnome Terminal, the command-line interface.  Check out the links below and read up a bit since I guarantee you will be using it a lot.  Welcome to the boards!

[Gnome Terminal]("https://help.ubuntu.com/community/GnomeTerminal") - Overview
[Using Terminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by YokoZar on 2008-06-25
By the way, don't feel bad; you shouldn't have to use a terminal to install steam like this.  For the next Ubuntu release, you will be able to just double click on the install file.  :)

---

### Post by Frak on 2008-06-25
I stole this off of teh intarwebz, hope it helps :)

> Setup Wine for Use w/Steam
To be able to use steam with wine you need to Install the tahoma.ttf font. Additionally, you must download and Install the Mozilla ActiveX control from TransGaming.

Step 1. Install Needed Font
The tahoma.ttf font is not included in the Microsoft core fonts package. To get the font, google for "filetype:ttf inurl:tahoma", download it and put it into your ~/.wine/drive_c/windows/fonts directory.

Step 2. Install TransGaming ActiveX Control
The TransGaming ActiveX Control is used because it includes one native dll necessary to Steam operation. Other Mozilla ActiveX controls (for example the one downloaded automatically by wine or from [http://www.iol.ie/~locka/mozilla/mozilla.htm](http://www.iol.ie/~locka/mozilla/mozilla.htm)) may not work, so make sure you have deleted these before installing the one from Transgaming. Install the ActiveX control with the following:

cd ~/.wine/c_drive/Program\ Files/
wget [http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz](http://downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz)
tar -zxvf mozcontrol.tgz && rm mozcontrol.tgz
cd mozcontrol/ && wine regsvr32 mozctlx.dll

Install Steam
At this point you are ready to Install steam. Fedora should know to use wine for .exe files thus you should be able to download the run the steam Installer with just a double click. Another option is to do the Install from the terminal. Install from the terminal with the following:

wget [http://steampowered.com/download/SteamInstall.msi](http://steampowered.com/download/SteamInstall.msi)
wine msiexec /i SteamInstall.msi


Performance Issues
If you know Steam is working, you could try to speed it up by running Steam.exe with the following options:

WINEDEBUG="-all" wine Steam.exe

---

### Post by Fenrirwulf on 2008-06-25
Frak,
  Awesome post! I was just able to finally get this installed thanks to you. I had never been able to get this work properly in the past.

---

### Post by Frak on 2008-06-25
> **Fenrirwulf said:**
> Frak,
  Awesome post! I was just able to finally get this installed thanks to you. I had never been able to get this work properly in the past.
Thank the Fedora Documentation team, they made the post in the first place. I just spammed it here on the forums. :D

---

### Post by cogadh on 2008-06-26
One minor note on those instructions, you don't need to install the Tahoma font anymore, Wine has its own now.

---

### Post by Phyrax on 2008-06-26
> **cogadh said:**
> One minor note on those instructions, you don't need to install the Tahoma font anymore, Wine has its own now.

my text is funny though, how do i use wines so my text on steam is not funny?

thanks.

---

